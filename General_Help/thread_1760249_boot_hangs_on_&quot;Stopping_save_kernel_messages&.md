---
title: "boot hangs on &quot;Stopping save kernel messages&quot; or &quot;stopping system v runlevel compatib"
date: 2011-05-16
forum: General Help
---

### Post by hwttdz on 2011-05-16
Boot of a new minimal system hangs on "Stopping save kernel messages" or "stopping system v runlevel compatibility".  I have ubuntu minimal iso x86_64 from usb stick created with unetbootin (don't have a cd drive on the machine in question), and after that I did

sudo aptitude install gnome-terminal network-manager-gnome gdm gedit
sudo reboot

never got a system back.  Annoyingly I can't boot into the recovery mode either, and it seems the keyboard is only semi-responsive (i.e. many dead keys when at the grub menu).  No qualms about reinstalling, but I've done this a few times and ended up at the same place every time.  Any further ideas?

---

### Post by reggler on 2011-07-09
I'm having the exacyly same problem with Kubuntu. Anyone able to help?

Thanks!

---

### Post by hwttdz on 2011-07-11
Unfortunately I had to go back to 10.10.

---

### Post by reggler on 2011-07-11
> **hwttdz said:**
> Unfortunately I had to go back to 10.10.

Not me, I realized that (Kubuntu) I was kissing /etc/init.d/kdm (same as gdm in ubuntu) thus i installed kubuntu-desktop and after some minor tweaks, i was able to boot-up just nicely... running 11.04 smoothly now :)

---

### Post by hwttdz on 2011-07-11
Doesn't that require you to install all the packages from the normal distribution, negating any savings you might have gotten from going minimal?

---

### Post by reggler on 2011-07-11
> **hwttdz said:**
> Doesn't that require you to install all the packages from the normal distribution, negating any savings you might have gotten from going minimal?

Huh, i don't understand the relationship between minimal and normal. I just intended to install normal Kubuntu 11.04 and ended up getting the same error you describe in the original posting...

---

### Post by hwttdz on 2011-07-11
I try not to install a whole bunch I don't need (i.e. the dependencies of *-desktop) which is the difference between the minimal and the desktop versions.  So this problem persists for certain hardware and the minimal install. Glad you got your problem fixed though.

---

### Post by rrgalvao on 2011-11-02
This  thread may help you.
[http://ubuntuforums.org/showthread.php?t=1807612&page=2]("http://ubuntuforums.org/showthread.php?t=1807612&page=2")

---

### Post by hwttdz on 2011-11-03
rrgalvao, thanks for the tip, I actually successfully upgraded to xubuntu 11.10 about a week ago.  And in the process I was wondering why that machine was at 10.10 and not 11.04.  Anyways, I was able to upgrade through 11.04, so perhaps the bug had been fixed in one of the updates.  Hard to say really.  Some questions (like this one) have a shelf life, and if they're not solved during that window they really won't ever be solved.

---

### Post by dc.ricardo on 2011-11-27
See if you have lightdm and lightdm-gtk-theme.
Installing gdm package helps.
Run dpkg-reconfigure gdm.

---

