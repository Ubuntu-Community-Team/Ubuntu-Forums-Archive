---
title: "Installed Ubuntu... now Windows XP not loading"
date: 2010-09-21
forum: General Help
---

### Post by ptychoptera on 2010-09-21
Hello

I just installed Ubuntu 10.04 on a partition so I could dual boot it with Windows XP. Ubuntu is working great, but I can no longer get windows to load. When I restart my computer it takes me to a screen that allows me to choose between the two, and when I choose Windows the screen goes black (except for a blinking white line in the top left) and the hard drive does nothing (as indicated by the little LED light not blinking). All of the Windows files are still on my computer, as I can access them just fine in Ubuntu. 

How do I fix this? Heeeeeeeeeeeeeeeeelp!

---

### Post by SmokeyThePanda on 2010-09-21
If you still have your windows XP disc, you can boot into the recovery console using it and there's a command you can run that will repair the partition, I forget exactly what it is though..:S Perhaps another poster will know, or you can find it on google. I had a similar problem with my father's XP installation, I torrented a copy of XP, burned it and repaired the partition :p

---

### Post by ptychoptera on 2010-09-21
> **SmokeyThePanda said:**
> If you still have your windows XP disc, you can boot into the recovery console using it and there's a command you can run that will repair the partition, I forget exactly what it is though..:S Perhaps another poster will know, or you can find it on google. I had a similar problem with my father's XP installation, I torrented a copy of XP, burned it and repaired the partition :p

I don't have a Windows CD. When I get to the list that lets me choose between Ubuntu/Windows there is also an option for a Windows recovery mode... but I don't want to do anything that will cause me to lose my files in windows. I don't have a backup for all my music on there.

---

### Post by VanillaMozilla on 2010-09-22
> I don't want to do anything that will cause me to lose my files in windows. I don't have a backup for all my music on there.
> All of the Windows files are still on my computer, as I can access them just fine in Ubuntu.
You just answered your own question.  Make a backup from Ubuntu.  That solves half the problem.

Sorry, I don't really know what the problem is with your Windows, though.  Booting used to be controlled by /boot/grub/menu.lst, but you may have the new version of grub, which doesn't use that configuration file.  Check the grub documentation.  Other than that possibility, I have no idea.  Sorry.

---

### Post by Infamous Wake on 2010-09-22
Try using EasyBCD to repair your boot sequence or any corrupt boot files. If your music can be accessed through ubuntu then why not back it up through that, along with anything else and wipe XP and reinstall.

---

### Post by amsterdamharu on 2010-09-22
If you have installed the newer Ubuntu then it probably uses grub2 to boot. In ubuntu try to run the following command:

```
sudo update-grub2
```  

Then reboot.

There is a bootscript somewhere but I am in a hurry to go out now. Later I'll post it so you can run it and post the output. That might help us fix your problem if update-grub2 didn't help.

---

### Post by VanillaMozilla on 2010-09-22
Here is too much information:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

