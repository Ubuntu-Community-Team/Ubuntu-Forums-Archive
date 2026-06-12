---
title: "No love for the Galaxy Nexus"
date: 2012-03-08
forum: General Help
---

### Post by iamtim on 2012-03-08
I am the proud owner of Verizon's new Ice Cream Sandwich equipped 4G phone. I like it a lot, but it has problems with Ubuntu.

Short version of the story: I need to transfer files from a netbook to the phone for quick transmission to my work. (I'm to cheap to buy a 2nd data plan, and don't want to hassle with rooting and tethering. Been there, not interested in doing it again.)

I need to mount my phone on my netbook. The OMG! Ubuntu instructions and the nyterryder script ([http://bit.ly/zWIJva](http://bit.ly/zWIJva)) don't work on 11.10 on my Dell Mini 9: they both create directories with NO attributes (just ??????) that can't be read, written to or removed. That, in turn, throws a "Transport endpoint not connected" error whenever I try to mount the phone's MTP drive.

Anybody having a similar experience? Got any better ideas how to hook up a Galaxy Nexus and Ubuntu?

---

### Post by oregonbob on 2012-03-13
I have been doing same thing and had same problems. Ubuntu support for MTP is nonexistent. I found a recipe that almost worked on mine so you may have better luck yet, See this blog:
[How To: Fix Samsung Galaxy Nexus MTP File Transfer for Ubuntu GNU/Linux 11.10"]How To: Fix Samsung Galaxy Nexus MTP File Transfer for Ubuntu GNU/Linux 11.10]("http://www.humans-enabled.com/2011/12/how-to-fix-samsung-galaxy-nexus-mtp.html")

It includes getting a MTP library update from sourceforge and it compiles OK, so it might help.

---

