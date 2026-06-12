---
title: "Help! Ubuntu won't boot past the splash screen!"
date: 2010-08-25
forum: General Help
---

### Post by articanos on 2010-08-25
I have a asus g50v running lucid 10.04. Everything was working except my headphones, thus I followed the steps on [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) to upgrade my alsa since the help for it on [http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v) did not work. After rebooting ubuntu got to my splash screen and took a crap, I can't get it to do anything at all, I can't even hit ctr alt f3 or alt 2 to make it tell me what it is doing. Any help would be appriciated.

---

### Post by articanos on 2010-08-25
Ok, by holding shift I was able to get to recovery mode, but after I tried repairing the packages, but it refuses to resume normal boot, something with alsa really screwed up, how can I remove it to boot the system again?

---

### Post by articanos on 2010-08-25
Wonderful, I tried to re-install the base drivers via [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and now I can't even get recovery mode to work. I'm really starting to hate 10.04, seems like it's nothing but trouble and was nowhere near stable enough for release.

---

### Post by lidex on 2010-08-25
Have you tried booting into an older kernel?

---

### Post by articanos on 2010-08-26
I finally got into an older kernel's recovery mode, and was able to restore the default alsa that locked everything up, was up till 2am trying to get it back to rights. Still can't get the damn headphone jack to work tho.... little things like that drive me mad.

---

### Post by lidex on 2010-08-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

