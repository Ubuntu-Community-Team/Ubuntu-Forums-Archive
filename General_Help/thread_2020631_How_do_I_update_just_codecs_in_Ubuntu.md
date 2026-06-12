---
title: "How do I update just codecs in Ubuntu"
date: 2012-07-08
forum: General Help
---

### Post by jacatone on 2012-07-08
I'm using Ubuntu 10 on an old P4 laptop with a small HDD (30GBs). I'd like to just update the codecs, java, flash. Don't need to update Open Office, language packs, etc. Rather than go through the Update Manager and manually select these things, is there a terminal command that'll do that for me? Thanks.

---

### Post by ajgreeny on 2012-07-08
> **jacatone said:**
> I'm using Ubuntu 10 on an old P4 laptop with a small HDD (30GBs). I'd like to just update the codecs, java, flash. Don't need to update Open Office, language packs, etc. Rather than go through the Update Manager and manually select these things, is there a terminal command that'll do that for me? Thanks.
To start I suggest you use synaptic and just "refresh" the repos with the button top left, then search for the applications you want to update and update them.

However, it is definitely not a good idea to continue using old versions of software as most, will have had security patches since ubuntu 10.4 or 10.10 came along.  Most updating of applications will take very little extra room for the app itself; it is the downloaded package that takes up disk space, but you can delete all those packages with ```
sudo apt-get clean
```, which after a big update could remove hundreds of MB of package files from /var/cache/apt/archives.

---

### Post by Sylslay on 2012-07-08
Clean install with 
[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/) 

Recomended :-), Worth a time :-),

[http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-i386.iso)

---

### Post by jacatone on 2012-07-09
OK, I didn't like the newer versions of Ubuntu with Unity, so I stick with v10. 

That "sudo apt-get clean" didn't do anything after spending a good two hours downloading updates and installing them. I assume they simply replace the older versions of themselves. I see it added a good 7GBs to my HDD. Something I wanted to avoid.

---

### Post by ajgreeny on 2012-07-10
> **jacatone said:**
> OK, I didn't like the newer versions of Ubuntu with Unity, so I stick with v10. 

That "sudo apt-get clean" didn't do anything after spending a good two hours downloading updates and installing them. I assume they simply replace the older versions of themselves. I see it added a good 7GBs to my HDD. Something I wanted to avoid.
7GB of downloaded packages?  That is hard to believe, and the **sudo apt-get clean** command should remove all .deb package files from /var/cache/apt/archives.

You either downloaded and installed an enormous amount and number of applications and upgrades, or something is very wrong with your setup or system.

Run ```
sudo apt-get clean
``` again then run ```
ls -l /var/cache/apt/archives
``` to see if everything has been removed as it should be.

---

