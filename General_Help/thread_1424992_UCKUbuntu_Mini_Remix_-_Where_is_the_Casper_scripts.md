---
title: "UCK/Ubuntu Mini Remix - Where is the Casper scripts can I switch to first console"
date: 2010-03-08
forum: General Help
---

### Post by garysims on 2010-03-08
Hi,

I am making a customized live CD based on the Ubuntu Mini Remix (using UCK). This particular CD will be a console only distro and I am looking for some hints on how to configure Casper so that it can automatically switch to the first console after boot up (rather than the user needing to press ALT + F1).

Many, many thanks,

Gary

Background information from FAQ

Ubuntu Mini Remix is freezing after boot

Question:
The system boots, the splash screen shows the loading state but after that nothing happens...

Answer:
The system is not frozen.
Type "ALT + F1" to move to shell.

Why Ubuntu Mini Remix does not move to shell automatically?
Because Ubuntu Mini Remix doesn't change the way Ubuntu decided to manage the boot process, you'll have the standard Ubuntu behaviour in Ubuntu Mini Remix, it's up to you to modify it.

Also remember that Ubuntu Mini Remix is not meant to be run "as is", you should use Ubuntu Mini Remix as a base to create your own distribution.

---

### Post by ryanrio95 on 2011-11-24
hi. if you got it that far than you'll need this packages.
lightdm, unity-greeter, casper, ubiquity, ubiquity-frontend, xorg-xserver, an desktop environment. kde for example

---

