---
title: "Media Center &amp; light weight server"
date: 2011-09-13
forum: General Help
---

### Post by tomsimmons on 2011-09-13
I'm looking to set up a light weight server:

groupware (I guess? mail/calendar/tasks/contacts/web interface/mobile client/hopefully work with outlook)
printing
samba (windows file share)
CVS/SVN
web server
vpn server (unless a better approach for getting a remote (Windows) machine to access (for CVS/Groupware/Samba) it?)

Sounds a lot, but it's home load stuff not business or worse.

I would also like to use is as a media centre/PVR type set up probably using MythTV.

Has anyone any thoughts/guidance on this?

Which groupware to use, was thinking maybe Zimbra?

I've got an Zotac/nVidia motherboad floating around with about 4GB of memory DVI/HDMI/Wifi/etc and 300+GB drive, think these are likely to be up to the job?

I'm not comfortable enough in Linux to go CLI, and because server wise it's fairly light weight I was thinking just using a desktop install and add the functionality I need.


Tom

---

### Post by tomsimmons on 2011-09-16
No one got any thought on this at all?

A further related question.

I started out on a similar route back in 2009.  Back then everything I found regarding DHCP and DNS was aimed heavily at having the server actually facing and touching the world.  I, with a lot of very good help from the forum got DNSMasq up and running instead.  Would this still be the recommended approach?


Tom

---

### Post by tomsimmons on 2012-02-12
OK, rather surprised that there has been no replies to this at all.

If it was covered else where or in guides I expected comments to the such, but I find it hard to believe that no one has an opinion on any of this.

Tom

---

### Post by sleepyhollows on 2012-02-12
Check out or ask on the Qnap forums. Great forums, lots of smart folk. 

Web interface is fantastic, these babys run on atoms, more than adequate for home and small office. You save a hell of a lot more power than an old desktop pc.

As long as you don't try to install some kind of java bloatware :P

Edit: i.e not zimbra. That thing EATS memory and cpu, even when blank!

---

### Post by tomsimmons on 2012-02-16
> **sleepyhollows said:**
> Check out or ask on the Qnap forums. Great forums, lots of smart folk. 

Web interface is fantastic, these babys run on atoms, more than adequate for home and small office. You save a hell of a lot more power than an old desktop pc.

As long as you don't try to install some kind of java bloatware :P

Edit: i.e not zimbra. That thing EATS memory and cpu, even when blank!

Maybe I'm being daft, but the only qnap I can find is a NAS and similar company?!

Tom

---

### Post by Paqman on 2012-02-16
> **tomsimmons said:**
> Maybe I'm being daft, but the only qnap I can find is a NAS and similar company?!

Tom

They are, but they can also serve web pages, print, etc, etc. Useful machines, but probably not exactly what you're after.

I think you'll get more responses if you make your questions a bit more specific. Was there anything in particular that you wanted advice on? I'd be inclined to start with a relatively simple subset of tasks (eg: printing/Samba/apache) that you know you can do and add the other stuff once you've got that set up and installed. Then you can ask specific questions as you hit the individual speed bumps.

---

### Post by tomsimmons on 2012-02-16
Well I guess it comes down to two points to start off with.

1.
Can I do these kind of things with a desktop install or do I need server?  I don't want to bury the machine under a ton of stuff that I'll never need.  At the end of the day this is only  a home network.

2.
What do people recommend in the way of groupware or similar?  Zimbra seems to get negative press on memory and CPU usage, also you need to purchase a connector for Outlook, and not sure if it handles push mail without an addon.

From what I have read, it seems Zimbra can be a pain to get running if you don't install it on the version of Ubuntu it was released for.  That would mean I'd have to go with 10.?? and I guess server.


Tom

---

### Post by Paqman on 2012-02-16
Can't help with Zimbra, but:

> **tomsimmons said:**
> 
Can I do these kind of things with a desktop install or do I need server?  I don't want to bury the machine under a ton of stuff that I'll never need.  At the end of the day this is only  a home network.


The only real difference between the server and desktop editions are the default packages that are installed. You could turn the desktop edition into the server edition by installing and removing packages, and vice versa.

So it's up to you. Normally you'd use the server edition for this if it was going to be a headless box serving up files and media. There's not really any point in having all the extra packages for desktop installed if you aren't using them, plus the server edition comes with a few extra tools like aptitude that can make administering it through a terminal a bit more pleasant.

---

### Post by tomsimmons on 2012-02-16
> **Paqman said:**
> Can't help with Zimbra, but:



The only real difference between the server and desktop editions are the default packages that are installed. You could turn the desktop edition into the server edition by installing and removing packages, and vice versa.

So it's up to you. Normally you'd use the server edition for this if it was going to be a headless box serving up files and media. There's not really any point in having all the extra packages for desktop installed if you aren't using them, plus the server edition comes with a few extra tools like aptitude that can make administering it through a terminal a bit more pleasant.

OK, I'm more at home round a GUI than CLI, so you'd recommend Server install and add X?


Tom

---

