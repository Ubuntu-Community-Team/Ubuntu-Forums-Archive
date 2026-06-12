---
title: "constant freezing?"
date: 2006-06-20
forum: General Help
---

### Post by ObeseOgre on 2006-06-20
I'm new to Ubuntu and just installed it yesterday.  I'm not sure why but Ubuntu constantly freezes, usually within 5-10 minutes.  I can still move my mouse around but eventually it just goes to a black screen.

I searched around here and checked the /var/log/Xorg.0.log file and the only error I found was:

(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.

I don't think that has to do with the freezing.  I also reinstalled ubuntu twice and I'm out of ideas.  Could it have something to do with my ATI Radeon 9550 or its drivers?

---

### Post by Third Thoughts on 2006-06-20
Try removing beagle if you have it installed (I think it comes installed by default, someone correct me if I'm wrong). Do 
```
 sudo apt-get remove beagle 
```
I've found that on my comp having beagle installed and beagle-d running causes the same problem you're describing. Which is a pity becaue beagle is such a nice little app. But its not worth having constant freezes.

~Andrew S.

---

### Post by ObeseOgre on 2006-06-20
Just tried that and it said beagle wasn't installed.

---

### Post by aysiu on 2006-06-20
Well, there are several tricks to diagnosing the problem. Unfortunately, a diagnosis doesn't necessarily lead to a cure.

Try creating a new user (you can always delete the account later). If the new user doesn't experience freezes, something's messed up with your account.

Try using another desktop environment (KDE or XFCE). If you don't experience freezes there, maybe it's a Gnome thing.

Of course, as you've already guessed, it may have something to do with your graphics card not being configured correctly. You may want to eliminate other possibilities first, though.

---

### Post by ObeseOgre on 2006-06-21
I made a new account and same thing happened.  Interestingly after I get the black screen i can cntrl + alt + F2 into like all text mode.  So perhaps this is a graphics card thing.

EDIT: I think it was the ATI drivers, I followed these instructions and so far its been working.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

