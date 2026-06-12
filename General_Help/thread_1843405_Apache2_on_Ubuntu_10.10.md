---
title: "Apache2 on Ubuntu 10.10"
date: 2011-09-13
forum: General Help
---

### Post by Murphy-10332 on 2011-09-13
To all who have contributed to ANY freeware, Thank you!! I very recently have been led of Jesus to scrap most every thing pertaining to Microsoft. As a result I have found Linux and the like to be very rewarding. That said,I may become a very active member of this forum. 
  If you need more outputs  or would like them to be configured differently please let me know and advise me.
Thank you in advance for any help that is offered.  on how to do it
  
Joshua Murphy


The issue is: I am unable to get a website viewable from outside my LAN. 

Hosts:
192.168.0.249    Webserver    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    Webserver    localhost6.localdomain6    localhost6
127.0.0.1           Ripples1-1.tk
127.0.0.1              Wordpress
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Ripples1-1.tk.conf
<VirtualHost *:80>
        ServerAdmin [email]webmaster@Ripples1-1.tk[/email]
        ServerName Ripples1-1.tk
        DocumentRoot /var/www/Ripples1-1.tk


</VirtualHost>

apache2.conf

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

---

### Post by Dangertux on 2011-09-13
Is there a router in front of the server? If there is you either need to port forward or DMZ the server.

---

### Post by Murphy-10332 on 2011-09-15
Yes there is a router in front of it. the router was not the issue. It appears the dns needed to update. Not sure why though, my dyndns has been up for awhile.

---

