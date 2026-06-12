---
title: "hi there, help me about ubuntu 10.10 bootloader"
date: 2011-02-03
forum: General Help
---

### Post by cjprofile on 2011-02-03
i have a problem.. i was using windows xp sp3 and i installed ubuntu 10.10,
 seems like i have a problem with grub. its rebooting directly to ubuntu ,how can i boot my windows xp?? where i can choose what i want to boot?

---

### Post by ivanovnegro on 2011-02-03
You posted in the forum feedback not in some support thread. Maybe someone of the staff will correct this.
Can you see Windows in the Grub menu? Normally if you dual boot you can choose between Ubuntu and Windows, if you do nothing it will boot itself to Ubuntu.

---

### Post by s.fox on 2011-02-03
Thread moved to [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")

---

### Post by Rubi1200 on 2011-02-03
> **cjprofile said:**
> i have a problem.. i was using windows xp sp3 and i installed ubuntu 10.10,
 seems like i have a problem with grub. its rebooting directly to ubuntu ,how can i boot my windows xp?? where i can choose what i want to boot?
Hi and welcome to the forums :-)

In Ubuntu, go to Applications > Accessories > Terminal and run these commands please:

```
sudo fdisk -lu

sudo update-grub
```

Post the output here.

Thanks.

---

### Post by cjprofile on 2011-02-04
i dont even know if do have that dual thingy or not..yah im just watching and doing nothing like an idiot waitinf for the boot menu to comeout.. lol.. how can i get that dual thingy??

---

### Post by cjprofile on 2011-02-04
i did that.. but still,, its directly booting to ubuntu..T^T i have lots of important files there, i need to copy or transfer those file here..  and delte some programs

---

### Post by cjprofile on 2011-02-04
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000208f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   384579583   192288768   83  Linux
/dev/sda2       384581630   390721535     3069953    5  Extended
/dev/sda5       384581632   390721535     3069952   82  Linux swap / Solaris
cedric@cedric-ER921AA-ABA-SR1830NX-NA660:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by dollzii on 2011-02-04
Actually, it looks like you deleted windows when installing Ubuntu.

Edit:

If this is what happened, take a look at this thread; 

> [http://ubuntuforums.org/archive/index.php/t-916137.html](http://ubuntuforums.org/archive/index.php/t-916137.html)

---

### Post by cjprofile on 2011-02-04
okay i totally messed up.. what i did before i red ur messge was i installed another ubuntu again.. crap!! whats happening now. how can i uninstall ubuntu?? and ill install it again

---

### Post by 3rdalbum on 2011-02-04
You don't need to "uninstall" before installing again. Just reinstall Ubuntu, but tell it to use the whole hard disk. Unfortunately it looks like this is what you did originally, and have wiped out your hard disk. You should make a backup of all important documents before doing any partitioning operations.

---

### Post by cjprofile on 2011-02-04
so you mean, i deleted all my files in windwos xp and xp as well?? so now i only have ubuntu.. this ubuntu?? well if is that true. its ok for me.. i just need patience to do all my stuff again..

---

### Post by dollzii on 2011-02-05
Well, you could try using testdisk to get some of you're files back but i guess it's not much chance now when you have formatted the system several times. 

I have never tried it but you'll probably find some good guides on google. 

Sorry, don't have msn :lolflag:

---

### Post by cjprofile on 2011-02-05
guys i need your opinion.. "collectivism" lol ... ahmmm do i need to install an antivirus for this, if i need( what anti virus u guys recommended) .. or ubuntu has their own anti virus and i dont need to insatall one..

---

### Post by dollzii on 2011-02-05
No, you do not need to install a antivirus. If you want to learn about ubuntu security check out this amazing thread; 

> [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Thanks bodhi.zazen ):P

---

### Post by cjprofile on 2011-02-05
hey guys..help.i want to install ubuntu in my dell..can i use that installer to my dell mini inspiron 10?? i have a usb hard drive..or better to use usb stick? well what about blackbuntu?? seems awesome can i install that in my dell??? i dont wanna make mistake again .. help..

---

