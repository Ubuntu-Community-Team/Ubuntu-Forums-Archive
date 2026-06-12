---
title: "Interesting issue: PHP-APC breaks Apache"
date: 2010-11-10
forum: General Help
---

### Post by JSHC on 2010-11-10
I have run into an interesting problem. I've just installed Ubuntu Server 10.10 64-bit for the purposes of hosting a web site.

I ran the following commands...

```

aptitude install apache2
aptitude install mysql-server mysql-client
aptitude install php5 libapache2-mod-php5
aptitude install php5-mysql php5-curl php5-gd php-pear php5-imap php5-mcrypt php5-memcache php5-recode php5-tidy php5-xmlrpc php5-xsl php5-json

```...and everything worked fine. The default index.html file worked as did the phpinfo.php test page that I loaded to see my configuration.

Then I ran this...

```
aptitude install php-apc php5-xcache
```...to install opcode caching for my server (I'm going to test both APC and XCache to see which one is better). Things went south after I did this.

Apache would load the default index.html fine, but it would not load any PHP file I pointed it to. I tried the following restart commands...

```
/etc/init.d/apache2 restart
/etc/init.d/apache2 force-reload
```...and neither did the trick.

Clearly one of the extensions broke the Apache server. I went to "/etc/php5/conf.d" and located the file apc.ini. I commented out the line "extension=apc.so" and then restarted the Apache server. Now everything works fine again.

**My question is why does the APC extension cause Apache to not load PHP files?**

Here are my apache2.conf and httpd.conf files. I haven't messed with them a lot because I was in the process of configuring things when this issue happened.

** Apache2.conf from /etc/apache2/apache2.conf**

```

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
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
# with "/", the value of ServerRoot is prepended -- so "foo.log"
# with ServerRoot set to "/etc/apache2" will be interpreted by the
# server as "/etc/apache2/foo.log".
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
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock

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
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
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
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

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
    Satisfy all
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
# e.g., www.apache.org (on) or 204.62.129.132 (off).
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
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

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

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/
```**Httpd.conf from /etc/apache2.conf (I added those lines of code after following another forum post. They were present before I commented out the apc.ini file, so they didn't help)**

```
AddType application/x-httpd-php .php3 .php4 .php5 .php
AddType application/x-httpd-php-source .phps
```As I mentioned, I'm running the latest version of Ubuntu Server 10.10 64-bit. Here's more information if it helps.

**ps aux|grep apache**

```
root      1133  0.0  1.4 243388 14612 ?        Ss   10:44   0:00 /usr/sbin/apache2 -k start
www-data  1235  0.0  1.0 245216 11048 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1236  0.0  0.8 244632  9176 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1237  0.0  0.9 244632  9388 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1238  0.0  0.9 245160  9828 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1239  0.0  0.9 244656  9228 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1240  0.0  0.7 243524  7472 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1241  0.0  0.7 243952  8004 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1242  0.0  0.7 243952  8048 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1243  0.0  0.7 243524  7664 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
root      1341  0.0  0.0   8952   856 pts/0    S+   12:25   0:00 grep --color=auto apache
```**ps aux|grep httpd**

```
root      1365  0.0  0.0   8952   856 pts/0    S+   12:27   0:00 grep --color=auto httpd
```**netstat -na|grep :80**

```
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
```

---

