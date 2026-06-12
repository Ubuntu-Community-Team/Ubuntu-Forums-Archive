---
title: "Hosting My Website with LAMP server with Ubuntu 10.10"
date: 2011-03-31
forum: General Help
---

### Post by ModderXstatic on 2011-03-31
Alright everyone,
   I'm running with Ubuntu 10.10 Desktop edition and I have LAMP server installed on the machine. I'm wanting to host my Automotive Detailing website that I'm almost done with off of that server. I have decals made up for my car and friends cars with the domain that I have registered on it. Now, can someone please tell me where and how to put the files for my website on the server and how to configure everything so I can get it up and running ASAP?!? I'm fairly new at this Ubuntu and what not so I need a detailed tutorial please!!!!!

So this is what I need to know:
==> Where to put the webpage files
==> How to configure the server to open it up to the world wide web
==> How to change the IP Address to Static and how to know what to change it to.
==> How to point the registered domain to the server.


Any help would be awesome guys and gals. Like I said I'm fairly new at this so please be as detailed as possible!!
   Thanks!!!

---

### Post by EckoUnltd88 on 2011-04-01
im in the same sittuation, can anybody awnser this question, execpt its for a profesional IT site

---

### Post by IHeequ5i on 2011-04-01
Forgive my asking what may be a silly question, but...

Why not purchase hosting from a professional company? You would simply have to FTP your files from your existing server to the host.

If you want to run your own server, you'll have to purchase a static IP address from your ISP and have them update their DNS servers to point to it correctly. Most ISPs will charge extra for this service.

As you can probably tell, I recommend the first option. I use BlueHost ([http://www.bluehost.com](http://www.bluehost.com)) for all my website work. I've been with them for several years now, and had very few problems.

---

### Post by GnuDragon on 2011-04-01
Going to get hacked to death if you do it yourself and don't know how. It can be taught but it takes a long time to learn.

Use a pro-hosting company for a few dollars a month.

That will give you time to read up on security and hosting.

---

### Post by bodhi.zazen on 2011-04-01
> **ModderXstatic said:**
> Alright everyone,
   I'm running with Ubuntu 10.10 Desktop edition and I have LAMP server installed on the machine. I'm wanting to host my Automotive Detailing website that I'm almost done with off of that server. I have decals made up for my car and friends cars with the domain that I have registered on it. Now, can someone please tell me where and how to put the files for my website on the server and how to configure everything so I can get it up and running ASAP?!? I'm fairly new at this Ubuntu and what not so I need a detailed tutorial please!!!!!

So this is what I need to know:
==> Where to put the webpage files
==> How to configure the server to open it up to the world wide web
==> How to change the IP Address to Static and how to know what to change it to.
==> How to point the registered domain to the server.


Any help would be awesome guys and gals. Like I said I'm fairly new at this so please be as detailed as possible!!
   Thanks!!!

In general you put the files (html) in /var/www

You need to configure your router to forward port 80 to your server.

Your ip address is going to be assigned by your IP provider, so you need to discuss a static (public) ip address with them.

On your server, configure a static IP address.

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

You point your domain name to your ip address via your domain name provider. Most use web interfaces. If you do not know how to do that , contact your domain name provider, the place you registered your domain name. Know that it may take 24 hours for you to see the changes.

See also:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by GnuDragon on 2011-04-01
helpful info there that will get you running
 
However the security sections in those linked guides are a little brief and i  recommend you read up some extra guides on (google for) "Linux security" and "hardening  apache" at the very least before putting up a server
 
also recommend that you read up on defensive coding and database  injection before you push the app live as web apps have additional  security considerations over terminal apps. For example consider what  would happen if a user entered "z';drop  table users;--" into e.g. your login form, or fed in fake URL  parameters or just opened pages randomly without using the menus  (admin.php is an easy URL to guess)

you might not mind sharing user data/giving out root but it would NOT BE  COOL if the attacker then used your server to launch further attacks

 definitely google "hardening linux" , "linux security", "defensive coding", "sql injection" before you proceed

Edit --- Consider 10.04 LTS over 10.10 if it's a server you plan to keep up for a while. Really, really recommend you go for commercial hosting. Let the host worry about securing the machine, so you only have to write secure code.

---

