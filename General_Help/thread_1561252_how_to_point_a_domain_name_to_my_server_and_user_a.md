---
title: "? how to point a domain name to my server and user accounts"
date: 2010-08-26
forum: General Help
---

### Post by Bushcraft Bill on 2010-08-26
I am thinking of getting a domain name or ten I do not know were to point the domain to?

and what do I need to setup if a user wants a domain name to point to his account on the server? ok more like I want to have a few domains pointing to my user accounts I have setup on the server..can I do this directly or do I need a server domain first before users can get a domain name?

I have a basic setup user web space and ftp and mysql setup 

what extra would I have to install or not to be able to get a domain pointed to my server and/or user accounts?

I don't seem to be able to find anything specific on how to set this up anywhere...

Bill

---

### Post by Peter09 on 2010-08-26
The best way is to go through to a company.
 
In the UK I use a company called easyspace which sells domain names, and optionally hosts them. 
 
You buy the name and they will register it and provide simple email accounts. You then point the domain name, via the DNS servers (they provide the utility to do this on their website) to your IP address. This gets circulated through the internet so that your domain name links to your IP address.
 
They do not host your domian (unless you require and wish to pay for it).
 
I am sure there are many other providers of this service,  just do a search.

---

### Post by Bushcraft Bill on 2010-08-26
yes I know I have to register a domain name an they will point it my way but what ip do I use? but what do I have to do on my end to get it to work?

and how to set it up on my end so that different domain names can go to specific user accounts as I don't know does each user account get their own ip? their is not much info that specifically tells me how its done...

> **Peter09 said:**
> The best way is to go through to a company.
 
In the UK I use a company called easyspace which sells domain names, and optionally hosts them. 
 
You buy the name and they will register it and provide simple email accounts. You then point the domain name, via the DNS servers (they provide the utility to do this on their website) to your IP address. This gets circulated through the internet so that your domain name links to your IP address.
 
They do not host your domian (unless you require and wish to pay for it).
 
I am sure there are many other providers of this service,  just do a search.

---

### Post by Peter09 on 2010-08-26
The IP address that you will use will be the one that is hosting your server, if you are hosting at home it will be the IP address of your connection - it will be shown in your router. Make sure you have a fixed IP address, some providers will change yout IP address.
 
In Apache (and I'm sure other webservers) there is a facility for Virtual Websites, when an HTTP message arrives the Webserver directs it to the webpage/site that is defined by its domain name (not IP address). So [www.<yoursiteA>.com]("http://www.<yoursiteA>.com") goes to one set of pages while [www.<yoursiteB>.com]("http://www.<yoursiteB>.com") goes to a different set of pages on the same server. You need to read up on it.

---

### Post by Bushcraft Bill on 2010-08-26
yes its a home server I have setup and i have a fixed IP so thats all their is to that part just point it to my IP on the server not the router thats easy enough then..

now how do I setup more domains and also sub domains as I want to do both depending on what I am doing.. so how do I point domain names to user accounts though like user1 user2 user3 user4 that kind thing is what I also want to know!

---

### Post by Peter09 on 2010-08-27
> yes its a home server I have setup and i have a fixed IP so thats all their is to that part just point it to my IP on the server not the router thats easy enough then..

 
Just to confirm, you need to point the DNS servers for the Domain to your external Routers IP address (the one your ISP provides), not the servers internal IP address. You then use port forwarding on your router to direct traffic of type HTTP from your router to your server.
 
As said before Apache (for instance) supports virtual websites. The webserver can tell which website was used in the call (even though they all come through the same IP address). So although DOMAIN A and DOMAIN B point to the same external IP address the webserver can distinguish them and send the request to a different part of the webserver (site).
 
You really need to go to the online documentation of Apache (or other webserver) and read up on virtual websites.

---

### Post by Peter09 on 2010-08-27
Note - you also appear to want to have user accounts. This will be part of the functionality of the webserver. Basically your user will get a login prompt - which identifies the user to the webserver, from there the user can be directed to thier own account area. This functionality is all part of the webserver. You need to decide what application (webserver) you want and how you will use it. Then read the documentation.
 
Apache comes free with Ubuntu - and a few other webservers as well.

---

### Post by Bushcraft Bill on 2010-08-27
OK got it sorted out...

---

