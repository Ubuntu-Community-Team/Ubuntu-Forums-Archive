---
title: "Virtual Host 403 Forbidden"
date: 2011-08-05
forum: General Help
---

### Post by coscos on 2011-08-05
I got a problem when I tried to setup a virtual host on my ubuntu server. The virtual host is under /var/www, called mytest.com. For some reason, I always get 403 forbidden when I tried to access it. I am on Ubuntu 10.10 server. Following is my settings, can somebody point out what is wrong?

permission of dir /var/www
> ls -l /var/www/

total 12
drwxr-xr-x 2 root root 4096 2011-08-04 11:26 mytest.com
-rwxr-xr-x 1 root root  177 2011-07-25 16:10 index.html

/etc/hosts file
> cat /etc/hosts

127.0.0.1    localhost 
127.0.1.1    americano
192.168.2.5    americano.mytest.com [www.mytest.com](www.mytest.com)

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

site config:
> <VirtualHost *>
    ServerAdmin [email]admin@mytest.com[/email]
    ServerName [www.mytest.com](www.mytest.com)
    ServerAlias mytest.com

    DocumentRoot "/var/www/mytest.com"

    ErrorLog /var/log/apache2/mytest-error_log
    CustomLog /var/log/apache2/mytest-access_log combined

    #
    # This should be changed to whatever you set DocumentRoot to.
    #
    <Directory "/var/www/mytest.com">
        Options -Indexes FollowSymLinks
        AllowOverride None

    Order allow,deny
    Allow from all
    </Directory>
</VirtualHost>

This server's ip is 192.168.2.5. When I went to [http://192.168.2.5](http://192.168.2.5) from my desktop, the apache default site loaded correctly. And then I added an entry "192.168.2.5 www.mytest.com" to the host file of my desktop. This time when I tried "http://www.mytest.com", I got the 403 error.

I appreciate your help!

---

### Post by CSimpson on 2011-10-05
For anyone else reading this (or if the OP hasn't solved it yet) I had this problem, and fixed it pretty simply.

I went to the folder in question, lets call it "/var/www/some_website", right clicked it, and set "folder access" to "access files".  I enclose a picture showing exactly that:

[IMG]http://i56.tinypic.com/6icop5.png[/IMG]

This is usually set by default, but was not the case for me.  For the record, in my case this was possibly because I was using a symlink, not a real folder.

You may need root permissions (depending on circumstances), in which case open a file browser by running "sudo nautilus" in a terminal.

---

### Post by sgmurphy19 on 2011-10-06
Make sure the files in the folder all have a chmod of 644 and the folders a chmod of 755.
Here are two easy commands to make that happen:
For directories
find . -type d -exec chmod 755 {} \; 
For files
find . -type f -exec chmod 644 {} \;

Note: you need the semicolon at the of the commands.

---

