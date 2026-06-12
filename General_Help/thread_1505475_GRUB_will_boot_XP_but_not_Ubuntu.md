---
title: "GRUB will boot XP but not Ubuntu"
date: 2010-06-09
forum: General Help
---

### Post by Ceiber Boy on 2010-06-09
I Installed ubuntu, and when rebooting grub will boot XP but not the new UBUNTU install, i previously had a hardward problen that has now been resolved. and idears please

thanks

---

### Post by Smart Viking on 2010-06-09
Hi, what happens when you choose ubuntu from grub, what error messages does it give? :)

---

### Post by Ceiber Boy on 2010-06-09
sorry

the curser flashes in the top left hand corner of the screen, then the HDD fininshes data transfer, (as if having reached the login screen) and then the screen goes blanK!

---

### Post by philinux on 2010-06-09
> **Ceiber Boy said:**
> sorry

the curser flashes in the top left hand corner of the screen, then the HDD fininshes data transfer, (as if having reached the login screen) and then the screen goes blanK!

Is this a regular dual boot setup or wubi?

Can you get to the recovery mode from grub? It's the second option down usually.

---

### Post by Ceiber Boy on 2010-06-09
> **philinux said:**
> Is this a regular dual boot setup or wubi?

Can you get to the recovery mode from grub? It's the second option down usually.
its a standard grub install, but haw do you recover grub?

---

### Post by philinux on 2010-06-09
> **Ceiber Boy said:**
> its a standard grub install, but haw do you recover grub?

When you see the grub menu appear press the down arrow key to select the recovery mode.

See in the image. [https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

See how that goes and you'll get to a recovery menu. Then try resume normal boot. Look for any error messages.

---

### Post by WolfRage on 2010-06-09
IMHO For future I would recommend installing Ubuntu on one hard drive and Windoz on another. Everything is much easier that way, and hard drives are very cheap now. 1TB for $150.00 or less.

---

### Post by tommcd on 2010-06-09
Just out of curiosity, what was the "hardware problem" that you resolved?
Also how many hard drives are on your system? If you have more than 1 hard drive, which drive has XP and which drive has Ubuntu? Are these drive(s) IDE or SATA? Also which drive did you install grub to?
Boot from the live CD, open a terminal, and run:
```
sudo fdisk -l
```
and post the output here. This will list your hard drives and the partitions on each drive.
To reinstall grub2 from the live CD, see this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just use the "simple" method outlined there. Don't bother with "Method 2" or "method 3" unless the first procedure fails for some reason.

---

### Post by Ceiber Boy on 2010-06-09
> **WolfRage said:**
> IMHO For future I would recommend installing Ubuntu on one hard drive and Windoz on another. Everything is much easier that way, and hard drives are very cheap now. 1TB for $150.00 or less.
i garee but as menshioned its a works machine and i would have to ask my employer to spend money!

---

### Post by Ceiber Boy on 2010-06-09
> **tommcd said:**
> Just out of curiosity, what was the "hardware problem" that you resolved?
Also how many hard drives are on your system? If you have more than 1 hard drive, which drive has XP and which drive has Ubuntu? Are these drive(s) IDE or SATA? Also which drive did you install grub to?
Boot from the live CD, open a terminal, and run:
```
sudo fdisk -l
```and post the output here.
To reinstall grub2 from the live CD, see this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just use the "simple" method outlined there. Don't bother with "Method 2" or "method 3" unless the first procedure fails for some reason.
the sata data cable was backwards, only one HDD,

---

### Post by tommcd on 2010-06-09
> **Ceiber Boy said:**
> the sata data cable was backwards, only one HDD,
So can you boot from the live CD and run:
```
sudo fdisk -l
```
You can also try reinstalling grub2 to the MBR of the hard drive according to the link I gave in my last post.

---

### Post by Ceiber Boy on 2010-06-10
The Monitor constantly needs manual adjustment every time linux is booted! when it is adjusted it works fine! I don't understand why this is the case so if anyone could offer an idea that would be good

thanks

---

### Post by tommcd on 2010-06-11
> **Ceiber Boy said:**
> The Monitor constantly needs manual adjustment every time linux is booted! when it is adjusted it works fine!

So are you able to boot Ubuntu then ... or what ???
If you are able to boot Ubuntu, try booting to recovery mode and choosing:
**xfix fix video**. Go through that to try to fix the video, and then reboot.
What video card do you have ???

If you are still not able to boot Ubuntu:
Did you try reinstalling grub2 from the live CD as I have suggested???

---

