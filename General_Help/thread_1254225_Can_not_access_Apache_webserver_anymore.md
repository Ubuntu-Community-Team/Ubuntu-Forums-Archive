---
title: "Can not access Apache webserver anymore"
date: 2009-08-31
forum: General Help
---

### Post by ularlaut on 2009-08-31
Hi all..

Today I suddenly can not access my Apace server from other PCs (Windows Vista SP1) anymore, yesterday afternoon was working fine.

I can access the Samba/SWAT configuration pages from my other PCs, but I Can not access to the root page.

When I try to restart / start the Apache from server, I got this messages : 


 [COLOR=RoyalBlue]ferdy-tokobagus@ubuntu-server:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs[/COLOR]
                                                                         [[COLOR=Red]fail[/COLOR]]
[COLOR=RoyalBlue]ferdy-tokobagus@ubuntu-server:~$ 
[/COLOR]

And here are the Apache2.conf file settings : 

[COLOR=RoyalBlue]#
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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
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
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/,
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerName localhost
[/COLOR]

[COLOR=Black]Is there anything wrong with the settings or something else ?[/COLOR]

Thank you very much for the kind attentions.

regards,

---

### Post by sahabcse on 2009-08-31
Hi 

run 

#lsof -i :443
#lsof -i :80

Then kill the PID and restart the apache

for more info [http://ubuntulinux.co.in/apache-restart-error.php](http://ubuntulinux.co.in/apache-restart-error.php)

---

### Post by ularlaut on 2009-08-31
> **sahabcse said:**
> Hi 

run 

#lsof -i :443
#lsof -i :80

Then kill the PID and restart the apache

for more info [http://ubuntulinux.co.in/apache-restart-error.php](http://ubuntulinux.co.in/apache-restart-error.php)


Thank you very much for the tips, but still not working.
And also check using the Samba/ SWAT config page, the server does not have any PID that still working to be "kill"ed... 

:(

Any other idea... ??

Thanks a bunch though  :)

---

### Post by sahabcse on 2009-08-31
paste the o/p of cat /etc/apache2/ports.conf

netstat -plan | grep :443

---

### Post by ularlaut on 2009-08-31
> **sahabcse said:**
> paste the o/p of cat /etc/apache2/ports.conf

netstat -plan | grep :443

Hello again..

Here are config of the /etc/apache2/ports.conf : 

[COLOR=RoyalBlue]# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
[/COLOR]

[COLOR=Black]And this is when I run the [/COLOR]: netstat -plan | grep :443

[COLOR=RoyalBlue]root@ubuntu-server:~# netstat -plan | grep :443
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2979/apache2

[COLOR=Black]
Thank you very much for your kind help....  :-)[/COLOR]
[/COLOR]

---

### Post by sahabcse on 2009-08-31
Paste the following too

#sudo apache2ctl configtest
#sudo apache2ctl status
#sudo iptables -L
#ps -e | grep apache
#tail -f /var
#tail -f /var/log/apache2/error.log

---

### Post by ularlaut on 2009-08-31
Paste the following too

#sudo apache2ctl configtest

   [COLOR=RoyalBlue]root@ubuntu-server:~# sudo apache2ctl configtest
Syntax OK[/COLOR]

#sudo apache2ctl status

   [COLOR=RoyalBlue]root@ubuntu-server:~# sudo apache2ctl status
w3m: Can't load [http://localhost:80/server-status](http://localhost:80/server-status).
[/COLOR]
#sudo iptables -L
[COLOR=RoyalBlue]
   root@ubuntu-server:~# sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere

Chain ufw-after-forward (1 references)
target     prot opt source               destination

Chain ufw-after-input (1 references)
target     prot opt source               destination
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm                                                                                                  
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn                                                                                                  
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination

Chain ufw-after-output (1 references)
target     prot opt source               destination

Chain ufw-before-forward (1 references)
target     prot opt source               destination
ufw-user-forward  all  --  anywhere             anywhere

Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID
DROP       all  --  anywhere             anywhere            state INVALID
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere
ACCEPT     all  --  anywhere             base-address.mcast.net/4
ufw-user-input  all  --  anywhere             anywhere

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination

Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere

Chain ufw-logging-allow (0 references)
target     prot opt source               destination

Chain ufw-logging-deny (2 references)
target     prot opt source               destination

Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3                                                                                                  /min burst 10
DROP       all  --  anywhere             anywhere

Chain ufw-reject-forward (1 references)
target     prot opt source               destination

Chain ufw-reject-input (1 references)
target     prot opt source               destination

Chain ufw-reject-output (1 references)
target     prot opt source               destination

Chain ufw-user-forward (1 references)
target     prot opt source               destination

Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere            udp dpt:mysql
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www
ACCEPT     all  --  172.16.0.0/12        anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:swat
ACCEPT     udp  --  anywhere             anywhere            udp dpt:901
ACCEPT     tcp  --  5.0.0.0/8            anywhere
ACCEPT     udp  --  5.0.0.0/8            anywhere

Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 3/min bu                                                                                                  rst 5 LOG level warning prefix `[UFW LIMIT BLOCK] '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination

Chain ufw-user-output (1 references)
target     prot opt source               destination[/COLOR]


#ps -e | grep apache

   [COLOR=RoyalBlue]root@ubuntu-server:~# ps -e | grep apache
 2979 ?        00:00:00 apache2
 3015 ?        00:00:00 apache2[/COLOR]

#tail -f /var

   [COLOR=RoyalBlue]root@ubuntu-server:~# tail -f /var
tail: error reading `/var': Is a directory
tail: /var: cannot follow end of this type of file; giving up on this name
tail: no files remaining[/COLOR]

#tail -f /var/log/apache2/error.log

   [COLOR=RoyalBlue]root@ubuntu-server:~# tail -f /var/log/apache2/error.log
[Sun Aug 30 06:29:28 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2                                                                                                   with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 con                                                                                                  figured -- resuming normal operations[/COLOR]


Hope this detail help...  ;-)

Thanks

---

### Post by sahabcse on 2009-08-31
kill the running apache process, and restart the apache

---

### Post by ularlaut on 2009-08-31
Thanks again..

However, the Apache2 itself has not started because of this error I am getting..

This is what I get when I run : /etc/init.d/apache2 start : 

   [COLOR=RoyalBlue]root@ubuntu-server:~# sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs[/COLOR]
                                                                         [[COLOR=Red]fail[/COLOR]]


Btw, how to kill the Apache Procesess ?

Thank you..  :)

