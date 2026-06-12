---
title: "Access Apache externally"
date: 2011-08-16
forum: General Help
---

### Post by rensell on 2011-08-16
Good evening all.

I have ubuntu 10.04 up and running with LAMP. I recently moved, so I just got the server up and running. I've been developing a new site and I need to access my webserver externally.

I have domain.com and this server is located at lamp.domain.com because I do not use it as my main webpage. I have my dns records set to transfer to my ISP IP address.

I have port forward setup and I know it works (If I forward port 80 to my security camera DVR I can access to web interface) however when I forward port 80 to my LAMP box, it just sits there before Opps! Google Chrome could not connect to.... I used to be able to access this box externally and now that I'm at a new location something is mucked up.

It's frustrating the **** out of me and any and all help is greatly appreciated. TYIA,

Ray

---

### Post by rensell on 2011-08-18
come on, anyone? Please...

---

### Post by georgemc on 2011-08-18
I would first establish what works with the server.
 

 
[LIST=1]
[*]does web browsing work using     either “localhost” and “127.0.0.1”?
[*]next I would browse from a     different system on the local network using the IP of the server.     Use “ifconfig” to determine the current IP. You probably done     that already.
[*]Double check the routers     forwarding settings.
[*]If your ISP is using dynamic IP     look into a DDNS provider.
[/LIST]
 

 I just setup a LAMP on my LAN and my ISP uses dynamic IP.
 

 Been using DDNS for years now on my router and I have ample opportunity to verify.
 

 I initially had port 80 blocked in the server firewall.  This showed up when I attempted to connect from another system on my LAN using IP addressing.
 

 I would suggest to trouble shoot a layer at a time, using IPs first on the lan then move outward.  Once it runs with IP addressing then dig through the DNS issues.
 

 Hope this helps.
 

 George

---

### Post by georgemc on 2011-08-18
Some other things to look at.
 

 On Apache I used default settings as much as possible.  Make sure your <Directory> directives and any kind of authentication are good.  I also force the entire site to HTTPS with rewrite rules in /var/www/.htaccess.
 

 Other Apache config files to look at:
 /etc/apache2/sites-available/default | default-ssl
 /etc/apache2/httpd.conf
 

 Any quirk with these should show up locally on the server itself.
 

 The “OOPS” from the browser is basically saying “I sent a request and it timed out”, could be a bad URL path, misconfigured server, or blocked some where.
   
 

Just additional thoughts.
 

 George

---

### Post by rensell on 2011-08-18
Thank you for the reply. Finally somethings to try. I know the server is running and working, because I am accessing the samba share - I share my /var/www file to simplify development. I can navigate to the IP address of the server from my laptop as well as the host name and they load the appropriate page(s).

My ISP is not using a dynamic IP address. I haven't changed any of the config files since I moved, so I'm really stumped.

I have even put the server in the DMZ of my router and it's still a no go... I don't fully understand all the configuration files so I'm not really sure where to go from here.

---

### Post by jramshu on 2011-08-18
Does the server have a static ip? 

If the router powers off, and the server is set up as dynamic, the router will assign a different ip and it will change the servers ip and the router will port forward to the wrong ip.

EDIT: Even if it's in the DMZ.

---

### Post by rensell on 2011-08-18
So, I just SSH'd into the server and got the XX updates available, blah blah and figured I'd run some updates, however ```
Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
``` so I tried ```
ping google.com
``` and I get an "unknown host google.com" error however I can ping my router 192.168.1.1 and it works just fine.

So, it looks like it's NOT an apache issue, but another issue, one of which I have no idea where to start.

Anyone?? Please??

---

### Post by rensell on 2011-08-18
Sorry, jramshu. Just saw your post. Yes the server has a static IP.

---

### Post by tcsmith1978 on 2011-08-19
Can u check /etc/resolv.conf and see if you have valid namservers set up there?

---

### Post by rensell on 2011-08-19
I believe that my resolv.conf is correct. It had the IP address and name of the bridge that it was connected to. However, I now have it connected directly to my router, so I updated the IP address to 192.168.1.1 - it's a linksys POS router. But I'm not sure what to change the domain and search lines to. I'm not sure that I ever had to edit this file before.

---

### Post by tcsmith1978 on 2011-08-20
Your resolv.conf seems the same as mine.

I had this problem when I first set up my server. Just trying to think of all the things that I had to look at to get it working! In iptables have you allowed access to port 53 - this may be why hosts can't be resolved.

---

