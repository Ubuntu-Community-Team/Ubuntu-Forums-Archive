---
title: "Can't boot Kubuntu from USB drive"
date: 2011-04-09
forum: General Help
---

### Post by Superpelican12 on 2011-04-09
Hello everyone,

I'm trying to boot Kubuntu 10.10 from my USB drive. I checked the BIOS, so it will boot from "removable drive" first. But it still boots my Xubuntu installation from the harddrive. I tried it on 2 different computers, but both had Xubuntu 10.10 on it. They both boot Xubuntu. And when I tried to boot Kubuntu on a Windows Vista laptop, without Xubuntu, it just boots!

I'm sure the BIOS is configured right. Does anyone know what' s going on?

Thanks,

Superpelican :|

---

### Post by f1tz on 2011-04-09
It might be that you're not attempting to boot from it in the first place. Usually, you can hold down F12 when booting to display a list of available devices from which to boot. Try that? It usually takes a fair while to boot from a USB stick.

---

### Post by linuxuser12345 on 2011-04-09
Are you sure that Kubuntu is installed correctly on the USB drive? Did you place it on the USB drive with the Startup Disk Creator or UNetbootin, or did you simply copy and paste the .iso file onto the USB drive?

---

### Post by Superpelican12 on 2011-04-09
I really configured the BIOS with F12 (F2 or F8 on some computers), I tried the same USB drive on a Win Vista laptop and it worked perfect. I even let Kubuntu check the USB drive for bugs on the Vista laptop: nothing found. 

And yes I made the USB startup disk with Xubuntu' s built in Startup Disk Creator. The .iso I used was from Kubuntu 10.10, downloaded from the official Kubuntu.org website.

---

### Post by linuxuser12345 on 2011-04-09
> **f1tz said:**
> It might be that you're not attempting to boot from it in the first place. Usually, you can hold down F12 when booting to display a list of available devices from which to boot. Try that? It usually takes a fair while to boot from a USB stick.
  What he means is that there is a specific button you can press at the time of start-up that doesn't bring you to BIOS, but rather simply shows a small list of places you can boot from. This is the easier and faster way than rather going through BIOS.

---

### Post by linuxuser12345 on 2011-04-09
Was the Live USB plugged in the time you set your BIOS? That may be the problem, and all you do is go to BIOS (when the USB is plugged in), go to where you select your hard drives, and then set up the USB drive to a higher priority than the SATA/ATA Hard Drive you are currently using.

---

### Post by Superpelican12 on 2011-04-09
Yes, that' s what I did with the Vista laptop! But so far I now my 2 other computers don't have it, I going to check it out. 

Thanks :P

---

### Post by linuxuser12345 on 2011-04-09
> **Superpelican12 said:**
> Yes, that' s what I did with the Vista laptop! But so far I now my 2 other computers don't have it, I going to check it out. 

Thanks :P
Wait, so is your problem solved?

---

### Post by Superpelican12 on 2011-04-09
I'm posting this reply on my Asus Eee PC netbook, in Kubuntu booted from my USB drive ;). The option "f1tz" meaned didn't have a seperate menu, it was in the BIOS itself. It is named "Boot Sequency" or something. Very strange as I looked in Boot Priority the first time. I'm angy on Asus for there very bad BIOS!

Thanks everyone,

Superpelican ;)

---

### Post by linuxuser12345 on 2011-04-09
Next time, the second your EeePC starts up and the EeePC screen shows up, click "Tab", and the second the black screen with the white text pops up, click "Esc". This brings you directly to the boot-up menu. 

Trust me, I use an EeePC myself, too! ;)

---

### Post by f1tz on 2011-04-09
Glad its working. Mark the thread as solved?

---

### Post by linuxuser12345 on 2011-04-09
> **f1tz said:**
> Glad its working. Mark the thread as solved?
Let me answer that for you: YES!!!

---
Another *EPIC SUCESS* story! ;)

---

### Post by drshahab on 2011-06-16
I have a PC with Asus P5G41T-MLX motherboard, the boot menu has 'removable drive' option but no 'boot from USB' entry, when I try to boot with a working Ubuntu live USB with 'removable drive' option it fails to boot.Is there any work around?

---

### Post by drshahab on 2011-06-18
> **drshahab said:**
> I have a PC with Asus P5G41T-MLX motherboard, the boot menu has 'removable drive' option but no 'boot from USB' entry, when I try to boot with a working Ubuntu live USB with 'removable drive' option it fails to boot.Is there any work around?
I have found a work around that I would like to share.
You have to create a 'PLoP Boot Manager CD' as explained at

[http://www.pendrivelinux.com/boot-](http://www.pendrivelinux.com/boot-) [...] a-plop-cd/

It works!

---

