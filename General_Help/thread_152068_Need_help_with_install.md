---
title: "Need help with install"
date: 2006-03-29
forum: General Help
---

### Post by pcormack on 2006-03-29
Hi guys,

I have been trying to install the Ubuntu 5.10 CD and DVD medias with no joy at all. The install itself goes fine but when the system starts X the screen goes all messed up with a hard to make out image... from my last install (suse 9.2) the pacman screensaver with KDE is still visible but very distorted and i can see see/ move the cursor around the screen.

I really really really hate windows and have basic experience using linux. The install setup I am trying to do is not duel boot, just ubuntu and i have no trouble partitioning so its not detecting the graphics cards properly or something.

Can I get some advice on what to do in this situation?

Thanks in advance,
Paul.

---

### Post by alamba on 2006-03-29
Let's get this working paul, post your hardware specs. Here's a quick fix that will get you up and running and then we'll get you the right drivers:

1. Boot into recovery model from the grub (think you need to press esc during boot and then get into recovery mode)
2. vi /etc/xorg.conf
3. You'll see a line something like DISPLAY = 'i915' or similar, change this to DISPLAY = 'vesa'
4. save and reboot

This should get X running atleast on a generic driver.

A

---

### Post by pcormack on 2006-03-29
Thanks for the quick response alamba,

My box contains:

-Azus K8V mainboard with AMD Semperion 3100+
-Dell E771p monitor
-1024Mb RAM
-ATI Radeon 128MB 9200
-Creative Labs Live! 24Bit soundcard with 5.1 surround

I am currently in college and will attempt your suggestion when i get home later.

Thanks again,
Paul.

---

### Post by alamba on 2006-03-29
Sure paul. The ATI Radeon might be the issue. By using vesa it'll get you up and running in GUI. You would then want to google for a linux driver for the 9200 model.

A

---

### Post by pcormack on 2006-03-29
ok so I got home and re-installed Ubuntu... 
From the recovery when i go to edit xorg.conf with vim it opens a blank file..
I was posting in the wrong forum! Have the default gnome desktop and the file was

etc/X11/xorg.conf

thanks for your help,
Paul

---

### Post by alamba on 2006-03-30
You're seeing a blank file since you don't have the right file open buddy. If needed step by step get into the directory like below:
1. cd /etc/X11
2. vi xorg.conf

A

PS: Type line 1 exactly. Don't forget the / before etc.

---

