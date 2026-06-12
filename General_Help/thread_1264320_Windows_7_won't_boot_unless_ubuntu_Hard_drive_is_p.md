---
title: "Windows 7 won't boot unless ubuntu Hard drive is pluged in! :("
date: 2009-09-12
forum: General Help
---

### Post by Palid1n on 2009-09-12
Hey !

well i have a 2 hard drives. one with windows 7, the other with ubuntu 9.04. when i try to boot windows 7, with out the ubuntu HD, i get a grub error!!! how in the hell i am i get a grub error when i only have a windows drive in? :( ? it appears as if ubuntu has planted a file in windows so when windows starts it will allow me to chose witch OS to choose from. but unless the ubuntu drive is plugged in it will all way's give me a grub error!!!

so how can i remove the ubuntu files from windows, so i can soulfully boot through windows hd, with out ubuntu drive!!! !!!!!!!!!!!!!!!!!!!!!!!!!!!!! :P

---

### Post by rob-ward on 2009-09-12
The problem will be that you have the grub files located in the /boot of your ubuntu install and without that there is no grub menu to install, your best bet will likely be to use you windows cd and tell it to recreate the MBR on your windows drive, this will get windows loading without the Ubuntu drive, you will then need to either place the grub MBR on your ubuntu drive so when that is plugged in it can still boot ubuntu or create a link in your windows boot loader pointing to the grub boot loader if you leave your windows drive in when using Ubuntu. You will need to decide if you are wanting to only ever have one drive attached or if you may want to have both attached.

You will needto have aread up on how you install and setup grub, I have done it in the past but don't have the article I used bookmarked, if you ask on the forum I am sure there is a grub expert around.

Your only other option if you always leave your windows drive in is to create a small partition on your windows drive where your /boot could be located, you would then have to edit grub so that it uses that partiotion for its boot information(again you need an grub guide or a grub expert) 

Sorry I can't help you more than that but hopefully I have pointed you in the right direction for getting a fix.

---

### Post by louieb on 2009-09-12
Its a shock to find out - last OS installed controls the MBR of the boot drive. Windows - Linux - BSD - whatever - they all do it. 

Guess you want win 7 to take the MBR back. Lots of ways described here [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html").  Take your pick. 

Just wondering is the 2nd hard drive internal or external? And do you still want to be able to boot Ubuntu - if so additional steps will be required.

---

### Post by rob-ward on 2009-09-12
> **louieb said:**
> Its a shock to find out - last OS installed controls the MBR of the boot drive. Windows - Linux - BSD - whatever - they all do it. 


To be fair Ubuntu and most linux distros do have an option to stop it from installing/altering the MBR, but yes it is a problem that a lot of people run into.

---

### Post by Palid1n on 2009-09-12
none of this **** works i am still getting error 21 when loading windows HD alone.!!!!

**** UBUNTU !!!!! :D

---

### Post by rob-ward on 2009-09-12
This seems like a very childish response when people are trying to help you.

Have you tried inserting your windows cd, going into your recovery console and redoing the MBR on you windows drive, that should fix you problem of getting your windows drive to boot without your ubuntu disk, you can then sort you Ubuntu install out later if you choose to.

---

### Post by Palid1n on 2009-09-13
I put the Winows cd in and i used the CMD prompts and tried to use winows start up fixer thing, but unlee the ubutnu Drive is in I Get ERROR 21! :( :confused: so i am kinda stuck with ubuntu! 

Any moe ideas !!!!!!!!!!!!!!!!!!!

---

### Post by rob-ward on 2009-09-13
If you are still getting the Grub error 21 after fixing the windows MBR then something has gone wrong with that process because by replacing the MBR record grub should no longer exist as far as your windows drive is concerned and just boot as it would if you had never installed ubuntu.

You may want to try this again, it is importnant not to have your ubuntu drive in when you do this.

---

### Post by Palid1n on 2009-09-15
alright man thanks for all you have done :D

---

### Post by madscientist032 on 2009-09-17
yes I am having this same problem. I successfully installed ubuntu onto my 4 GiB flashdrive (as an installation, not as a LiveCD) and, like you, Windows XP will not boot (read - error 21) unless the flashdrive with Ubuntu is connected. I've done some major research and the most common solution is to fix the MBR (Master Boot Record) by using the Windows XP/Vista/7 startup CD. Unfortunately the laptop that I have done this to isn't mine and I don't want to chance an accidental deletion of everything I have on the lappy. (Yes I do have a backup but I don't want to use it unless I have to)

So my question is, will reseting the MBR allow me to boot Windows XP without the flashdrive? 

I really want to do this but I don't want to lose my data.

---

### Post by Carl Hamlin on 2009-09-17
> **madscientist032 said:**
> yes I am having this same problem. I successfully installed ubuntu onto my 4 GiB flashdrive (as an installation, not as a LiveCD) and, like you, Windows XP will not boot (read - error 21) unless the flashdrive with Ubuntu is connected.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

As an aside, installing an operating system to a flash drive is a *dandy* way to drastically shorten the life of the drive. Flash can only endure a finite number of write/erase cycles before it does the big firework, and running swap on it burns through those like *crazy*.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAkqyQXoACgkQyLm4ydrABveRTgCgpWWoMPhLNAHqEMKXoZ6GrBMk
FbsAnjruwAe3Icc0N2F7/iW5iE7snACr
=Cmhw
-----END PGP SIGNATURE-----

---

### Post by madscientist032 on 2009-09-17
> *As an aside, installing an operating system to a flash drive is a *dandy* way to drastically shorten the life of the drive. Flash can only endure a finite number of write/erase cycles before it does the big firework, and running swap on it burns through those like *crazy*.*

Nice to know that *that* still effects flash memory. Another reason why I won't use an SSD for my next install. (I don't want a $300 paperweight sitting around.)

(Getting back to the original question) if I reset the MBR back to what it was originally will I erase any data under the Windows partition? I don't want to lose my data. Nor do I want to keep having to plug the flashdrive in whenever I need to bring my lappy out of hibernation.

---

### Post by rob-ward on 2009-09-17
> **madscientist032 said:**
> Nice to know that *that* still effects flash memory. Another reason why I won't use an SSD for my next install. (I don't want a $300 paperweight sitting around.)

