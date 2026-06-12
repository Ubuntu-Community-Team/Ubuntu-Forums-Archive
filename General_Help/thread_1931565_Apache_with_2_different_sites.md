---
title: "Apache with 2 different sites?"
date: 2012-02-25
forum: General Help
---

### Post by garyed on 2012-02-25
I have Apache2 installed & running fine. I can access it using localhost or from the web by typing in my ip address. If I set the directory in sites-enabled/default to /var/www/ then I can access all my pages but I'd like to go directly to my index page of my site. If I change the directory under <VirtualHost> to /var/www/mysite1/ then it will take me directly to that site but I have more than one site. I have added /var/www/mysite2/ also but I can only get to the first site listed by typing in my ip address. Is something I could type in to the address bar in the browser that could get me to mysite2?
Here's what the default file looks like:
```

<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/mysite1/
	ServerName  mysite1
</VirtualHost>
<VirtualHost *>
        ServerAdmin webmaster@localhost	
        DocumentRoot /var/www/mysite2/
	ServerName  mysite2
</VirtualHost>


```

---

### Post by josephmills on 2012-02-25
> **garyed said:**
> I have Apache2 installed & running fine. I can access it using localhost or from the web by typing in my ip address. If I set the directory in sites-enabled/default to /var/www/ then I can access all my pages but I'd like to go directly to my index page of my site. If I change the directory under <VirtualHost> to /var/www/mysite1/ then it will take me directly to that site but I have more than one site. I have added /var/www/mysite2/ also but I can only get to the first site listed by typing in my ip address. Is something I could type in to the address bar in the browser that could get me to mysite2?
Here's what the default file looks like:
```

<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/mysite1/
	ServerName  mysite1
</VirtualHost>
<VirtualHost *>
        ServerAdmin webmaster@localhost	
        DocumentRoot /var/www/mysite2/
	ServerName  mysite2
</VirtualHost>


```

