---
title: "HP Deskjet D2660 and Ubuntu 10.04...  :("
date: 2011-07-20
forum: General Help
---

### Post by t0p on 2011-07-20
Here we go again...

I got a HP Deskjet D2660 because it was apparently compatible with Linux.  This was back when I was running 8.04.  But it *didn't* work, and I  eventually had to work around it by installing a virtual XP in VirtualBox and using the printer through that.

Well, now I'm using 10.04, and yet again the printer won't work with it.  I've got the latest hplip installed:

```

t0p@phobos:~$ sudo apt-get install hplip
[sudo] password for t0p: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

So why oh why do I *still* have to go through the VBox/XP palaver?  The D2660 shows up under **System > Administrating > Printing**, but when I try to print an image it doesn't even appear in the "print queue"!  Why?  *Why??*  I figured Hewlett Packard with its hplip project would be the best bet to go with... but it doesn't seem to be that way.  Unless, of course, I'm being  an utter doofus and missing something that's right under my schnozzle...

Any suggestions?  Cheers...

---