(Getting back to the original question) if I reset the MBR back to what it was originally will I erase any data under the Windows partition? I don't want to lose my data. Nor do I want to keep having to plug the flashdrive in whenever I need to bring my lappy out of hibernation.

Yes, it should fix your problem, however you will then no longer be able to boot the USB flash drive. The reason that you are having this trouble it that when you installed Ubuntu on the flash drive you didn't tell it to install the bootloader on the flashdrive so it installed it on the main HDD but pointed to the boot system on the flash disk(hence always needing the flashdrive), next time that you try to do the install you need to go to the advanced options and tell ubuntu to install the bootloader for it's install on the USB device.

---

### Post by madscientist032 on 2009-09-17
> **rob-ward said:**
> The reason that you are having this trouble it that when you installed Ubuntu on the flash drive you didn't tell it to install the bootloader on the flashdrive so it installed it on the main HDD but pointed to the boot system on the flash disk(hence always needing the flashdrive)

So when I power-up the lappy it looks for the bootloader...which is on the flashdrive...ahhhh. Sneaky sneaky Ubuntu.
Next time I'll be more careful. (I'm just glad I didn't install Ubuntu to the main hard drive. That would have sucked.)

---

### Post by gtr32 on 2009-09-17
> **Palid1n said:**
> I put the Winows cd in and i used the CMD prompts and tried to use winows start up fixer thing, but unlee the ubutnu Drive is in I Get ERROR 21! :( :confused: so i am kinda stuck with ubuntu! 

Any moe ideas !!!!!!!!!!!!!!!!!!!

Don't use the windows "fixer", use command prompt:

bootrec /fixmbr

---

### Post by madscientist032 on 2009-09-17
I think what Palid1n was referring to was that he couldn't boot from the CD drive because the BIOS bootloader was looking for GRUB (on the Ubuntu hard drive) and couldn't find it because the Ubuntu HD wasn't connected. 

Basically he's in the same boat as me - If the drive that contains Ubuntu is *not* connected when the computer is powered on, BIOS cannot continue the boot process because it's looking for the GRUB boot manager.

---

### Post by gtr32 on 2009-09-17
Then you need to change your BIOS settings and enable CD-ROM as your first boot device.

---

### Post by madscientist032 on 2009-09-17
> **gtr32 said:**
> Then you need to change your BIOS settings and enable CD-ROM as your first boot device.

I changed the order in my BIOS so that the internal hard disk was first and I get the usual GRUB Error 21 because(in my case) BIOS *needs* GRUB to boot into windows, regardless of the change of order in boot devices. So in order for Windows to boot, the flashdrive with ubuntu installed on it *has* to be connected. The flashdrive **must be connected** in order to boot into windows or linux. Period.

That's the best I can explain it to you.

---

### Post by pricetech on 2009-09-17
Change the BIOS boot order to boot the Optical Drive BEFORE the Hard Drive.

---

### Post by Zoot7 on 2009-09-17
GRUB Error 21 AFAIK means Grub is looking for an installation that doesn't exist.

Can you post the contents your menu.lst file and the output of sudo fdisk -l?

---

### Post by madscientist032 on 2009-09-17
> **pricetech said:**
> Change the BIOS boot order to boot the Optical Drive BEFORE the Hard Drive.
That was the first thing I did with my laptop. That runs fine, with or without the flashdrive connected.

> **Zoot7 said:**
> GRUB Error 21 AFAIK means Grub is looking for an installation that doesn't exist.

Yes it's looking for an installation that doesn't exist when the damn flash drive **isn't connected!** GRUB is both on the internal hard drive **and** on the flash drive. BIOS looks for the bootloader which is on the flashdrive itself. I overwrote the MBR when I installed Ubuntu on the flash drive. So now whenever I turn on my computer (or even when I take it out of Standby or Hibernation) I have to have the flashdrive connected or else I get the GRUB error 21.

---

### Post by RalphSleigh on 2009-09-18
> **madscientist032 said:**
> That was the first thing I did with my laptop. That runs fine, with or without the flashdrive connected.



Yes it's looking for an installation that doesn't exist when the damn flash drive **isn't connected!** GRUB is both on the internal hard drive **and** on the flash drive. BIOS looks for the bootloader which is on the flashdrive itself. I overwrote the MBR when I installed Ubuntu on the flash drive. So now whenever I turn on my computer (or even when I take it out of Standby or Hibernation) I have to have the flashdrive connected or else I get the GRUB error 21.

Madscientist, to get windows booting without the flash drive (assume windows xp):

1)Remove flash drive

