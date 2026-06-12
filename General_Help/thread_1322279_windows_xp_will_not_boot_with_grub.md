---
title: "windows xp will not boot with grub"
date: 2009-11-10
forum: General Help
---

### Post by dustin92 on 2009-11-10
Problem:

I have 2 physical HDD. On the first drive I have Win XP. On the second drive I have ubuntu 9.10. when I start up my computer grub loads but when I click on the windows XP option It moves to a new screen and on the top "GRUB _" shows and then does nothing. but I can boot into linux just fine. what might be wrong and how can I fix this?

by the way, I am very new to using terminal commands so if you could give me detailed instructions I would really appreciate it.

---

### Post by SteveHillier on 2009-11-10
This might not be of much use, but I did once have a machine with one disk with Win XP and Ubuntu installed and a second disk with Vista installed and I could get to all three without problem.  This was with earlier versions of GRUB so maybe it is a GRUB issue, others will have to advise.  It might be useful to post some details of your hardware configuration and if you have any install problems.
Others might then be better placed to help you.

---

### Post by Giblet5 on 2009-11-10
Open a terminal window (Ubuntu...). Enter the following commands by selecting each line separately, hitting Ctrl-C (to copy), clicking in the terminal window, and hitting Shift-Insert: ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

That will recalculate the location of all Windows and Ubuntu partitions, create the boot menu, and write the Master Boot Record to the first physical drive.

Hopefully, that is the boot drive in BIOS, else you'll see more odd behavior than you already are, and this will have accomplished nothing.

You should be able to reboot and select Windows XP from the grub menu, and it should boot.

I have three different Windows installs on this box. They all work perfectly with grub. The menu is getting a bit long...

---

### Post by dustin92 on 2009-11-10
> **Giblet5 said:**
> Open a terminal window (Ubuntu...). Enter the following commands by selecting each line separately, hitting Ctrl-C (to copy), clicking in the terminal window, and hitting Shift-Insert: ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```That will recalculate the location of all Windows and Ubuntu partitions, create the boot menu, and write the Master Boot Record to the first physical drive.

Hopefully, that is the boot drive in BIOS, else you'll see more odd behavior than you already are, and this will have accomplished nothing.

You should be able to reboot and select Windows XP from the grub menu, and it should boot.

I have three different Windows installs on this box. They all work perfectly with grub. The menu is getting a bit long...

I tried that code but know my computer boots right into ubuntu I don't even see the grub menu anymore. It says its loading then says something else right below it but it flashes up too fast and I cant read it. know what? xp is on hd0 and ubuntu is on hd1 if that helps.](*,)

---

### Post by SteveHillier on 2009-11-11
Do you have a BIOS that allows you to select the boot drive?

---

### Post by dustin92 on 2009-11-11
I did the commad above, but know the grub menu does not even show up. I think when I first installed ubuntu I clicked the advanced menu and installed grub on hd0 with win xp. how can I undo that last command and how do I boot into windows. like I said earlier I am very new to this and I don't understand really technical stuff. as long as you tell me what to type in and what you need to know to help me I can figure it out. thank you for your help.

---

