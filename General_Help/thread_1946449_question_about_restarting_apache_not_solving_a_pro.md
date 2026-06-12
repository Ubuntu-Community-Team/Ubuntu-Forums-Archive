---
title: "question about restarting apache not solving a problem with local host"
date: 2012-03-24
forum: General Help
---

### Post by imachavel on 2012-03-24
ok I don't want to start this thread off too confusing, so I won't get into make or model or my computer, motherboard, hdd type, drivers, any of that. This question is purely related to a web interface question. I will start though by providing my distro version:

lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

the problem I'm having is this, I've recently been toggling around the idea of updating my html page on a go daddy domain URL that is the front end interface index.html file. So I've been experimenting in local host in /var/www/localhost

[http://webdesignerwall.com/tutorials/installing-wordpress-locally](http://webdesignerwall.com/tutorials/installing-wordpress-locally)

[http://wordpress.org/download/](http://wordpress.org/download/)

I've installed lamp quite nicely, and even managed to install bb3 forums template interface. Now I was trying to use wordpress, and it seems a bit complicated, it all uses php, so the index file might be index.php instead of index.html. Now aside from all that, I decided to delete the index.html file and associated .jpg image from within the folder that is included in the index.html file tagged. So I took the index.html file, which includes an image, and the image that is tagged out. I haven't been able to get wordpress to work when I load [http://localhost](http://localhost) in the browser URL, or type in my computers i.p. address in the browser. So I decided to put index.html and the associated tagged .jpg image file back into the folder, and had to obviously use gksu nautilus in the terminal to get proper root permissions. Now that it's back in, nothing will load in the browser, but interesting enough when I type localhost in browser, the top bar above the address that names what you are looking at in the url to the right of the menu drop down bar it says home page | (name of html page)

I'm very confused to why this wasn't loading, so I decided to restart apache successfully:

[http://www.cyberciti.biz/faq/ubuntu-linux-start-restart-stop-apache-web-server/](http://www.cyberciti.biz/faq/ubuntu-linux-start-restart-stop-apache-web-server/)

#/etc/init.d/apache2 restart
 * Restarting web server apache2                                                ulimit: 88: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
ulimit: 88: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
danel@danel-Dimension-4700:~$ sudo /etc/init.d/apache2 restart
[sudo] password for danel: 
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


But it didn't resolve the issue. Any ideas on what to troubleshoot?

---

### Post by agillator on 2012-03-24
I know nothing about wordpress, so someone else will have to help you with that after you make sure apache is running properly. So, I would uninstall wordpress. I assume you installed LAMP through apt or at least from the repositories, not by going through all the compiling. Look in /etc/apache2/sites-enabled/000-default. Make note of the Document Root entry in the Virtual Host *:80 section. Go to that directory (Document Root) and create index.html that simply says IT WORKS! Delete (or move) any other file in that directory. Now, at the end of /etc/apache2/apache2.conf create a line "ServerName xxxx" with xxxx being the name of your server. Now try 'sudo /etc/init.d/apache2 restart' (or start if apache isn't running) and see what happens. If it restarts successfully, open your browser and go to localhost. You should see IT WORKS!. Once you have that working you can reinstall wordpress and fight with that.

---

### Post by imachavel on 2012-03-25
this is what's in the file:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
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

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


Now here is what is in apache2.conf


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
KeepAliveTimeout 5

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
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
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
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
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
```


I believe my server name is root, or is there a command I can run in the terminal that will show what local host is, I'm guessing [EMAIL="Danel@localhost.com"]Danel@localhost.com[/EMAIL], but I'm not sure, and also don't know where in the .conf file you'd want me to edit and add that line in there. Anyway, remember I also have bb3 forums installed which I don't plan on using, since I installed it but didn't configure the index.(extension) file, that is probably what is messing up the ability to use local host for anything else. My best guess is to take this advice I got from someone else:

"Try removing everything and starting again:
 
sudo rm -r /var/www/*
sudo service apache2 restart"


if that fixes it, then I'll come back to this thread, and reply that it's been solved.


Perhaps you are right and I should reset the server name:

sudo service apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

another note, I never created a dhcp server out of ubuntu, and never created a .conf for samba or dhcp. This local host I configured just so I could open it, not to try and view the web site by typing in the i.p. address of this computer, from another computer. I don't think I'd need to configure this to be a dhcp server, but from another computer I only have windows so I'd need to at least configure the samba.conf, to access this computers i.p. address. Both computers recieve an i.p. address from d.n.s. configuration from a web server from my i.s.p. I'd really have no need to hook up another router, and configure it to use a subnet mask range, and default gateway of a dhcp server. I want to keep it simple more of a home/work environment then a work environment

wait I noticed something else, it's using 127.0.1.1 for a server name instead of 127.0.0.1 as a loop back address. WTF :facepalm: I should try and change that

---

### Post by imachavel on 2012-03-25
not going too well..

sudo apt-get uninstall apache2
E: Invalid operation uninstall
danel@danel-Dimension-4700:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]


thanks for the help though

---

### Post by agillator on 2012-03-25
First, your USER NAME may be root, but not your server name. What is the name you give your web server - Fred, 'Useless-Information', 'I_Love_Football', or what? That's what goes in the server name line.When someone goes to your web site they will put something like webserver.somewhere.com in the address bar of their browser. In this case, webserver would be the server name.

Second, to remove something with apt, the command is sudo apt-get remove xxxx, not uninstall.

---

### Post by Bobhuber on 2012-03-25
> **imachavel said:**
> not going too well..

sudo apt-get uninstall apache2
E: Invalid operation uninstall
danel@danel-Dimension-4700:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]


thanks for the help though
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by imachavel on 2012-03-25
echo "ServerName localhost" | sudo tree /etc/apache2/conf.d/fqdn
[sudo] password for danel: 
/etc/apache2/conf.d/fqdn [error opening dir]

0 directories, 0 files

not too good. Any further suggestions of what to trouble shoot?

---

### Post by Bobhuber on 2012-03-25
> **imachavel said:**
> echo "ServerName localhost" | sudo tree /etc/apache2/conf.d/fqdn
[sudo] password for danel: 
/etc/apache2/conf.d/fqdn [error opening dir]

0 directories, 0 files

not too good. Any further suggestions of what to trouble shoot?
You need remove and reinstall apach2 following the post I gave you. I have no idea whats  screwed up with wordpress or what you did in trying to set it up along with correctly setting up PHP on the server.
sudo apt-get purge <list> using the list on the post

---

### Post by MG&amp;TL on 2012-03-25
Imachavel, He meant *tee*, not *tree*-*tee* is a program that writes output to a file and stdout at the same time. *tree* is a program that lists files in a set directory.

---

### Post by Bobhuber on 2012-03-25
> **MG&TL said:**
> Imachavel, He meant *tee*, not *tree*-*tee* is a program that writes output to a file and stdout at the same time. *tree* is a program that lists files in a set directory.
Thanks I didn't cache that.

---

### Post by imachavel on 2012-03-25
> **Bobhuber said:**
> Thanks I didn't cache that.

ahahah I didn't 'cache' that. Haha

---

### Post by imachavel on 2012-03-25
> **Bobhuber said:**
> You need remove and reinstall apach2 following the post I gave you. I have no idea whats  screwed up with wordpress or what you did in trying to set it up along with correctly setting up PHP on the server.
sudo apt-get purge <list> using the list on the post

ok removed apache as you suggested, reinstalled it, restarted the service

sudo service apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

same issue

as for mg&tl and other repliers reply:

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d.fqdn
ServerName localhost

out of curiosity, if I echo "ServerName localhost" won't it echo those names instead of listing server name in local host?

I understand there are ways to troubleshoot not being able to find the fully qualified domain in the link you gave me. However, they involved finding a .conf file in /etc/apache2 and editing it to see if restarting Apache gives a different syntax return. What was on the site you listed didn't seem to be extremely descriptive on how to edit that. I know you are just trying of course

danel@danel-Dimension-4700:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting        

got it, didn't realize fqdn just needed to be a one liner. Simple enough..
Strange, index.html doesn't load when I type in [http://localhost](http://localhost) in browser

---

