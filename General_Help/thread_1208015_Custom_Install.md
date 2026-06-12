---
title: "Custom Install"
date: 2009-07-08
forum: General Help
---

### Post by PigeonMedia on 2009-07-08
Hey guys, pretty new to the forums so I'm not exactly sure where to put this question.

I'm looking for a direction pointer on how to make a custom install of Ubuntu.  I want to be able to tell the installer which apps to install and which ones not to so I don't have to configure after or during.

How you can help.

THnks

---

### Post by wojox on 2009-07-08
You could check this site out

[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

### Post by Jebtrix on 2009-07-08
Use Remastersys, its easy. Just install Ubuntu, tweak it up, remastersys will make a livecd including your user profile n all.


[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by Jebtrix on 2009-07-08
Just another tip I thought of, before using remastersys, I would use Bleach Bit (as Root) to lean out the .iso size. The biggest chunk is cleared up in removing System > Localizations. Usually saves 100Mb+. Now if you need other languages, then neva-mind. :wink:

sudo apt-get install bleachbit

---

### Post by RedSquirrel on 2009-07-08
Install the base system using the Minimal CD, reboot, and then add the applications you want. That's the easiest way to do a custom install. For example:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by PigeonMedia on 2009-07-24
Thanks for the help guys.

---