2)Enter the BIOS, and set CD-ROM as first boot device and HDD as second.

3)insert windows xp CD, reboot, press enter to boot from CD when prompted

4) When asked, press R to enter recovery console

5) At the recovery console, run fixmbr

6)Run exit, the computer should reboot

7)Don't press enter to boot from CD-ROM, it should then boot windows from your HDD.

This should get your windows booting again, but you will be unable to boot Ubuntu off your flash drive.  Getting Grub running without a permanent linux partition to store its config is somewhat nontrivial.

---

### Post by madscientist032 on 2009-09-18
> **RalphSleigh said:**
> This should get your windows booting again, but you will be unable to boot Ubuntu off your flash drive.  Getting Grub running without a permanent linux partition to store its config is somewhat nontrivial.

Thank you so much! Once I get hold of my XP CD I will have the laptop guys at my school take care of this ASAP. (I'd do it myself but like I said in one of my earlier posts, this laptop isn't mine and I'd rather my Techies fix it for me anyways.)

Once my lappy's back and booting normally I'll simply format the flash drive and use it properly. I won't be experimenting with Ubuntu for a while now. (At least not until I get a netbook) :redface:

I think I've learned a very important lesson here. 

Thank you all so much!! :KS

---

### Post by Zoot7 on 2009-09-18
> **madscientist032 said:**
> Yes it's looking for an installation that doesn't exist when the damn flash drive **isn't connected!** GRUB is both on the internal hard drive **and** on the flash drive. BIOS looks for the bootloader which is on the flashdrive itself. I overwrote the MBR when I installed Ubuntu on the flash drive. So now whenever I turn on my computer (or even when I take it out of Standby or Hibernation) I have to have the flashdrive connected or else I get the GRUB error 21.
Since I haven't seen it suggested to you already, try this.

```
sudo grub
find /boot/grub/stage1
```
That'll return something like:
(hd1,4) -  what it returns for me.
In your case it'll have two entries, hd0 will be in one of them assuming your ubuntu installation isn't on a different hard drive and there'll also be the entry for the flash drive. Then do
```
root (hd0,1)
setup (hd0)
```
That's assuming (hd0,1) ie the first partition on the hard drive connected to SATA0 is where your ubuntu installation is. 

That should re-install GRUB to the MBR and have it point to the right hard drive.

---

### Post by madscientist032 on 2009-09-19
I did that and this what the output was:
```
grub> find /boot/grub/stage1
 (hd1,0)
```

How do I know if this is the flash drive or not?

---

