---
title: "Removing GRUB so I can try and install Windows"
date: 2011-04-14
forum: General Help
---

### Post by Totergott on 2011-04-14
I'm giving my laptop to my mom, but she doesn't know anything about Ubuntu, so I thought I'd just install Windows 7 for her since she knows Windows 7 from her work.  Well, I thought I could just put in the disc and install like normal, but it wouldn't but and instead that there was an error and couldn't recognize the file system and followed by Grub Rescue>

So I searched all over trying to figure out how to remove GRUB, and I found ms-sys.  Once I installed, I used it and it said I successfully set it MBR7 for Windows 7, but when I put in my Windows 7 disc, it wouldn't boot the CD. Yes, I set the BIOS to boot from CD/DVD-ROM.  I also tried MBRVista and just mbr for 2000/XP.

So I tried this program Super Grub.  I tried 3 different ways to setting mbr, but each time I failed.  I tried the basic tutorial provided by Super Grub Disk, I tried WIN => MBR & !WIN!, and I also tried !WIN!.  But now when I put in my Windows 7 disc or even any other disc for windows (XP, Server 2008, Server 2003, Windows 7) it gave me "No bootable device -- insert boot disk and press any key", but when I put in my Ubuntu 9.04 disc, it boots normal.

So I redid Super Grub after replacing the cd/dvd-rom with one of my other laptops and tried all 3 again and still same problem.

My laptop is an HP G56.

---

### Post by seawolf167 on 2011-04-14
When setting up Windows, select to delete all partitions on the hard drive, then repartition with your sizes of choice (in NTFS) and Windows will automatically install it's bootloader

---

### Post by wilee-nilee on 2011-04-14
Like the key prompt for going to the bios to change the boot from=what media is read first, there is another boot from choice menu outside the bios. With my computer it is the f12 key, I think the HP is f9, peck around with all the f keys at start up including the delete, esc...etc, I think that is what you need to do. Booting from a cd with just changing the bios fails at times, not sure why.

---

### Post by Totergott on 2011-04-14
@ seawolf167 - I can't get into Windows loader to delete all partitions.  I used Ubuntu Live CD to delete the partition, but I'm still getting my problem

@ wilee-nilee - To setup my BIOS, I had to press F9 and change the order from Internal Drive to CD/DVD-ROM, that's why Ubuntu and Super Grub load everytime.

---

### Post by wilee-nilee on 2011-04-14
> **Totergott said:**
> @ seawolf167 - I can't get into Windows loader to delete all partitions.  I used Ubuntu Live CD to delete the partition, but I'm still getting my problem

@ wilee-nilee - To setup my BIOS, I had to press F9 and change the order from Internal Drive to CD/DVD-ROM, that's why Ubuntu and Super Grub load everytime.

Correct there is another boot from menu, I have seen hundreds of people on this forum with the exact same problem, and most of the time it was getting them to that second boot from choice menu, not the bios one do you understand what I am talking about.

It may be another problem but I would bet this is the answer.

Since you can boot the Ubuntu disc take a screen shot of gparted and post it as well if you can, if this other method does not work.

---

### Post by seawolf167 on 2011-04-14
Aye, as Wilee-nilee said, there should be a POST message displayed saying something to the effect of "Press [SOMEKEY] now to enter the boot menu". For me this key is [F12], once I hit it, I can select which device to boot off of.

Most BIOS (that I know of) have a setting to control POST messages, boot into BIOS, and search for, and turn on displaying of POST messages if you can't see the boot menu options.

---

### Post by Totergott on 2011-04-14
> **wilee-nilee said:**
> Correct there is another boot from menu, I have seen hundreds of people on this forum with the exact same problem, and most of the time it was getting them to that second boot from choice menu, not the bios one do you understand what I am talking about.

It may be another problem but I would bet this is the answer.

Since you can boot the Ubuntu disc take a screen shot of gparted and post it as well if you can, if this other method does not work.

@ wilee-nilee - I uploaded my gparted.  /dev/sda1 is set to ntfs because GRUB said to.

@ seawolf167 - The only thing I can do about POST BIOS display is delay it.  Right now the order is CD/DVD-ROM, USB CD/DVD, Internal Hard drive.

---