### Post by stefangr1 on 2012-02-16
It's certainly possible to use your system this way, and obviously everyone on these forums will agree that it's fun to run your own Ubuntu server, but I'm not sure whether it's the most practical solution for the purposes you mention.

In any case I would advise you to split up the Media playing part and the server part (well, that's how I had it before I replaced my Ubuntu server with a Synology NAS).

You can pick up a network attached media player (I have the Asus O'Play and am very happy with it) for $70. This will give you the advantage of a user interface and a remote control. Furthermore, it enables you to put the server part outside of the living room. A system doesn't need to make a lot of noise, but you'll always here the disks spinning. Running a 24/7 server next to your bed or TV means there's always some noise.

The server functions you mention will require a lot of configuration, but it's all possible to do. You do need to work with the command line, however. My estimate is that if you would have moderate command line experience, one weekend of configuration, testing and tweaking should be sufficient. The reason to go for this solution is, however, that you enjoy spending time on building and configuring your own Ubuntu setup. It's neither the most feasible solution, nor the most cost-effective (probably not even when you already have the IO-board). My Synology NAS (but I think on a QNAP NAS this can be done as well) can do the things you mention, and everything can be configured to a relatively user friendly interface.

---

### Post by tomsimmons on 2012-02-16
I have to confess that I am thinking of ditching the media centre side of things.

I'm pondering using a Beagleboard or possibly even a Rasberry Pi as a media unit on the back of the TV and it would just use the storage from this server.

The leaves this machine really hosting the groupware, FTP, web server, VPN, and file store.

The groupware or similar is my biggest question I guess.


Tom

---

### Post by Paqman on 2012-02-16
> **tomsimmons said:**
> OK, I'm more at home round a GUI than CLI, so you'd recommend Server install and add X?


Once you've added X and a DE you've pretty much got the desktop version anyway.

I would advise learning to use the command line, you'll need it for fiddling with server packages. If you want to use something like Gedit for editing files instead of nano or (shudder) vim, you can just connect to the box through something like SSH or NFS and use Gedit on your local machine. There's not much point in installing a GUI on the actual server if you've got a machine running a desktop already.

> **stefangr1 said:**
> Furthermore, it enables you to put the server part outside of the living room.

I was assuming he meant a MythTV backend.

---

### Post by Khayyam on 2012-02-16
> **tomsimmons said:**
> I have to confess that I am thinking of ditching the media centre side of things.

Tom .. as I see it your needs are pretty modest, they would/could all run on the same machine **but** there are one or two reasons they should probably be seperated.

Firstly, running a groupware on an intranet is fine if your a business and your main useage is 9-5 with perhaps some roaming users connecting via VPN. However, this kind of setup will (and I would say should) be gateway'ed, users have to VPN to access intranet services (Groupware, mail, etc) from outside. The intranet should be isolated as much as possible from abuse, the gateway/firewall standing guardian. So, this is really a two machine, minumum, setup.  

A groupware without roaming access is next to useless, if it can't be accessed from anywhere then clients will have to use other services when not on the intranet. I know from experience having worked within a large institution whos intranet was inaccessable from outside their subnet, what happens is that people eventually give up using the groupware for less schizophrenic options.

There are also good reasons for seperating other services from the 'gateway' if there is need to connect to those services without a VPN. SMTP, and perhaps FTP, come to mind.

Also if you plan on setting up a mailserver be sure to spend some time understanding how its configured, I've seen many a home network become inoperable because either it was an 'open relay' (and was then blacklisted) or didn't have an MX (mail) record configured, and when a mail delivery went wrong on a remote host they wern't able to send status messges and mail server gets blocked. Mail is one of those things that people make the most mistakes with, so its best to be somewhat careful with it.

> **tomsimmons said:**
> The leaves this machine really hosting the groupware, FTP, web server, VPN, and file store.

You should also think about what really needs to be accessed outside of the intranet. FTP traffic can be forwarded from the gateway, but you could also have users VPN and use fileservices (Samba/NFS/AppleTalk/etc). In this way all the gateway does it stand guardian, and services are accessed once the VPN is in effect. 

> **tomsimmons said:**
> The groupware or similar is my biggest question I guess.

I think I should only give you a very tentative answer on this, there are just too many factors that play into CMS/Groupware selection. So, you really need to hit [free(code)]("http://freecode.com") and take a good look at those **still in development**. I've used [Horde]("http://www.horde.org/apps/groupware") and [Simple Groupware]("http://www.simple-groupware.de/cms/") both of which seem to have everything you want, but again, you should look for youself, you may prefer something python, or perl based ... needs are often based on factors that are hard to gauge. I was once recommended Zope/Plone, set it up to authenticate with LDAP (not completely supported at the time), tryed to use it, wasted a whole week, removed it completely and ended up using Typo2 to complete the project. It turned out the person recommending it had **never** used it but "heard it was good".I know some people (actually the people who develop [Silva]("http://infrae.com/products/silva/")) (which is Zope based) who love it. Go figure.

HTH ...

---

