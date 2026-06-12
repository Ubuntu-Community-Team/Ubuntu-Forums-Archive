---
title: "Set Name for localhost"
date: 2009-07-11
forum: General Help
---

### Post by mthalis on 2009-07-11
I installed apache2 and run my web pages. I run my web pages using below urls. 
> [http://localhost](http://localhost) 
[http://ip](http://ip)


In same network if i give other to view my web page they have view pages using ip address. I want to set name for ip address.

like
> [http://10.1.12.12/](http://10.1.12.12/) to
[http://mthalis/](http://mthalis/)

---

### Post by Jebtrix on 2009-07-11
I'd say you'd have to add your IP to Websitename to the hosts files on each persons comp you want to test with.


Windows based systems:
C:\WINXP\system32\drivers\etc\hosts
C:\WINNT\system32\drivers\etc\hosts
C:\WINDOWS\system32\drivers\etc\hosts
C:\WINDOWS\hosts

For Linux based system:
/etc/hosts

---

### Post by mthalis on 2009-07-11
Can you give more details here. Example configuration? please.

---

### Post by Jebtrix on 2009-07-11
Linux example:

```
127.0.0.1	localhost
127.0.1.1	ubuntumachine
172.16.108.2    somewebsite <--- your ip, whatever name you want

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Windows:

```
# Copyright (c) 1993-1999 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost
172.16.108.2    somewebsite  <-- same as linux example above

```

Then you can get to it by [http://somewebsite](http://somewebsite)

---

### Post by mthalis on 2009-07-11
It works only local machine, if i go other machine in same network and brows. that not working, instead of go to my web site it search web site equal to that name.
pleas help..
> 
127.0.0.1	localhost
127.0.1.1	ites-desktop
192.168.20.253  dinesh

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by credobyte on 2009-07-11
Not 100% sure if it will work from other local PC's, but .. 

Open config :
```
sudo gedit /etc/apache2/apache2.conf
```
Add :
```
ServerName local.webserver
```

---

### Post by Jebtrix on 2009-07-11
On the other machine you tried [http://dinesh](http://dinesh) and it went to search? Easy way to tell if the host file is being used is either console on win, or terminal on linux and:

```
ping dinesh
```

PING dinesh (172.16.108.129) 56(84) bytes of data.

Basically it should be resolving dinesh to the specified IP.

---

### Post by mthalis on 2009-07-11
I coud't ping 
ping: Unknow host 
please any way to do it?

sudo gedit /etc/apache2/apache2.conf i can't find ServerName.

---

### Post by credobyte on 2009-07-11
> **mthalis said:**
> I coud't ping 
ping: Unknow host 
please any way to do it?

sudo gedit /etc/apache2/apache2.conf i can't find ServerName.

I said ADD, not CHANGE ;)

---

### Post by mthalis on 2009-07-11
I add and restart apache and type
> [http://local.webserver/](http://local.webserver/) 
gave addres not found error

---

### Post by credobyte on 2009-07-11
In that case, bind9 would be the best ( maybe the easiest way as well ) choice : [http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html](http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html) ( instead of foo.com, use whatever you want ).

---

### Post by Jebtrix on 2009-07-11
I'm not sure what your doing wrong, I've did exactly what your trying to do at work several times. Shouldnt have to but did you try logging out/loggin in on the machine you added the ip to the host file.

---

### Post by OldAlgis on 2009-07-11
> **mthalis said:**
> I add and restart apache and type

gave addres not found error

Addresses in /etc/hosts will only work on your own network.

---

### Post by mthalis on 2009-07-11
My apache.conf

[PHP]#
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
#ErrorDocument 402 http://www.example.com/subscription_info.html
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

# I add this
ServerName local.webserver

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/




[/PHP]



I add this
> ServerName local.webserver
end of apache.conf

default
[PHP]<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/wifidog-auth/wifidog
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>[/PHP]

host file
[PHP]0.0.1	localhost
127.0.1.1	ites-desktop
192.168.20.253  dinesh

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/PHP]

---

### Post by itsjareds on 2009-07-11
Not that the other ideas will not work, but if all the computers are on the same network (same public IP) you could also set their DNS to OpenDNS then add some shortcuts from the OpenDNS dashboard. Works the same way, but there's only one area you have to configure and you can get multiple computers on it.

---

### Post by Jebtrix on 2009-07-11
> **OldAlgis said:**
> Addresses in /etc/hosts will only work on your own network.

**In same network** if i give other to view my web page they have view pages using ip address. I want to set name for ip address.

Thats what he said.

---

### Post by mthalis on 2009-07-11
My server ip is 192.168.20.253

Issue dhcp 192.168.20.1 to 20

another program that allow to access internet using proxy.

my proxy 

[PHP]
#!/bin/sh 
# IPTABLES  PROXY  script for the Linux 2.4 kernel.
# This script is a derivitive of the script presented in
# the IP Masquerade HOWTO page at:
# www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html
# It was simplified to coincide with the configuration of
# the sample system presented in the Guides section of
# www.aboutdebian.com

# This script is presented as an example for testing ONLY
# and should not be used on a production proxy server.

#    PLEASE SET THE USER VARIABLES
#    IN SECTIONS A AND B OR C
echo -e "\n\nSETTING UP IPTABLES PROXY..."
 
# === SECTION A ===
#   FOR EVERYONE SET THE INTERFACE DESIGNATION FOR THE NIC CONNECTED TO YOUR INTERNAL NETWORK
#   The default value below is for "eth0".  This value 
#   could also be "eth1" if you have TWO NICs in your system.
#   You can use the ifconfig command to list the interfaces
#   on your system.  The internal interface will likely have
#   have an address that is in one of the private IP address
#   ranges.
#   Note that this is an interface DESIGNATION - not
#   the IP address of the interface.
#   Enter the internal interfaces designation for the INTIF variable

 
INTIF="eth1"
 
 
#   SET THE INTERFACE DESIGNATION FOR YOUR "EXTERNAL" (INTERNET) CONNECTION
#   The default value below is "ppp0" which is appropriate 
#   for a MODEM connection.
#   If you have two NICs in your system change this value
#   to "eth0" or "eth1" (whichever is opposite of the value
#   set for INTIF above).  This would be the NIC connected
#   to your cable or DSL modem (WITHOUT a cable/DSL router).
#   Note that this is an interface DESIGNATION - not
#   the IP address of the interface.
#   Enter the external interfaces designation for the EXTIF variable:

 
EXTIF="eth0"
 
 
# ! ! ! ! !  Use ONLY Section B  *OR*  Section C depending on
#  ! ! ! !   the type of Internet connection you have.
# === SECTION B
# -----------   FOR THOSE WITH STATIC PUBLIC IP ADDRESSES
  # SET YOUR EXTERNAL IP ADDRESS
  #   If you specified a NIC (i.e. "eth0" or "eth1" for
  #   the external interface (EXTIF) variable above,
  #   AND if that external NIC is configured with a
  #   static, public IP address (assigned by your ISP),
  #   UNCOMMENT the following EXTIP line and enter the 
#   IP address for the EXTIP variable:

EXTIP="192.168.101.232"
 
# === SECTION C
# ----------   DIAL-UP MODEM, AND RESIDENTIAL CABLE-MODEM/DSL (Dynamic IP) USERS
# SET YOUR EXTERNAL INTERFACE FOR DYNAMIC IP ADDRESSING
#   If you get your IP address dynamically from SLIP, PPP,
#   BOOTP, or DHCP, UNCOMMENT the command below.
#   (No values have to be entered.)
#         Note that if you are uncommenting these lines then
#         the EXTIP line in Section B must be commented out.
#EXTIP="`/sbin/ifconfig ppp0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
# --------  No more variable setting beyond this point  --------

echo "Loading required stateful/NAT kernel modules..."
/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ip_nat_irc
echo "    Enabling IP forwarding..."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
echo "    External interface: $EXTIF"
echo "       External interface IP address is: $EXTIP" 
echo "    Loading proxy server rules..."
 
# Clearing any existing rules and setting default policy

iptables -P INPUT ACCEPT
iptables -F INPUT 
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT 
iptables -P FORWARD DROP
iptables -F FORWARD 
iptables -t nat -F
 
#This is where you would probably want to put rules banning MAC addresses of naughty users

# FWD: Allow all connections OUT and only existing and related ones IN
iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
 
# Chriss rule to stop port 22 traffic passing from wireless clients

iptables -A INPUT -p tcp -i $INTIF --dport 22 -j DROP
 
# Enabling SNAT (MASQUERADE) functionality on $EXTIF

iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
echo -e "       Proxy server rule loading complete\n\n"
 
echo -e " We are now starting the DHCP server on eth1 \n\n"
dhcpd eth1
[/PHP]

eth0 192.168.101.232 go internet
eth1 192.168.20.254 issue dhcp

any comments

---

### Post by mthalis on 2009-07-11
I explain my whole program

I have two server gateway server and authentication server, gateway server issue ip using dhcp, and so after issue ip user go to auth server and get permission to go Internet if user success he can go Internet using that ip, what i want is when user try to go to authserver, load web page so that web page load using ip(auth server) so i want to change that ip to name
[http://192.168.20.253](http://192.168.20.253)
http"//dinesh

That's what i want.

---

### Post by mthalis on 2009-07-13
Running DNS server in my apache machine can I success or not ..

---

### Post by mthalis on 2009-07-14
I found answer if you want clik link
[http://www.linuxforums.org/forum/ubuntu-help/127525-how-setup-domain-name-my-ubuntu-webserver.html](http://www.linuxforums.org/forum/ubuntu-help/127525-how-setup-domain-name-my-ubuntu-webserver.html)

---

