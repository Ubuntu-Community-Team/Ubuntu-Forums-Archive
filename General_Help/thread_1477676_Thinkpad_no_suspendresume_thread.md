---
title: "Thinkpad no suspend/resume thread"
date: 2010-05-09
forum: General Help
---

### Post by utnubuuser on 2010-05-09
Hi
I've got a Thinkpad X31 with ATI M6 Ly card.
Since Karmic, and Lucid, I get no suspend/hibernate/resume.
If/when I select resume or close the lid, Lucid goes through the suspend cycle, and for approximately half a second it actually seems to go into suspend, then the screen comes back on, black, but definitely on, and absolutely no response to any keyboard input - have to hard-shutdown by holding down the power button.


I'm not expecting a solution here really, just wanted to start a thread for the older ThinkPads because this seems to be an issue since Karmic.

I've read that the problem is with the Ubuntu kernel, and that installing/compiling 2.6.33 fixes the issue, but causes other ones.

If anyone has found any fixes,workarounds, or the magic configuration settings, I'd appreciate reading about them.

---

### Post by utnubuuser on 2010-05-14
**Update**
I've managed to get suspend working by calling > nomodesetas a kernel parameter and switching effects off in System>>Preferences>>Appearance>>Visual Effects>>None

In /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

save
then > sudo update-grub
...bit of a drag considering the great job the team did on the new desktop/visuals, but at least I can suspend/resume.

I'll try some of the older settings for the ATI M6 Ly card and report back...

---

### Post by utnubuuser on 2010-07-31
.

---

### Post by utnubuuser on 2010-07-31
.

---

### Post by utnubuuser on 2010-09-04
I got the nice/necessary effects back by going through gconf-editor and enabling compositing_manager.

Alt+F2>>gconf-editor>>apps>>metacity>>general>>compositing_manager

---

