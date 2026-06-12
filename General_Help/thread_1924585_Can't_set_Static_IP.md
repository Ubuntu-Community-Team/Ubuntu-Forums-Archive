---
title: "Can't set Static IP"
date: 2012-02-13
forum: General Help
---

### Post by antiacus on 2012-02-13
This is killing me.  I'm needing a static ip for fully qualified domain name to install a webserver platform.

I'm running ubuntu 11.1

I click on networks, click "edit connections", select my connection, click ipv4 settings, change to "manual"
Then for address i use 127.0.0.1 because that's what the platform suggested using.  
For Netmask i checked "connection information" button from the main network access in ubuntu gui, so i added mask of 255.255.254.0 (also tried 255.255.255.0), 
For gateway i've tried a whole bunch of things based on what see others doing in various youtube videos on the subject, but i'm kinda clueless what this should be.  
For DNS servers: i tried using 127.0.0.1  

So yeah, i'm a newb, but i'm trying hard!

I don't know if i'm fouling myself up by using info from "active network connections".  I also ran a command in terminal that had some confusing network numbers and tried one of those, lol.

Long story short:

How do i determine my correction ip address, gateway, netmask, and dns numbers to input?

Thanks so much!

---

### Post by lisati on 2012-02-13
For a publicly accessible IP address you need to contact your ISP if you want it to be static.

---

### Post by antiacus on 2012-02-13
> **lisati said:**
> For a publicly accessible IP address you need to contact your ISP if you want it to be static.

OK, so while i'm developing my website, do i still have to do this?  I'm not publishing it for a long time.

Thanks

---

### Post by |{urse on 2012-02-13
-or-

Create a Dyndns account (not free but reasonable)

[http://dyn.com/dns/](http://dyn.com/dns/)

Log into your router and set it up so that your dynamic ip resolves to a domain name.. the location of dyndns (or ddns) settings is different for each router so make sure your router supports it before you set up an account.

DO NOT route through dmz, unless you like insecurity.

gateway, netmask can be found with the ifconfig command

[http://www.whatismyip.com/](http://www.whatismyip.com/) <-- one easy way to check your real ip

this is nowhere near enough information to be a howto but hopefully this helps you a bit.. cool thing is once you install apache2 and set up dyndns (also be sure to forward port 80 via your router of course) you can self-host your page with a really real domain name. Be sure to rock a decent firewall, preferably hardware.

---

### Post by |{urse on 2012-02-13
> **antiacus said:**
> OK, so while i'm developing my website, do i still have to do this?  I'm not publishing it for a long time.

Thanks

Heck no, I just keep my site in whatever folder until I want to install/configure apache then copy the contents to Root/var/www/ when it's time to go live

You can just use any folder you like until you're ready.

---

### Post by efflandt on 2012-02-13
Then of course if you are using a broadband router, you will need to set it to forward TCP port 80 to the LAN IP of your web server.

And any computer you want to access it from your same LAN would likely need an entry in its **hosts** file pointing any servername you use to the LAN IP of the server. Most broadband routers do not do loopback (LAN2LAN via public IP) to avoid IP spoofing.  Testing it from the internet would need to be done from some computer NOT on your LAN (mobile data, dial up ISP, unix shell account elsewhere, etc.)

---

### Post by dcstar on 2012-02-13
> **antiacus said:**
> This is killing me.  I'm needing a static ip for fully qualified domain name to install a webserver platform.
......

Then simply pick a vacant IP address in the internal range you are already using - stop overcomplicating things.

---

### Post by rg4w on 2012-02-13
> **antiacus said:**
> OK, so while i'm developing my website, do i still have to do this?  I'm not publishing it for a long time.
It may be wise to check with your ISP to see if your account type allows serving.  Most ISPs allow serving only from static-IP accounts (which are usually a bit pricier), throttling or even disabling port 80 traffic from shared-IP accounts if they see a high volume of upload traffic.

---

### Post by antiacus on 2012-02-13
Thanks so much for the replies!

I'll look into all of this.

---

### Post by antiacus on 2012-03-24
Just an update.

Comcast does not allow static ip for residential customers.  I've been beating my head over this problem for months to find out that i need to upgrade to business class, then it's an additional $14.95 a month for 1 static ip, or $19.95 for 5.  

For now, since i'm a ways from publishing my website, i'm going to install a virtual box (yet another thing to learn from scratch) and go from there.

While i'm on that topic :), if i wipe my drive clean, install ubuntu, then the virtual box, then another copy of ubuntu within the VB, how much space should i allocate for the 2nd OS?  Can i access files outside of it?  If not, i'll leave minimal space for the 1st OS, so that the OS on the VB can use up most of the drive.

Thanks for any assistance!

---

### Post by jmore9 on 2012-03-24
Comcast also has some hosting capability .  The higher priced the package the more you get , speed, storage , etc.  Might be of interest to you.  Just a thought.

---

### Post by wildmanne39 on 2013-02-06
Old thread closed.

---

