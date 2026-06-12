---
title: "Getting ready to migrate"
date: 2010-03-09
forum: General Help
---

### Post by AgentWiggles on 2010-03-09
So, I picked up a nice computer very cheap, with Windows 7 installed on it. I'm getting ready to begin doing backups of this computer, which has been my main one for about a year now. Then, I'll empty the hard drives currently installed in both computers, add them to the new PC, and then start fresh by reinstalling Windows 7 and setting up a Ubuntu dual boot. Obviously I'll be backing up my files, but my main question is more focused on backing up my settings from Ubuntu. I know there is a way to store all my package selections in a text file, but I can't find the tutorial and I don't remember how I did it. Anyway, I made this thread for that specific piece of knowledge and also just general suggestions, tips, etc, to make this go as possible. Thanks in advance!

---

### Post by wojox on 2010-03-09
Packages:

```
sudo dpkg --get-selections > myPackages
```

Re-install the system and use this command to get everything back the way it was:

```
 sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

---

### Post by 3rdalbum on 2010-03-09
Your per-userr settings are stored in hidden folders in your home directory. (their names start with a fullstop) Make sure these are backed up, and you will be fine.

---

### Post by AgentWiggles on 2010-03-11
Alright, so I've got my files backed up, and I've got my Firefox and Ubuntu and other relevant settings stored away too. 

Now, what I need to do next

Download and Burn the Ubuntu Install CD

Then hook up the Windows computer and back up the setup file that's included with the downloaded copy of Windows 7 (legally from Microsoft's site, for clarification), just in case something goes wrong while installing Ubuntu as a dual boot.

Then I need to hook up the hard drives (2), one with 80 Gb and one with 200, from the Ubuntu comp to the board in the Windows comp (it's more powerful). 

At that point, all I should need to do is install Ubuntu to the 80 Gb as a dual-boot, and then I can restore my packages and settings in Ubuntu, and start setting up the Windows part to my liking.

Does this sound right? Can anyone think of a missing step?

Also, most importantly, how should I go about formatting the two hard drives currently in my Ubuntu box? The 80 has Ubuntu installed, and the 200 is just extra space, so I think I'm going to format the 200 with Gpart and then just let the new installation of Ubuntu to the 80 to overwrite everything. Sound good?

Thanks so much for your help.

---

### Post by audiomick on 2010-03-11
That all sounds reasonable to me.

---

### Post by AgentWiggles on 2010-03-11
What would be the best file system to format the 200 gig hard drive with? I think I'll just do NTFS but if someone has a better idea I'm open.

---

### Post by audiomick on 2010-03-11
If you want to access the partition/drive from windows and Ubuntu, NTFS is your choice. For partitions that you only want to access from Ubuntu, use EXT4

---

### Post by AgentWiggles on 2010-03-11
> **audiomick said:**
> If you want to access the partition/drive from windows and Ubuntu, NTFS is your choice. For partitions that you only want to access from Ubuntu, use EXT4

Alright, thanks. NTFS it is.

---

### Post by AgentWiggles on 2010-03-11
All right now I'm having a problem because Gparted won't let me format the HDD as NTFS. It's currently unformatted, but the NTFS option is grayed out.

---

### Post by audiomick on 2010-03-11
I've read about that, but I can't remember what the solution was, sorry. It is after 2 a.m. here, and I am not thinking too well anymore.
Hang in there, hopefully someone else will know more.

---

### Post by Slim Odds on 2010-03-11
> **AgentWiggles said:**
> All right now I'm having a problem because Gparted won't let me format the HDD as NTFS. It's currently unformatted, but the NTFS option is grayed out.

You need to install ntfs-3g to get NTFS  support

---

### Post by AgentWiggles on 2010-03-11
Alright, so I go the partition working, and everything is ready for the install of Ubuntu, except this:

GNU/GRUB is the boot manager installed in Ubuntu by default. If you use the Alternate CD you can choose Lilo instead. GRUB and Lilo are both good Open Source boot managers so the main parts of the boot loaders are installed inside Ubuntu. This means Ubuntu is independent and avoids any need for writing to other operating systems. To accomplish this, the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk. The MBR code is changed to point to the boot loader in Ubuntu. You will be presented with a list of operating systems and you can choose one to boot. If you do nothing Ubuntu will boot after a ten second countdown. If you select Windows then GRUB or Lilo will chainload Windows for you at the Windows boot sector, which is the first sector of the Windows partition.

Thats from [here]("https://help.ubuntu.com/community/WindowsDualBoot"). I get the idea, but I don't know how to go about changing the MBR to point to the Ubuntu Bootloader. As soon as I know that, I can get this show on the road.

---

### Post by srs5694 on 2010-03-11
> **AgentWiggles said:**
> the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk. The MBR code is changed to point to the boot loader in Ubuntu. You will be presented with a list of operating systems and you can choose one to boot. If you do nothing Ubuntu will boot after a ten second countdown. If you select Windows then GRUB or Lilo will chainload Windows for you at the Windows boot sector, which is the first sector of the Windows partition.

Thats from [here]("https://help.ubuntu.com/community/WindowsDualBoot"). I get the idea, but I don't know how to go about changing the MBR to point to the Ubuntu Bootloader. As soon as I know that, I can get this show on the road.

There are two ways to install either GRUB or LILO:


[list=1]
[*]In the MBR of the hard disk
[*]In the boot sector of a Linux partition
[/list]


If you do #1, no other partition/boot loader options are required to get GRUB started; the BIOS will load GRUB (or LILO) and any OSes configured in the boot loader will be presented. (They'll only boot if their GRUB/LILO configurations are correct and the OSes are properly installed, of course.)

If you do #2, then you must set the Linux partition in which GRUB or LILO is installed as "active" (aka "bootable" or various other terms). You can do this with Linux's fdisk tool by using the 'a' option ("toggle bootable flag"), by using the "toggle" command in GNU Parted, or in other ways using other utilities.

Installing GRUB/LILO in the MBR is generally more trouble-free and flexible for Linux-only installations; however, Windows has an annoying habit of replacing the MBR boot loader with its own bare-bones boot loader whenever you install Windows. Thus, some people prefer putting GRUB/LILO in a Linux partition's boot sector on dual-boot systems.

---

### Post by AgentWiggles on 2010-03-11
> **srs5694 said:**
> There are two ways to install either GRUB or LILO:


[list=1]
[*]In the MBR of the hard disk

Installing GRUB/LILO in the MBR is generally more trouble-free and flexible for Linux-only installations; however, Windows has an annoying habit of replacing the MBR boot loader with its own bare-bones boot loader whenever you install Windows. Thus, some people prefer putting GRUB/LILO in a Linux partition's boot sector on dual-boot systems.

That's what I want to do, but how do I do it? The annoying habit of Windows won't be a problem as I already have it installed.

---

### Post by audiomick on 2010-03-12
I would suggest just letting the installer do what it wants to do. This will give you grub2 and alter the MBR of the drive that the computer looks at first (usually the first drive) to point at the grub boot files.

It is true that if you then have to re-install windows for some reason, you will have to re-install grub again afterwards, however that is not all that difficult.

For simplicity's sake, I would go with the default install for now. You can then research the possibilities of putting grub somewhere else at your leisure, and change it in the future at an opportune time (e.g. a re-install) if you see the need to.

---

### Post by Slim Odds on 2010-03-12
There is no need to mess with the MBR if you don't want to.

It's actually quite easy to get the Windows boot loader to load linux.

You just need to install grub into the boot sector of the partition where you installed linux instead of the MBR. Then, create a file from that boot sector. Then use it within the Windows boot loader.

Follow these instructions: [http://www.linux.com/archive/feature/113945](http://www.linux.com/archive/feature/113945)

I did this a long, long time ago with XP and it worked just dandy.

---

### Post by AgentWiggles on 2010-03-12
> **Slim Odds said:**
> There is no need to mess with the MBR if you don't want to.

It's actually quite easy to get the Windows boot loader to load linux.

You just need to install grub into the boot sector of the partition where you installed linux instead of the MBR. Then, create a file from that boot sector. Then use it within the Windows boot loader.

Follow these instructions: [http://www.linux.com/archive/feature/113945](http://www.linux.com/archive/feature/113945)

I did this a long, long time ago with XP and it worked just dandy.

PERFECT. Thanks infintely.

---

### Post by ubunterooster on 2010-03-12
When I set up my dual-boot system, I installed Vista on one drive, pulled out the sata, installed Ubuntu on #2.
I use the BIOS to switch between OSs.

---

