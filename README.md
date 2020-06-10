# ApisCP Memcached Provider

This is a drop-in provider for [ApisCP](https://apiscp.com/) that installs Memcached.

## Installation

Running this playbooks installs `memcached` package and adds the PECL module to your `pecl_extensions` list.

```
cd /usr/local/apnscp/resources/playbooks
git clone https://github.com/thundersquared/apiscp-memcached.git addins/apiscp-memcached
ansible-playbook addin.yml --extra-vars=addin=apiscp-memcached
```

To start using `memcached` via PHP, you'll have to rebuild your PECL modules.

```
upcp -sb php/install-pecl-module
```

If you're using Multi-PHP you'd want to build the modules for your custom PHPs too.

```
cd /usr/local/apnscp/resources/playbooks
ansible-playbook bootstrap.yml --tags=php/install-pecl-module --extra-vars=php_version=7.4 --extra-vars=multiphp_build=true
```

## Usage

Usage may vary based on the software you're running on your websites.

Recommended usage for WordPress is via [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/), starting a process on boot for each account on personal [user_daemons](https://docs.apiscp.com/INSTALL/#recommended-configuration-settings) port via Task Scheduler.

```
memcached -p 40010 -m 128
```

## Contributing

Submit a PR and have fun!