### Post by Totergott on 2011-04-16
Bump :(

I tried installing Ubuntu and dual boot with Windows and that didn't work either.

---

### Post by WorMzy on 2011-04-16
If there's nothing on the hard drive that you want to keep, boot a LiveCD and run

```
sudo dd if=/dev/zero of=/dev/sda
```

It'll take a while to complete, but once it has, the entire disk should be completely wiped. If the Windows install still can't get it's act together, chances are it's a system recovery CD, not an installation CD. Find your installation CD if you have one, or contact your PC's manufacturer for a replacement (assuming the PC came with Windows).

---

### Post by Totergott on 2011-04-17
How long will this take, it's been a few hours already.

---

### Post by suduntu on 2011-04-17
It sounds very silly, but is your win7 or other vista/xp cd/dvd a bootable one?#-o

---

### Post by Totergott on 2011-04-17
All the Windows CD's that I tried, I've used for fresh install, none are recovery discs.  The Windows Server 2008 was from my school that came with a book, and that wouldn't even load.

---

### Post by suduntu on 2011-04-17
> **Totergott said:**
> I thought I could just put in the disc and install like normal, but it wouldn't but and instead that there was an [COLOR=Blue]error and couldn't recognize the file system and followed by Grub Rescue[/COLOR]> Could you elaborate what was the exact error that you got, if you can recall.

> **Totergott said:**
> I successfully set it MBR7 for Windows 7, but when I put in my Windows 7 disc, it wouldn't boot the CD. Yes, I set the BIOS to boot from CD/DVD-ROM.  I also tried MBRVista and just mbr for 2000/XP. MBR is for hard disks generally. setting the MBR of your hdd should not affect the booting from a cd/dvd drive unless these drives are selected as the first boot device in the BIOS Setup. The same is what others have to say.

If you get a message like"No bootable device -- insert boot disk and press any key" there are only two possibilities: 

[LIST=1]
[*]the cd/dvd drive is not the first boot drive. and or function "boot from optical devices" is been disabled in BIOS
[*]the loaded media is not a bootable one.
[/LIST]
can you try the same cd/dvd in other computer and try booting from it?

---

### Post by Totergott on 2011-04-17
> **suduntu said:**
> Could you elaborate what was the exact error that you got, if you can recall.

 MBR is for hard disks generally. setting the MBR of your hdd should not affect the booting from a cd/dvd drive unless these drives are selected as the first boot device in the BIOS Setup. The same is what others have to say.

If you get a message like"No bootable device -- insert boot disk and press any key" there are only two possibilities: 

[LIST=1]
[*]the cd/dvd drive is not the first boot drive. and or function "boot from optical devices" is been disabled in BIOS
[*]the loaded media is not a bootable one.
[/LIST]
can you try the same cd/dvd in other computer and try booting from it?

Okay, the first problem I got said:

error: unknown filesystem
grub rescue >


Then once I used Super Grub, that went away and now everything isn't bootable except Linux distros.

Like right now I'm installing Mint 10 KDE to try a different distro and dual boot, which I doubt will change, but I want to make sure I try all the options.

I put in my Windows 7 disc in my desktop, which has Ubuntu 10.04 on it, and I got the message "Press any key to boot from disc..." and same with my XP Professional disc.

So I would have to say that it's the optical drive, but it doesn't make sense that only Linux boots properly while Windows doesn't.


BTW- I REALLY REALLY appreciate all the help you all have been giving, you have no idea how much better it makes me feel to have help on this.

---

### Post by Totergott on 2011-04-19
Yeah, installed Mint, and it locks my hard drive so I can't partition it, nor does the CD boot like before. So frustrating.  I would set up virtual box, but the graphics are too low in box where her games won't work.  The cap is like 64mb so lame :(

---

### Post by Totergott on 2011-04-24
Okay, maybe I can fix it by physically removing GRUB.  Where is GRUB actually stored?

---

### Post by samacaster on 2011-04-24
You need to delete all Ubuntu partitions with Gparted. And I mean all partitions. From your screen shot I see you still have the swap and extended containers present. These need to go. You don't need to create any partitions once the drive is clean. Shutdown (not reboot) and when you are prompted to remove the media, do so, and stick in your Windows installation disc, then hit Enter to finish the shutdown. Wait a few moments, and provided your boot order ordeal is worked out, turn on the computer and you should boot off of the CD/DVD now.

---

### Post by Totergott on 2011-04-26
But it's locked and won't let me remove it.  How do I go about overriding that?

---

### Post by plucky on 2011-04-26
> **Totergott said:**
> But it's locked and won't let me remove it.  How do I go about overriding that?

Right click on the swap partition and select **swapoff**.

The Live Cd will mount the swap partition,so that is why you are getting the key symbols on the swap and extended partition.One you turn swap off you should be able to delete the partitions.

Good Luck

---

### Post by Totergott on 2011-04-26
> **samacaster said:**
> You need to delete all Ubuntu partitions with Gparted. And I mean all partitions. From your screen shot I see you still have the swap and extended containers present. These need to go. You don't need to create any partitions once the drive is clean. Shutdown (not reboot) and when you are prompted to remove the media, do so, and stick in your Windows installation disc, then hit Enter to finish the shutdown. Wait a few moments, and provided your boot order ordeal is worked out, turn on the computer and you should boot off of the CD/DVD now.
> **plucky said:**
> Right click on the swap partition and select **swapoff**.

The Live Cd will mount the swap partition,so that is why you are getting the key symbols on the swap and extended partition.One you turn swap off you should be able to delete the partitions.

Good Luck

OMG!!! It worked!!  Thank you so much guys, mom is going to be happy to finally get the laptop.  Once I got rid of swap, just booted like normal. :D :D :D

THANK YOU EVERYONE!!

---

### Post by pAsM on 2011-04-26
Hello,
[INDENT]Another option is using the Windows Recovery Console. 

1) Boot into the Windows 7 Install Disk
2) Go through he Keyboard Setup
3) Select "Repair My Computer"
4) Choose the option to launch a command prompt
5) Type bootrec.exe /FixMbr 

The bootrec.exe /FixMbr will tell windows to overwrite the MBR on your hard disk and replace it with the stick Windows MBR
[/INDENT]

---

