---
title: "I cannot install Kubuntu 11.04"
date: 2011-08-21
forum: General Help
---

### Post by deckoff on 2011-08-21
I have an desktop OEM machine which runs Win7 ultimate. I tried to install Kubuntu 11.04, the installation reports it was successful, but after a reboot, the PC does not show the grub menu, but windows start automatically??? 
I tried manual mode, and the guided one... Mind it, I use only Kubuntu on my laptop and have experience how to make it run. So this is a surprise for me. Any ideas what is happening. The guided method will not allow me to install on the physical drive, where the Win7 install is. All drives are NTFS, a let Kubuntu prepare them. I tried manually formatting to ext4 and installing, too

---

### Post by dino99 on 2011-08-21
have very bad experience too with recent kubuntu, so i've moved to gnome which is more friendly and better supported

---

### Post by deckoff on 2011-08-21
An usb image from the very same CD image installed Kubuntu without a problem. I will try with Ubuntu, though...

---

### Post by deckoff on 2011-08-23
It seems the problem was an old Photoshop installation. I tried to re-install grub and got the followin error message:
> /usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
I followed this link here to get rid of this [http://computers-linux-other-nonsense.blogspot.com/2011/03/flexnet-sector-32.html]("http://computers-linux-other-nonsense.blogspot.com/2011/03/flexnet-sector-32.html")
And then I run boot-repair (described in Ubuntu section about grub and this did the trick.
To sum it up - ubuntu was installed , but grub was screwed.
Hop this help someone.

---

### Post by YannBuntu on 2011-08-23
Hello Deckoff,
I am happy to see that Boot-Repair helped you. This tool is new, so if you have 5 minutes, please could you help translating it in Bulgarian? ( [https://translations.launchpad.net/boot-repair/trunk/+pots/cleancommon-translations/bg/+translate](https://translations.launchpad.net/boot-repair/trunk/+pots/cleancommon-translations/bg/+translate) )

regards

---

