---
title: "Login window problems"
date: 2011-12-16
forum: General Help
---

### Post by cosners on 2011-12-16
Hey everyone, sorry to bother you with this trivial problem but I would appreciate it if you helped me fix it. Whenever I try to change around my login settings to disable login sound, or change the background/icon on the login, it doesn't do anything. I'm using 10.04 by the way (am patiently waiting for the next LTS release).
Is there a way to fix it or manually configure my login screen?

---

### Post by Mark Phelps on 2011-12-16
Don't know how you're doing it, but I believe that startup-manager worked well with Ubuntu 10.x.

---

### Post by cosners on 2011-12-16
Hmm, I tried installing and running that and it told me:
Usplash not detected
Splashy not detected

I'm not exactly sure what to do with it, I checked the option that said "show boot splash" but the login is still the default purplish color. Then I tried apt-get install splashy as superuser to see if that would fix it and I received this mesage. 

[B]Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]
When I try to install usplash it says I have some unmet dependencies.

[B]Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme[/B]
**E: Broken packages**

Not sure how to proceed from here. If it's relevant, the way I tried to change the default login was by using the login screen options in the control center to turn off the sound it plays, and by using Ubuntu Tweak (a version for 10.x) to give it a nicer looking background. It hasn't changed at all though.

---

