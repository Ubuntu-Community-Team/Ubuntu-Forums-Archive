---
title: "make a directory that is visable on the internet"
date: 2009-11-08
forum: General Help
---

### Post by metalmaniac248 on 2009-11-08
i installed a couple of packages, they were "apache2" "libapache2-mod-php5" and "php5"  these allowed me to have a folder called "/var/www" where everything in it was visible on the network that my computer is attached to

is there any way to have one of these folders that is visible to the entire web?

---

### Post by oscurochu on 2009-11-08
Set up port forwarding on your router. Instructions vary, depending on the brand and model number of the router.

---

### Post by P4man on 2009-11-08
that folder already is accessible on the internet, provided your router forwards port 80 to our machine.  To access it someone not on your network will need to use your public IP. If you dont know it, this will tell you:
[http://www.whatismyip.com/](http://www.whatismyip.com/)

someone else could then access your "website" with

[http://123.123.123.123](http://123.123.123.123) (replace those with your public IP obviously)

If you prefer a name and/or if you have a dynamic IP that changes regularly you may want to use something like:

[http://www.no-ip.org](http://www.no-ip.org)

Or purchase a domain name..

---

### Post by metalmaniac248 on 2009-11-08
orite thanks if i could just get access to my router im sure that would work, for some odd reason the admin password for the router is not the default one. :confused:

---

### Post by tommynz1975 on 2009-11-08
making your system more open to the out side world, you may want to add a post to 
[Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338")

and ask for notes on making your system more secure. if this is required.

unless some one here would like to comment.

---

### Post by metalmaniac248 on 2009-11-08
well that wont be a problem if i cant get access to my routers administration settings

---

### Post by oscurochu on 2009-11-08
Every router has a reset switch. Hold it down with a pen, or something small enough to press it. After resetting it, your default password should be restored, along with the factory settings. I am assuming your are the owner and administrator of the router.

---

