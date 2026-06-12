---
title: "Update kills Keyboard and mouse"
date: 2010-12-25
forum: General Help
---

### Post by hariks0 on 2010-12-25
I had applied all the updates available on 23rd Morning and Keyboard and mouse stopped working thereafter. The updates amounted to around 130 MBs in size. I can use the keyboard to select other items in Grub menu and it works upto the login prompt. I can change the console to Ctrl+Alt+F1 to F6 before the login screen. No response thereafter. I have set the autoloin after 10 Seconds and the notification asks me for enabling compositing.

Some thread advises me to remove the .gconfd folder of my home. Please advise whether it is safe. Or will applying the later updates through recovery mode console solve the issue?

TIA.

---

### Post by dino99 on 2010-12-25
boot on recovery mode, then select "repair packages", then "continue normal boot"

.gcond, if deleted, is automatically recreated on next boot, so no worry (its only the saved state)

---

### Post by hariks0 on 2010-12-25
> **dino99 said:**
> boot on recovery mode, then select "repair packages", then "continue normal boot"

.gcond, if deleted, is automatically recreated on next boot, so no worry (its only the saved state)

When booted in recovery mode, the screen remains blank without the options like *Repair Packages, Root shell, Resume etc*
BTW, Ctrl+Alt+Del reboots the blank screen.
What to do now? I thought that Reovery mode boot will give me the menu of these above items.

---

### Post by dino99 on 2010-12-25
if you can open a terminal, play either with:

compiz --replace &
metacity --replace &
gnome-panel --replace &

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a (could be long, dont stop it)

---

### Post by hariks0 on 2010-12-25
No. The recovery mode presents a blank screen without any command prompt, menu etc. I am stuck there. However, Ctrl+Alt+Del reboots the PC as usual.

Why the usual menu of recovery mode does not display?

Is it possible to edit grub entries to access the terminal of my user or root?

Can I do something from there ?

---

### Post by hariks0 on 2010-12-25
I tried replacing “ro quiet splash” with "rw init=/bin/bash" in grub menu and gained access to the root shell "root@(none)". Ran these commands and only the last one worked. Yes, it did give a long output but the end result was nothing. When rebooted, I was still where I had started. Keyboard and mouse still does not work.

Please help.

---

### Post by hariks0 on 2010-12-26
The keyboard and mouse freeze just at login screen. So is it related to .gconfd or Gnome? Or can I unistall all the updates I had installed on 23rd December?

At least how can I have the list of installed applications and my customisations in case of a reinstallation?

---

### Post by hariks0 on 2010-12-26
I removed the .gconf and .gconfd from my home by booting from live CD. Still no result. Is there any method to revert to the system state before the updates were installed?

---

### Post by hariks0 on 2010-12-28
Bump :( Should I renstall and start all over again without any clue what I had done earlier?

---

