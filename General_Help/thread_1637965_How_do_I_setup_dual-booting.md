---
title: "How do I setup dual-booting"
date: 2010-12-05
forum: General Help
---

### Post by Wayne1987 on 2010-12-05
I'm in widows xp sp3 right now, I'm just wondering how do I go about, setting up dual booting with out breaking my Windows Xp OS, being last time - I setup Dual booting with the Ubuntu setup disk and that didn't work at all, Xp was broken after that.  Would anybody know of software that does the dual-booting setup from windows with the linux ubuntu iso image?

---

### Post by IndyGunFreak on 2010-12-05
> **Wayne1987 said:**
> I'm in widows xp sp3 right now, I'm just wondering how do I go about, setting up dual booting with out breaking my Windows Xp OS, being last time - I setup Dual booting with the Ubuntu setup disk and that didn't work at all, Xp was broken after that.  Would anybody know of software that does the dual-booting setup from windows with the linux ubuntu iso image?

You can try Wubi, but I'm more leery of Wubi than a "normal" Ubuntu install.  Wubi has been known to cause problems to the Windows OS as well.

What exact problem did you run into when you tried to install Ubuntu previously?  It was most likely user error, than an Ubuntu problem.

---

### Post by Wayne1987 on 2010-12-05
> **IndyGunFreak said:**
> You can try Wubi, but I'm more leery of Wubi than a "normal" Ubuntu install.  Wubi has been known to cause problems to the Windows OS as well.

What exact problem did you run into when you tried to install Ubuntu previously?  It was most likely user error, than an Ubuntu problem.

I couldn't boot into windows anymore.

I had a line that just set there and blinked for hours 

_ <-- Something like that, but nothing ever happened I tried to fix it but, it seemed there wasn't much I could do..

---

### Post by VCoolio on 2010-12-05
Using the live disk is the way to set it up. Just don't touch the partition with windows on it during installation (except for resizing to make space for ubuntu, if you didn't do that yet). Find a decent howto, there are lots of them. Also, what does 'xp was broken' mean? It didn't show up in the grub menu? Or it wouldn't boot?

---

### Post by IndyGunFreak on 2010-12-05
> **VCoolio said:**
> Using the live disk is the way to set it up. Just don't touch the partition with windows on it during installation (except for resizing to make space for ubuntu, if you didn't do that yet). Find a decent howto, there are lots of them. Also, what does 'xp was broken' mean? It didn't show up in the grub menu? Or it wouldn't boot?

Agreed.

---

### Post by psihokiller4 on 2010-12-05
if you're concern you may break windows system

try installing ubuntu inside windows

if you won't be satisfied after that you may just at add remove uninstall ubuntu ;)



but if you wish to install it side by side
install it and grub loader will automaticly have dual boot the setup will automaticly know what to do

---

### Post by Wayne1987 on 2010-12-05
> **VCoolio said:**
> Using the live disk is the way to set it up. Just don't touch the partition with windows on it during installation (except for resizing to make space for ubuntu, if you didn't do that yet). Find a decent howto, there are lots of them. Also, what does 'xp was broken' mean? It didn't show up in the grub menu? Or it wouldn't boot?

Broken, meaning it didn't show up as anything..
but a blinking line..

---

### Post by Wayne1987 on 2010-12-05
> **psihokiller4 said:**
> if you're concern you may break 



but if you wish to install it side by side
install it and grub loader will automaticly have dual boot the setup will automaticly know what to do

Pretty sure thats how I did it last time, but I didn't resize the partition because It looked right..

I have 80GB hard drive tho.

I'm only using 14.8 GBS for Windows.

How could I setup up the Partition?

---

### Post by IndyGunFreak on 2010-12-05
There's an automatic partition tool that's fairly easy to use, but really it should have been pretty clear the first time you installed.

---

### Post by VCoolio on 2010-12-05
> **Wayne1987 said:**
> Broken, meaning it didn't show up as anything..
but a blinking line..
But did you get the grub menu after reboot, where you can choose whether to boot windows or ubuntu? If yes, then check the windows entry in there. Boot ubuntu, check the file /boot/grub/grub.cfg and compare the windows entry with examples you find on the web. Don't edit that file by the way, that's useless; edit /etc/default/grub if needed and apply with 'sudo update-grub'. If you didn't get the grub menu, something went wrong during installation. Depending on what that was, recovering grub may help. Grub howto [here]("https://help.ubuntu.com/community/Grub2").

---

### Post by Wayne1987 on 2010-12-05
> **IndyGunFreak said:**
> There's an automatic partition tool that's fairly easy to use, but really it should have been pretty clear the first time you installed.

What do you mean tools?

---

### Post by IndyGunFreak on 2010-12-05
When you install, and you come to the partition stage, there's an automatic partitioning tool that you can use to partition the drive, and it makes it very simple.  

This has been in place for quite some time, so really, I'm not sure what your problem was, partitioning is not that difficult..

I sent you a PM.

---

### Post by Wayne1987 on 2010-12-05
Okay I'll give it a shot and see it worked if not I'll be back in here with linux

---

### Post by Wayne1987 on 2010-12-05
Okay just installed Linux ubuntu with the Tools in the Linux ubuntu 10.10 install disk with the partition side by side all size correctly, yet windows xp still can't boot.

What can I do now, being I can't use xp now...

---

### Post by Wayne1987 on 2010-12-05
?????

---

### Post by Wayne1987 on 2010-12-05
> **VCoolio said:**
> But did you get the grub menu after reboot, where you can choose whether to boot windows or ubuntu? If yes, then check the windows entry in there. Boot ubuntu, check the file /boot/grub/grub.cfg and compare the windows entry with examples you find on the web. Don't edit that file by the way, that's useless; edit /etc/default/grub if needed and apply with 'sudo update-grub'. If you didn't get the grub menu, something went wrong during installation. Depending on what that was, recovering grub may help. Grub howto [here]("https://help.ubuntu.com/community/Grub2").
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x236c13cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5663    45482996    7  HPFS/NTFS
/dev/sda2            5663        9730    32666625    5  Extended
/dev/sda5            5663        9557    31275008   83  Linux
/dev/sda6            9557        9730     1390592   82  Linux swap / Solaris

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

---

### Post by Wayne1987 on 2010-12-05
Well I guess I'm no longer getting help, that just isn't right at all, I wont be coming back here

---

### Post by IndyGunFreak on 2010-12-05
Obviously something is not correct, because it shows Grub booting, but it's not booting grub for some reason.

---

### Post by wilee-nilee on 2010-12-05
> **Wayne1987 said:**
> Well I guess I'm no longer getting help, that just isn't right at all, I wont be coming back here

Okay first if you expected instant help you should call Microsoft, or the paid Canonical's services, this a forum where nobody gets paid not even the moderators. But you PM'd me for help I will try.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

