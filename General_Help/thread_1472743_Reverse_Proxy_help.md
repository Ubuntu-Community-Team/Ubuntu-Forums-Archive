---
title: "Reverse Proxy help"
date: 2010-05-04
forum: General Help
---

### Post by PlugInPrius on 2010-05-04
I need some help getting a reverse proxy to work. I have it working fine on my windows box with at32 Reverse Proxy. It was very easy to setup. Anyway I'm wanting to replace that windows box with a Linux box.

Here is some background on what I'm trying to get done in Linux.

I have 
myserver1.mydomain.com
myserver2.mydomain.com
myserver3.mydomain.com

All pointing with a CNAME to my dyndns.org address. I have a dynamic IP from my ISP so I need this and its currently working just fine.

My ISP blocks port 80 so I have to use port 443. Port 443 seems to be the most reliable port to use since its one of the ports my ISP does not block and its one of the ports other places like hotels dont block.

So I want to access my bittorrent server. I type in [http://myserver1.mydomain.com:443](http://myserver1.mydomain.com:443) and the at32 Reverse Proxy points it to my internal server [http://bittorrent](http://bittorrent) on port 80.

I got this to work perfect in windows.


So right now I'm doing this all in a virtual machine for testing. I have Apache all setup and working with the reverse proxy except for my thermostat's web server.

Here is how I have it setup in the virtual machine.
The machine is called testbox and its running Ubuntu Alt 10.04 32bit
In that VM  I can go to [http://testbox](http://testbox) but it will only display the HTML code of the page. If I go directly to the main page on the thermostat [http://testbox/index.shtml](http://testbox/index.shtml) the web page renders just fine and all the links work.

My sites-available config file has this inside.

<VirtualHost testbox:80>
ProxyPass / [http://192.168.0.205/](http://192.168.0.205/)
ProxyPassReverse / [http://192.168.0.205/](http://192.168.0.205/)
</VirtualHost>

The config file is for port 80 but I think once I get things working in the testbox I should not have any problems switching it to port 443.

Can anyone help get this working?

---

### Post by PlugInPrius on 2010-05-06
Bump!

I'm still having issues getting my thermostat pages to display by just going to [http://testbox]("http://testbox/") and its still loads correctly if I go to [http://testbox]("http://testbox/")/index.shtml

Does anyone understand why?

This is the last piece of the Linux puzzle so I can get my server converted to Linux.

---

### Post by PlugInPrius on 2011-04-04
I had to rebuild my server recently and I still have this issue. I tried to access my thermostat with IE today from work and it will work just fine but FF will not display it correctly if I dont use the status.shtml.

So its either A. my reverse proxy. B. Fire Fox. or C. IE just being its self and not giving a crap about anything and just rendering the page.

Its not a big deal since I have dealt with it for about a year now but I just wanted to update this post with what I found.

---

