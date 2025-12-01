# LXD WordPress CLI

**Professional WordPress deployment automation made simple.**

Instantly deploy production-ready WordPress sites with automated SSL, caching, and professional nginx configuration using LXD containers.

## What You Get

- **Isolated Containers** - WordPress, Database, and Proxy in separate LXD containers
- **Redis Caching** - Built-in object caching for lightning-fast performance  
- **Automatic SSL** - Let's Encrypt certificates with auto-renewal
- **Professional Proxy** - Nginx reverse proxy with security headers
- **Cloudflare Integration** - Automatic DNS record management
- **Zero Configuration** - Works out of the box

## Quick Install

```bash
curl -sSL https://github.com/thxnlo/lxdautomated-cli/releases/latest/download/install.sh | bash
```

##  Deploy WordPress in Minutes

```bash
# Interactive deployment
lxd-wp deploy

# Or specify your domain
lxd-wp deploy --domain example.com

# Full deployment with options
lxd-wp deploy \
  --domain example.com \
  --container-name my-site \
  --admin-user admin \
  --admin-email admin@example.com
```

##  System Requirements

- **Ubuntu 20.04+** or compatible Linux distribution
- **LXD** installed and initialized
- **Internet connection** for SSL certificates and WordPress downloads

### Install LXD (if not installed)

```bash
sudo apt install -y lxd
sudo lxd init --auto
sudo usermod -a -G lxd $USER
newgrp lxd
```

## Features

###  Professional Architecture
```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Nginx Proxy   │    │   WordPress      │    │   Database      │
│   (SSL + Cache) │◄──►│   (PHP + Redis)  │◄──►│   (MariaDB)     │
│   Port 80/443   │    │   Optimized      │    │   Dedicated     │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

###  Security First
- **Isolated containers** for each service
- **Security headers** and hardened nginx configuration
- **Non-root WordPress** with proper file permissions
- **Automatic security updates**

###  Performance Optimized
- **Redis object caching** for WordPress
- **Nginx caching** for static assets
- **Optimized PHP-FPM** configuration
- **Database query optimization**

###  Production Ready
- **SSL certificates** with automatic renewal
- **CDN integration** with Cloudflare
- **Backup automation** (optional)
- **Monitoring and logging**

##  Available Commands

### Deploy a WordPress Site
```bash
lxd-wp deploy [OPTIONS]

Options:
  -d, --domain <DOMAIN>              Domain name for WordPress site
  -c, --container-name <NAME>        Custom container name
  -u, --admin-user <USER>            WordPress admin username
  -e, --admin-email <EMAIL>          WordPress admin email
      --skip-ssl                     Skip SSL certificate setup
      --skip-cloudflare              Skip Cloudflare DNS setup
```

### List Your Sites
```bash
lxd-wp list
```

### Remove a Site
```bash
lxd-wp remove <container-name>
```

### Check System Status
```bash
lxd-wp check
```

##  Advanced Usage

### Multiple Site Deployment
```bash
# Deploy multiple sites
lxd-wp deploy --domain site1.com --container-name site1
lxd-wp deploy --domain site2.com --container-name site2
lxd-wp deploy --domain site3.com --container-name site3

# List all sites
lxd-wp list
```

### Custom Configuration
The CLI automatically configures:
- Database connection and optimization
- Redis object caching
- Nginx reverse proxy with SSL
- WordPress security hardening
- Automatic backups (optional)

### Cloudflare Integration
When enabled, automatically:
- Creates DNS A records
- Configures CDN settings
- Sets up security rules
- Enables caching policies

##  Security Features

- **Container Isolation** - Each site in separate containers
- **Non-root WordPress** - Runs as dedicated user
- **Security Headers** - HSTS, CSP, XSS protection
- **File Permissions** - Strict WordPress file permissions
- **SSL Enforcement** - HTTPS redirect enabled
- **Login Protection** - Brute force protection

##  Performance Benefits

- **Lightning Fast** - Redis caching + nginx optimization
- **Resource Efficient** - Minimal container overhead
- **Scalable** - Deploy multiple sites without conflicts
- **CDN Ready** - Cloudflare integration for global performance

##  Support & Troubleshooting

### Common Issues

#### LXD Permission Denied
```bash
sudo usermod -a -G lxd $USER
newgrp lxd
```

#### Container Creation Fails
```bash
sudo systemctl restart lxd
lxd waitready
```

#### SSL Certificate Issues
```bash
# Check certificate status
lxc exec proxy -- certbot certificates

# Renew certificates
lxc exec proxy -- certbot renew
```

### Get Help
For support and troubleshooting, check the [documentation](https://github.com/thxnlo/lxdautomated) or open an issue.

##  Why Choose LXD WordPress CLI?

### vs. Docker Compose
- ✅ **Simpler setup** - No Docker knowledge required
- ✅ **Better isolation** - True container isolation with LXD
- ✅ **Resource efficient** - Lower overhead than Docker

### vs. Manual Installation  
- ✅ **Automated everything** - SSL, caching, security, backups
- ✅ **Best practices** - Professional configuration out of the box
- ✅ **Consistent deployments** - Same result every time

### vs. Hosting Providers
- ✅ **Full control** - Your server, your rules
- ✅ **Cost effective** - No monthly hosting fees
- ✅ **Professional setup** - Enterprise-grade architecture

---

##  Professional WordPress Hosting Made Simple

**Stop fighting with complex configurations. Deploy WordPress like the pros.**

```bash
curl -sSL https://github.com/thxnlo/lxdautomated-cli/releases/latest/download/install.sh | bash
```


*Built with ❤️ for WordPress developers and system administrators*

