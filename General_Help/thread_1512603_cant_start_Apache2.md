---
title: "cant start Apache2"
date: 2010-06-18
forum: General Help
---

### Post by deff182 on 2010-06-18
hi, i've installed apache2+php+mysql.
[COLOR=Silver]Server version: Apache/2.2.12 (Ubuntu)[/COLOR]
[COLOR=Black]when i try to: sudo /etc/init.d/apache2 start[/COLOR]


> 
 * Restarting web server apache2                                                                                                                 [Fri Jun 18 17:21:31 2010] [warn] module alias_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module auth_basic_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authn_file_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_default_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_groupfile_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_host_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_user_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module autoindex_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module cgi_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module deflate_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module dir_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module env_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module mime_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module negotiation_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module php5_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module setenvif_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module status_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module php5_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/mods-enabled/alias.conf at line 15 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/conf.d/javascript-common.conf at line 1 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Jun 18 17:21:31 2010] [warn] module alias_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module auth_basic_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authn_file_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_default_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_groupfile_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_host_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module authz_user_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module autoindex_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module cgi_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module deflate_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module dir_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module env_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module mime_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module negotiation_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module php5_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module setenvif_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module status_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] module php5_module is already loaded, skipping
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/mods-enabled/alias.conf at line 15 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/conf.d/javascript-common.conf at line 1 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
[Fri Jun 18 17:21:31 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                                          fail
my httpd.conf
> 
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
ServerName midnightServer

#
DefaultType text/html

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User www-data 
#${APACHE_RUN_USER}
Group www-data
#${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org]("http://www.apache.org") (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
#Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
#Include /etc/apache2/sites-enabled/

#Include PHP5 module
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
#Directory Index
DirectoryIndex index.php index.php5 index.html index.htm
it shows some messy stuff when ps -aux | grep httpd:
> midnight@midnight-desktop:~$ ps -aux | grep httpd
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
midnight  3589  0.0  0.0   7336   884 pts/0    R+   17:29   0:00 grep --color=auto httpd:confused: any decisions on how to make it work

---

### Post by dcstar on 2010-06-18
> **deff182 said:**
> 
..........
it shows some messy stuff when ps -aux | grep httpd:
:confused: any decisions on how to make it work

```
sudo netstat -lpt
```

Find what is already using TCP port 80/HTTP.

---

### Post by leg on 2010-06-18
What happens when you type [http://localhost](http://localhost) into a browser?

---

