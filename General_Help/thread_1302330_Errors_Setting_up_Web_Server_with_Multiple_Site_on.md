---
title: "Errors Setting up Web Server with Multiple Site on Ubuntu 9.04 i386 Server"
date: 2009-10-27
forum: General Help
---

### Post by Elliptic on 2009-10-27
Help anyone, I am new and keep getting this error setting up my server.
 
I get these errors when Starting up the Server; All is [ OK ] except when "Starting web server apache2". The next lines are exactly as follows:
 
[Mon Oct 26 20:38:47 2009] [error] VirtualHost *:80 -- mixing * ports and non-*ports with NameVirtualHost address is not supported, proceeding with undefined results
[Mon Oct 26 20:38:47 2009] [error] VirtualHost *:80 -- mixing * ports and non-*ports with NameVirtualHost address is not supported, proceeding with undefined results
[Mon Oct 26 20:38:47 2009] [warn] NameFirtualHost *:80 has no VirtualHosts
[ OK ]
 
I read in the forums about the Listen 80 and potentially I have something else listening to that port or something along those lines. All I have done is loaded Ubuntu 9.04 i386 Server edition. I installed the LAMP & openSSL options. Then once I booted up, I modified files as per the Getting Started Guide (which by the way is not very easy for us beginners to read and do). I added to the /etc/httpd.conf file the following:
 
NameVirtualHost *:80
 
<VirtualHost *:80>
ServerName *mywebsite1.com*
ServerAlias *[www.mywebsite1.com]("http://www.mywebsite1.com")*
DocumentRoot /var/www/*mywebsite1* (ok here I did not put any www. or .com on the name of my website. Just for creating a folder, that was all, is that wrong?)
</VirtualHost *:80>
 
<VirtualHost *:80>
ServerName *mywebsite2.com*
ServerAlias *[www.mywebsite2.com]("http://www.mywebsite2.com")*
DocumentRoot /var/www/*mywebsite2* (I did the same thing here on naming it)
</VirtualHost *:80>
 
My /etc/host.conf file is as follows:
 
# The "order" line is only used by old versions of the C library. order hosts, bind
multi on
 
My /etc/hosts file is as follows:
 
127.0.0.1 Localhost.localdomain *hostname(of Ubuntu Server)*
 
*myIPaddress hostname.mywebsite1 [www.mywebsite1.com]("http://www.mywebsite1.com")*
*myIPaddress hostname.mywebsite2 [www.mywebsite2.com]("http://www.mywebsite2.com")*
*(Where myIPaddress is equal to my IP address I set STATIC on my LAN. Hostname is of my Ubuntu Server name. Mywebsite1 or 2 is the domain w/o the www. or .com on it)*
 
# The following lines are desirable for IPv6 capable hosts 
::1 localhost ip6-localhost ip6-loopback
*blah, blah, blah (all that other stuff that looks pretty standard in this setup)*
 
Under my /etc/apache2/sites-available/*mywebsite1 (again here I did not us the www. or .com on the name), *I basically copied the Default folder then went in and modified the DocumentRoot section to match my /var/www/*mywebsite1.* I did the same thing for *mywebsite2.*
 
In all this, I cannot remember if I did some adjusting to other files or not, but if I did, it was in reference to Listen 80. I have reloaded my server 4 times now to clear out or wipe out all I did and restart fresh... it is getting anoying at this point.
 
Can anyone give me suggestions in my set up so far, what am I missing. It all sounds pretty easy, but that is how it sounds... pretty different doing...
 
Much Thanx in advance

---

