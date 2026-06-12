---
title: "php files downloading and not displaying"
date: 2010-11-18
forum: General Help
---

### Post by nanewk on 2010-11-18
I have searched the forum, read the wiki, and still have not came up with a solution that works for me. The topic says it all - when i try to load a php file my browser downloads the file instead of displaying the page. Here is my apache conf file.

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
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
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
Include /etc/apache2/httpd.conf

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
Include /etc/apache2/sites-enabled/

************* end *************

php output:

tj@macbuntu:/etc/apache2/mods-enabled$ locate php5
/etc/php5
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load
/etc/apache2/mods-enabled/php5.conf
/etc/apache2/mods-enabled/php5.load
/etc/apparmor.d/abstractions/php5
/etc/cron.d/php5
/etc/php5/apache2
/etc/php5/conf.d
/etc/php5/apache2/conf.d
/etc/php5/apache2/php.ini
/etc/php5/conf.d/mysql.ini
/etc/php5/conf.d/mysqli.ini
/etc/php5/conf.d/pdo.ini
/etc/php5/conf.d/pdo_mysql.ini
/usr/lib/php5
/usr/lib/apache2/modules/libphp5.so
/usr/lib/php5/20090626+lfs
/usr/lib/php5/libexec
/usr/lib/php5/maxlifetime
/usr/lib/php5/20090626+lfs/mysql.so
/usr/lib/php5/20090626+lfs/mysqli.so
/usr/lib/php5/20090626+lfs/pdo.so
/usr/lib/php5/20090626+lfs/pdo_mysql.so
/usr/share/php5
/usr/share/apport/package-hooks/source_php5.py
/usr/share/doc/libapache2-mod-php5
/usr/share/doc/php5
/usr/share/doc/php5-common
/usr/share/doc/php5-mysql
/usr/share/doc/php5-common/CODING_STANDARDS.gz
/usr/share/doc/php5-common/CREDITS
/usr/share/doc/php5-common/EXTENSIONS.gz
/usr/share/doc/php5-common/NEWS.Debian.gz
/usr/share/doc/php5-common/README.Debian.gz
/usr/share/doc/php5-common/README.Debian.security
/usr/share/doc/php5-common/README.EXT_SKEL.gz
/usr/share/doc/php5-common/README.PHP4-TO-PHP5-THIN-CHANGES.gz
/usr/share/doc/php5-common/README.SELF-CONTAINED-EXTENSIONS.gz
/usr/share/doc/php5-common/README.SVN-RULES.gz
/usr/share/doc/php5-common/README.Zeus.gz
/usr/share/doc/php5-common/TODO.Debian
/usr/share/doc/php5-common/TODO.gz
/usr/share/doc/php5-common/changelog.Debian.gz
/usr/share/doc/php5-common/changelog.gz
/usr/share/doc/php5-common/copyright
/usr/share/doc/php5-common/examples
/usr/share/doc/php5-common/test-results.txt.gz
/usr/share/doc/php5-common/examples/php.ini-development
/usr/share/doc/php5-common/examples/php.ini-production
/usr/share/lintian/overrides/libapache2-mod-php5
/usr/share/lintian/overrides/php5-common
/usr/share/php5/php.ini-production
/usr/share/php5/php.ini-production-dist
/usr/share/php5/php.ini-production.cli
/var/cache/apt/archives/php5_5.3.2-1ubuntu4.5_all.deb
/var/lib/php5
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/lib/dpkg/info/libapache2-mod-php5.triggers
/var/lib/dpkg/info/php5-common.conffiles
/var/lib/dpkg/info/php5-common.list
/var/lib/dpkg/info/php5-common.md5sums
/var/lib/dpkg/info/php5-common.postrm
/var/lib/dpkg/info/php5-mysql.conffiles
/var/lib/dpkg/info/php5-mysql.list
/var/lib/dpkg/info/php5-mysql.md5sums
/var/lib/dpkg/info/php5.list

********* end *******

---

### Post by lisati on 2010-11-18
You might want to restart apache & clear your browser cache. If that doesn't help, check that libapache2-mod-php5 is installed.

---

### Post by nanewk on 2010-11-21
tj@macbuntu:~$ locate libapache2-mod-php5
/usr/share/doc/libapache2-mod-php5
/usr/share/lintian/overrides/libapache2-mod-php5
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/lib/dpkg/info/libapache2-mod-php5.triggers

tj@macbuntu:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                     apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                              [ OK ]


php is installed, some odd error restarting apache..

---

### Post by nanewk on 2010-11-21
I fixed the localhost error. Still downloading php files unfortunately.

---

### Post by fragos on 2010-11-21
I only have 3 lines in my apache config file /etc/apache2/httpd.conf, all which I added to execute PHP. It works properly, they are as follows:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by nanewk on 2010-11-21
> **fragos said:**
> I only have 3 lines in my apache config file /etc/apache2/httpd.conf, all which I added to execute PHP. It works properly, they are as follows:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

I added those three lines to my httpd.conf file and returned these results after i cleared my cache/history and restarted apache:

tj@macbuntu:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                     [Sun Nov 21 20:39:41 2010] [warn] module php5_module is already loaded, skipping
 ... waiting [Sun Nov 21 20:39:42 2010] [warn] module php5_module is already loaded, skipping
                                                                                              [ OK ]

php files still download instead of displaying :|

---

### Post by fragos on 2010-11-21
I always set my PHP file permission to executable. I'm not sure if that's necessary but I do. Those three lines are the only configuration change I make to a default LAMP install.

---

### Post by psymeg on 2011-01-27
Installing php5-suhosin worked for me:

sudo apt-get install -y php5-suhosin

:popcorn:

---

