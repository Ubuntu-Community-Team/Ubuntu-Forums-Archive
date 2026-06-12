---
title: "Dell Mini 1010 boots to balck screen"
date: 2010-10-15
forum: General Help
---

### Post by blur xc on 2010-10-15
I've got a dell mini 1010, that after doing upgrades boots to a black screen.  It's running the infamous gma500 vid chip...

Before upgrading, I did like the instructions stated, and purged the psb-kernel-source package, upgraded, and then reinstalled all of those poulsbo packages.  After that, I rebooted, and was met w/ the black screen.  Nothing works, not even ctrl-alt-f1.

Since then, I figured out how to boot to a root prompt, which I can do just fine, and purged the psb-kernel-source again, replaced the configured xorg.conf with the failsafe xorg.conf, but still, boots to a black screen.  The last time this happened, I ended up doing a new clean install.  I really don't want to do that again.  It's such a pain.

Also, I can't seem to get a wifi connection from the root prompt to be able to install any new packages.  I don't recall the error messages, but I entered the commands like the instructions I found on-line stated, but it just won't connect.

thanks,
BM

---

### Post by blur xc on 2010-10-18
bump

I figure if I can get to a command prompt, there has got to be some way to fix this computer w/o resorting to a clean install.

....

thanks,
BM

---

### Post by blur xc on 2010-10-19
bump

thanks,
BM

---

### Post by Rubi1200 on 2010-10-19
I don't know if this will help, but look here:
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by blur xc on 2010-10-20
I managed to fix it last night!

Man, that took forever to figure out, and it was so stupid simple.  Apparently, purging psb-kernel-source isn't good enough.  I should have done a apt-get autoremove after, because there were some packages that stuck around and messed everything up.

Then I ran updates again, and reinstalled the poulsbo drivers and all is well again.

BM

---