---

### Post by sahabcse on 2009-08-31
#ps -ax | grep -i apache

It gives the o/p like

eg)

3061 ?        Ss     0:00 /usr/sbin/apache2 -k start

Then run the command

#sudo kill -9 3061

---

### Post by ularlaut on 2009-08-31
Thank you very much Sahabcse.:)

It finally work, I can access my Apache server from my other Pc with web browser.

However, when I restart / reboot the Server, the same problem came up again.:(

[COLOR=RoyalBlue]   root@ubuntu-server:~# sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
                                                                     [/COLOR]    [[COLOR=Red]fail[/COLOR]]

So, when the reboot is completed I have to run all the (last/recent) script you have given me again.

Any idea why ? :confused:

And again, I thank you very-very much for your  kind assistance.

---

### Post by sahabcse on 2009-09-01
Have you installed any new package's before the apache error?

---

### Post by ularlaut on 2009-09-01
Hello again Sahabcse..

I only do the update and upgrade for the LAMP and Ubuntu system, using :

   # sudo apt-get update

and

   # sudo apt-get upgrade

I did not installed any specific packages...

---

### Post by sahabcse on 2009-09-01
Hi

check whether the apache and apache2 are installed and runing?

---

### Post by ularlaut on 2009-09-01
Hello...

Ehhmm..... could you provide me with the command on how-to check whether Apache or Apache2 is installed and running or not ?

Sorry about this, because this is my first time setting up Ubuntu Server with Apache (LAMP)..  ;-)

regards,

---