did you also enter them into /ect/hosts ? here is a video 
[http://www.youtube.com/watch?v=2vA2Yzv-NoI](http://www.youtube.com/watch?v=2vA2Yzv-NoI)

---

### Post by garyed on 2012-02-25
Nice video but I've been working on it for hours with no luck.
He did it in 6 minutes & I followed everything exactly but it still doesn't work. There must be another configuration file that he's assuming doesn't need to be changed but it does for me. No matter which of the names I type in the address bar it still leads me right back to my original root index file.

---

### Post by garyed on 2012-02-26
I can change the sites-available/default file & make it work but for only one page no matter which site name I type in. I think there's something in that file that's causing the problem.
Anyone else have any ideas?

---

### Post by garyed on 2012-02-26
Well I got it working but i used a different video that did things a little differently.

[http://www.youtube.com/watch?v=yUWtrYlM_9c&feature=related](http://www.youtube.com/watch?v=yUWtrYlM_9c&feature=related)


I can access either site on my server by typing in the name in my browser. The thing I can't figure out now is how to access them from the internet.
If I type my ipaddress from another computer it always goes to the first site on the list. Since these are not registered domain names going to my computer I can't just type in the name on another computer so I have to type in my ip address to access my computer. Is there a way to type my ip address & the site name so my computer will know which site to display when being accessed from the internet?

---

### Post by xgrendel on 2012-02-26
What exactly are you trying to do?

From what it looks like, you would not need to use a separate Virtual Host if you are just using separate sub-directories within the www directory.

If you're trying to sandbox the sites for whatever purpose, you're going to hit a few snags. 

Here's what you have:

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/mysite1/
	ServerName  mysite1
</VirtualHost>
<VirtualHost *>
        ServerAdmin webmaster@localhost	
        DocumentRoot /var/www/mysite2/
	ServerName  mysite2
</VirtualHost>
```

And if I understand what you are saying, you are trying to do this:

http request-> 192.168.1.255/mysite1
http request-> 192.168.1.255/mysite2

If this is the case, it will not work. IIRC, Apache is looking for an HTTP request header with the host name set in it (mysite1 or mysite2). However, you are passing the IP address, not a host name. So Apache hits your first virtual host that is listening on all IPs/Ports, then tries to resolve the directory path. So if you do this:

http request-> 192.168.1.255/mysite1

Apache tries to resolve to this: 
/var/www/mysite1/mysite1

if you try this:

http request-> 192.168.1.255/mysite2

Apache tries to resolve this:
/var/www/mysite1/mysite2

I'm not 100% sure this will work but if you want to try to fake a domain name (mysite1.blah and mysite2.blah), you can try editing the host file on the *client* side to resolve the fake domain name to your server's IP address. I haven't tried it so I'm not sure if the browser will still pass the domain name in the header or not but it might be worth a shot to verify if you set up the virtual hosts correctly. If it does work, you should be able to do something like:

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/mysite1/
	ServerName  mysite1.blah
</VirtualHost>
<VirtualHost *>
        ServerAdmin webmaster@localhost	
        DocumentRoot /var/www/mysite2/
	ServerName  mysite2.blah
</VirtualHost>
```

http request-> mysite1.blah (from your browser)and hit your server

(I added the .blah as I'm not sure if Apache will accept a servername without the tld

If domain names are not going to be set up on the Internet side, you can probably just set up a dummy page at the root directory (/var/www/) so you can just enter the IP followed by the subdirectory your app lives in.

---

### Post by Bobhuber on 2012-02-26
+1 on the above post. There is realy no need to do anything other than setting up separate sub-directories in /var/www.
I have multiple sites on my server in /home/bob/webpages (changed from the default /var/www) with each site in a separate directory with its own index file. The easiest way to access the different sites from the web is to use a free service like Dyndns and set up DNS hosting thru there site. Then when you wish to access your site(s)  from the web you would enter <somename>.dydns.org/mysite1 replacing mysite1 with the name of the sub-directory on your server that contains the index file and pages you want. As far as accessing the local site from your machine just enter localhost/mysite1 again replacing mysite1 with the name of the subdirectory.
I'ts very handy when developing webpages to allow (in my case) customers to actually view my work before transferring the pages to a web host of there choice.

---

### Post by garyed on 2012-02-26
> **Bobhuber said:**
> ........................
I have multiple sites on my server in /home/bob/webpages (changed from the default /var/www) with each site in a separate directory with its own index file. The easiest way to access the different sites from the web is to use a free service like Dyndns and set up DNS hosting thru there site. Then when you wish to access your site(s)  from the web you would enter <somename>.dydns.org/mysite1 replacing mysite1 with the name of the sub-directory on your server that contains the index file and pages you want........... .
Thanks guys for the replies,
That's exactly what I want to do is access the different sites from the web.
I've done all the prep work with the directories etc. so locally each site can get accessed by typing its name in my browser. I'll look into Dyndns but does that mean that without a service like that there is no way to type in my ipaddress & the site names to access each different site?

---

### Post by pqwoerituytrueiwoq on 2012-02-26
not sure if you got it working but you may be better off running each site on a different port
i use 80, 81, 82 and 83 myself
```
~$ cat /etc/apache2/ports.conf 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
NameVirtualHost *:81
Listen 81
NameVirtualHost *:82
Listen 82
NameVirtualHost ***:83**
Listen **83**

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
``````
~$ cat /etc/apache2/sites-available/testing 
<VirtualHost ***:83**>
    ServerAdmin webmaster@localhost
    DocumentRoot /home/www-data/testing
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/www-data/testing/>
        Options FollowSymLinks
        AllowOverride All
        Options +Indexes
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ErrorLog /var/log/apache2/error.log
    CustomLog /var/log/apache2/access.log combined
</VirtualHost>
```

---

### Post by Bobhuber on 2012-02-26
> **garyed said:**
> Thanks guys for the replies,
That's exactly what I want to do is access the different sites from the web.
I've done all the prep work with the directories etc. so locally each site can get accessed by typing its name in my browser. I'll look into Dyndns but does that mean that without a service like that there is no way to type in my ipaddress & the site names to access each different site?
Not at all if you want to use the IP address and its static.
[In the address bar use your  IP address with the directory name >     72.185.17.xxx/mysite1]("http://72.185.17.xxx/mysite1")
However if your IP address changes on a daily basis its much easier to use Dydns. As stated it's free.

---

### Post by garyed on 2012-02-26
Now I get it. That was easy, everything works locally & from the web now too. 

So when you run a shared server & a domain name is forwarded to your server can I assume the name is tagged to the end of the servers ip address so it would know what directory to use for its website.

---

