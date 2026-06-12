---
title: "VMs hosted in Ubuntu"
date: 2009-11-23
forum: General Help
---

### Post by tdk1964 on 2009-11-23
Hi,
First an foremost, I am a Ubuntu newbie and still trying to find my way around so apologies for what might be a basic question.

I have VMWare Server running on my Ubuntu Server 9.10. I have created a new Win 2K3 Server VM and want to make this servers web server externally accessible. 

Ubuntu Server: 192.168.0.2
Win2K3 VM:     192.168.0.18
My external IP: xxx.xxx.xxx.xxx

I can browse to 192.168.0.18 on my WinXP laptop and this displays the site ok. 
I can also browse to mydomain.co.uk and this displays the Apache default site on my Ubunto server (It Work's)
So what I need to do now is have my sub domain resolve to my Win2K3 VM (192.168.0.18 )

My domain: [www.mydomain.co.uk](www.mydomain.co.uk) --> xxx.xxx.xxx.xxx --> 192.168.0.2
My sub domain: sub.mydomain.co.uk --> xxx.xxx.xxx.xxx --> 192.168.0.18

My problem is I don't have a clue what to do next. Any help would be appreciated.

---

### Post by sefs on 2009-11-23
That to me sounds like a dns server project, where you would have to install bind9.  

You should Google bind9 and see if you need an internal dns server to direct request appropriately on your local network, once they hit your network.

---

### Post by bodhi.zazen on 2009-11-23
> **tdk1964 said:**
> Hi,
First an foremost, I am a Ubuntu newbie and still trying to find my way around so apologies for what might be a basic question.

I have VMWare Server running on my Ubuntu Server 9.10. I have created a new Win 2K3 Server VM and want to make this servers web server externally accessible. 

Ubuntu Server: 192.168.0.2
Win2K3 VM:     192.168.0.18
My external IP: xxx.xxx.xxx.xxx

I can browse to 192.168.0.18 on my WinXP laptop and this displays the site ok. 
I can also browse to mydomain.co.uk and this displays the Apache default site on my Ubunto server (It Work's)
So what I need to do now is have my sub domain resolve to my Win2K3 VM (192.168.0.18 )

My domain: [www.mydomain.co.uk]("http://www.mydomain.co.uk") --> xxx.xxx.xxx.xxx --> 192.168.0.2
My sub domain: sub.mydomain.co.uk --> xxx.xxx.xxx.xxx --> 192.168.0.18

My problem is I don't have a clue what to do next. Any help would be appreciated.

Depends on your router. Many routers can only forward one instance of port 80.

If this is the case you will need to use a reverse proxy. You can use eithe rpound or nginx.

Personally I prefer nginx ;)

Both are in the Ubuntu repos.

[https://help.ubuntu.com/community/Nginx/ReverseProxy](https://help.ubuntu.com/community/Nginx/ReverseProxy)

[http://www.apsis.ch/pound/](http://www.apsis.ch/pound/)

So set up say nginx in a minimal VM , give it an ip of 192.168.0.100

forward your public ip to 192.168.0.100 and proxy server your  other servers.

apache can be configured as a reverse proxy as well.

---

### Post by sefs on 2009-11-23
Amazing info.

---

### Post by dcstar on 2009-11-23
> **tdk1964 said:**
> Hi,
First an foremost, I am a Ubuntu newbie and still trying to find my way around so apologies for what might be a basic question.

I have VMWare Server running on my Ubuntu Server 9.10. I have created a new Win 2K3 Server VM and want to make this servers web server externally accessible. 

Ubuntu Server: 192.168.0.2
Win2K3 VM:     192.168.0.18
My external IP: xxx.xxx.xxx.xxx

I can browse to 192.168.0.18 on my WinXP laptop and this displays the site ok. 
I can also browse to mydomain.co.uk and this displays the Apache default site on my Ubunto server (It Work's)
So what I need to do now is have my sub domain resolve to my Win2K3 VM (192.168.0.18 )

My domain: [www.mydomain.co.uk](www.mydomain.co.uk) --> xxx.xxx.xxx.xxx --> 192.168.0.2
My sub domain: sub.mydomain.co.uk --> xxx.xxx.xxx.xxx --> 192.168.0.18

My problem is I don't have a clue what to do next. Any help would be appreciated.

Put in an Apache rule that forwards all requests to that name to the Windows IP address.

Since you have only one external IP address there is nothing else you can do.

---

### Post by tdk1964 on 2009-11-24
Thanks for all you advise. I'm nearly there, here's what I done so far.

### THIS WORKED ###
<VirtualHost *:80>
	ServerName myserver.co.uk
	ServerAlias myserver.co.uk
	DocumentRoot /var/www/myserver.co.uk
</VirtualHost>

### THIS WORKED ###
<VirtualHost *:80>
	ServerName sub.myserver.co.uk
	ServerAlias sub.myserver.co.uk
	DocumentRoot /var/www/sub.myserver.co.uk
</VirtualHost>

### THIS WORKED ###
<VirtualHost *:80>
	ServerName sub.myserver.co.uk
	DocumentRoot /var/www/sub.myserver.co.uk
	Redirect / [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) # My Windows VM
</VirtualHost>

So far so good, all pretty basic stuff. However that's where is all ends. The following didn't work

### NOT WORKING ###
<VirtualHost *:80>
	ServerName sub.myserver.co.uk
	ProxyPass / [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx)
	ProxyPassReverse / [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) # My Windows V
</VirtualHost>

### NOT WORKING ###
<VirtualHost *>
    ServerName sub.myserver.co.uk
    DocumentRoot /var/www
    ProxyRequests Off
    <Proxy *>
       Order deny,allow
       Allow from all
    </Proxy>
    ProxyPass / [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) # My Windows V
    ProxyPassReverse / [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) # My Windows V
    ErrorDocument 503 "The server is currently offline."
</VirtualHost>

So now I'm stuff :(

---

### Post by dcstar on 2009-11-24
You may want to set up the VM web server on port 81, and then redirect all incoming requests for it on port 80 to the VM IP address and port 81.

---

### Post by tdk1964 on 2009-11-25
OK finally figured it all out. For those interested this it what I did.

Firstly I needed to run these commands
sudo a2enmod proxy
sudo a2enmod proxy_http

Secondly I edited the /etc/apache2/httpd.conf and added the following. Apparently when using virtual host the first entry is your default website.

<VirtualHost *:80>
	ServerName mydomain.co.uk
	ServerAlias mydomain.co.uk
	DocumentRoot /var/www/mydomain.co.uk
</VirtualHost>

<VirtualHost *:80>
	ProxyRequests Off
	ProxyPreserveHost On
	<Proxy *>
		Order deny,allow
		Allow from all
	</Proxy>
	ProxyPass / [http://192.168.0.3/](http://192.168.0.3/)
	ProxyPassReverse / [http://192.168.0.3/](http://192.168.0.3/)
	ServerName sub.mydomain.co.uk
</VirtualHost>

---

### Post by dcstar on 2009-11-25
> **tdk1964 said:**
> OK finally figured it all out. For those interested this it what I did.
.........

Good work, now please have a read of my sig and mark this thread appropriately.

---

### Post by sefs on 2009-12-03
> **tdk1964 said:**
> OK finally figured it all out. For those interested this it what I did.

Firstly I needed to run these commands
sudo a2enmod proxy
sudo a2enmod proxy_http

Secondly I edited the /etc/apache2/httpd.conf and added the following. Apparently when using virtual host the first entry is your default website.

<VirtualHost *:80>
	ServerName mydomain.co.uk
	ServerAlias mydomain.co.uk
	DocumentRoot /var/www/mydomain.co.uk
</VirtualHost>

<VirtualHost *:80>
	ProxyRequests Off
	ProxyPreserveHost On
	<Proxy *>
		Order deny,allow
		Allow from all
	</Proxy>
	ProxyPass / [http://192.168.0.3/](http://192.168.0.3/)
	ProxyPassReverse / [http://192.168.0.3/](http://192.168.0.3/)
	ServerName sub.mydomain.co.uk
</VirtualHost>

Some questions.

1/
Did you need to install either rpound or nginx?  You didn't say

2/
Your ubuntu was at .02 and your win2k3 at .18

How did you manage to get .03 work into the mix such that your subdomain resolves to .18

Thanks.

---

### Post by bodhi.zazen on 2009-12-03
Those configs are all using apache as a reverse proxy.

---

