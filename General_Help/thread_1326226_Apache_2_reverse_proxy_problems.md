---
title: "Apache 2 reverse proxy problems"
date: 2009-11-14
forum: General Help
---

### Post by DanEames on 2009-11-14
I am fairly new to Linux/Ubuntu and have set myself some goals in order to get to know it better. One of the things I have been trying for sometime to setup is a reverse proxy to enable access to an IP camera that is behind a firewall.
 
My Apache 2 computer is accessible remotely using a dyndns account that resolves my dynamic IP to a fixed host. Using this I can see the standard "It Works" page remotely. I would like to be able to remotely access the cameras own html page and display a picture.
 
The camera is addressable as 192.168.0.6 on my nework. It doesn't have a host name and I don't have a local DNS server. That is for another day.
 
I have been changing the proxy.conf file trying different things including the mod_proxy_html module that I have found out about. I am not too sure that this module is installed and I can't figure out how to add more. It doesn't seem as simple as editing the httpd.conf and then restarting Apache.
 
A couple of things that don't work and I am not sure of the significance is httpd -l and aspx commands. These are refered to in a number of places but i can't work out their meaning.
 
Hopefully someone has some experience of this and doesn't mind offering some advice.
 
Thanks in advance,
 
Dan

---

### Post by DanEames on 2009-11-17
Polite nudge

---

