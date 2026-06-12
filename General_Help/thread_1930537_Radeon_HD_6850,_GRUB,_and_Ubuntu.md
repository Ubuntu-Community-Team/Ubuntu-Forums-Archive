---
title: "Radeon HD 6850, GRUB, and Ubuntu"
date: 2012-02-23
forum: General Help
---

### Post by alphaamanitin on 2012-02-23
So,

I am still having graphical errors.  I followed the amazing guide by an ubuntu team member.  I think the fact that my computer is EFI is complicating things.  I cannot get grub to appear, no matter what I do, but the computer does boot into ubuntu, though with graphical errors that render it worthless.  Using the nomodeset option for GRUB I can boot into the live kubuntu11.10/12.04, and the live 12.04 ubuntu (oddly though not 11.10 ubuntu), but I cannot get the grub menu on my install to add the nomodeset option.  

I tried booting into a liveCD 12.04 LTS, mounted my install (I couldn't mount whole drive, just the partition with home directory), chroot, modify etc/default/grub to have the nomodeset, but can't update the grub.cfg menu.  I assume this is because I cannot mount the whole drive.  Any advice?

AlphaA

---

### Post by idoitprone on 2012-02-24
When you edited /etc/default/grub, you edited the live cd's grub. You have to mount the root partition and edit it's /etc/default grub to make it pernament.
And enter ```
sudo update-grub 
``` while chroot

If you just want to remove nomodeset or add it temperally
Go to the grub menu

Highlight the enty you want to change
press e to edit it
arrow key to the paramets which is at the end of the line that starts with kernel
Modify way you want
press b to boot when done

---

### Post by alphaamanitin on 2012-02-24
I guess you didn't read my post.  I DID mount the root file system and chroot into it to edit the grub.  As I said though, for some reason it would not let me mount the entire dev (/dev/sdb) only the partition containing / directory.  After ediing that file, it wouldn't let me do anything. 

Unless you are saying that because it wouldn't let me mount the /dev/sdb that it caused me to edit the wrong file.

AlphaA

---

### Post by idoitprone on 2012-02-24
```
I couldn't mount whole drive, just the partition with home directory
```Please clearify. I did read you post. People can have seperate /home partition and you said you only mounted that partition. You led me to believe that you are editing the live cd's /etc/default/grub


You should be able to edit the mounted partition

```
mount /dev/sda3 /mnt/gentoo
livecd ~ # cd /mnt/gentoo
livecd usr # cd /
 livecd / # mount -t proc proc /mnt/gentoo/proc
 livecd / # mount --rbind /dev /mnt/gentoo/dev
 livecd / # cp -L /etc/resolv.conf /mnt/gentoo/etc/
 livecd / # chroot /mnt/gentoo /bin/bash
 livecd / # env-update && source /etc/profile
```Are you sure you did all those steps NOTE: i took it from the gentoo installation guide
then you probably forgot to
type
```
sudo update-grub
```that is the time when the changes are move to grub.cfg

[http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml)
[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

### Post by dcstar on 2012-02-24
> **alphaamanitin said:**
> So,

I am still having graphical errors.  I followed the amazing guide by an ubuntu team member.  I think the fact that my computer is EFI is complicating things.  I cannot get grub to appear, no matter what I do, **but the computer does boot into ubuntu**, though with graphical errors that render it worthless.  Using the nomodeset option for GRUB I can boot into the live kubuntu11.10/12.04, and the live 12.04 ubuntu (oddly though not 11.10 ubuntu), but I cannot get the grub menu on my install to add the nomodeset option.  

I tried booting into a liveCD 12.04 LTS, mounted my install (I couldn't mount whole drive, just the partition with home directory), chroot, modify etc/default/grub to have the nomodeset, but can't update the grub.cfg menu.  I assume this is because I cannot mount the whole drive.  Any advice?

AlphaA

Just boot up Ubuntu, edit the grub.cfg file (using sudo) and then do:

```
sudo update-grub
```

There is no need whatsoever to use a Live CD to do any of this.

---

### Post by alphaamanitin on 2012-02-24
> **dcstar said:**
> Just boot up Ubuntu, edit the grub.cfg file (using sudo) and then do:

```
sudo update-grub
```There is no need whatsoever to use a Live CD to do any of this.
I guess you expect me to memorize every keystroke needed to log in, open the terminal, change directory to the file, edit the file, save it, leave and reboot.  Or did you not notice the part about graphical errors rendering the desktop GUI worthless?

@idiotprone, I can see how my first post was confusing.  Thanks for the help.

AlphaA

---

### Post by dcstar on 2012-02-24
> **alphaamanitin said:**
> I guess you expect me to memorize every keystroke needed to log in, open the terminal, change directory to the file, edit the file, save it, leave and reboot.  Or did you not notice the part about graphical errors rendering the desktop GUI worthless?

Log into the ALT-F1 terminal, then:
```
cd /etc/default
sudo nano grub
```
Make your changes, save the file and then:
```

sudo update-grub
sudo init 6
```

Personally I use BURG, it seems far more usable than plain old GRUB.

BTW, I just installed a RADEON 5450 card and had to change the BIOS settings (using my old inbuilt video) to set the card as the Primary video device to get it to show the BIOS & boot menu.

---

### Post by alphaamanitin on 2012-02-25
I have tried every possible keyboard short cut, ALT-F1 included, those cause the screen to go completely black.  When I say worthless I mean worthless.  I can, however, see my mouse at the very top of my screen when I move it around, but only partially.  I do not use BIOS, I use UEFI.

Id

---

### Post by dcstar on 2012-02-26
> **alphaamanitin said:**
> I have tried every possible keyboard short cut, ALT-F1 included, those cause the screen to go completely black.  When I say worthless I mean worthless.  I can, however, see my mouse at the very top of my screen when I move it around, but only partially.  I do not use BIOS, I use UEFI.

Id

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

