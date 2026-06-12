---
title: "ubuntu boot to delete Winxp dll?"
date: 2009-08-05
forum: General Help
---

### Post by Luxx on 2009-08-05
I don't know if this is possible but I'm running out of options. With no WinXP CD or WinXP boot disk available and knowing I can boot any computer with an ubuntu disk to at least view files I thought I would try.... but is access possible?

I installed a stubborn video driver on a WinXP computer and it caused screen to go black after initializing. I know the computer works, but need to find a way to remove, rename, or rewrite a file to get the visual back booting to Windows.

Is it possible to obtain create/delete or read/write access to the HD from CD-only boot from an ubuntu live CD? How about shrinking Win partition and install ubuntu, dual boot? I don't know if there is enough HD space for that and we can't afford to erase the Windows files.

Win XP Home on Intel 865
ubuntu Feisty Fawn live CD

Problem is updated physx driver with no dedicated physx card = black screen at Windows login. The older physx drivers didn't require a dedicated card.

Removed nvidea geforce card and plugged monitor into onboard Intel crap card and can see and navigate files with ubuntu live CD, but the HD in media folder is locked. Any way around this?

(This message posted from my ubuntustudio 9.04 computer, WinXP comp belongs to spouse.)

---

### Post by ugm6hr on 2009-08-05
> **Luxx said:**
> Removed nvidea geforce card and plugged monitor into onboard Intel crap card and can see and navigate files with ubuntu live CD, but the HD in media folder is locked. Any way around this?

Locked?  What do you mean?

If you mean that you can see it, but it won't allowyou access to the file in question, then try using sudo:

```
gksudo nautilus
```

This gives you root access to all files - be careful what you delete!!!!!

If this still doesn't work, then it may be the ntfs-3g driver in Feisty was not on the LiveCD - try a 9.04 LiveCD/USB instead.

---

### Post by Luxx on 2009-08-05
Thank you for your reply.

> **ugm6hr said:**
> Locked?  What do you mean?

If you mean that you can see it, but it won't allowyou access to the file in question, then try using sudo:

```
gksudo nautilus
```

This gives you root access to all files - be careful what you delete!!!!!

If this still doesn't work, then it may be the ntfs-3g driver in Feisty was not on the LiveCD - try a 9.04 LiveCD/USB instead.

'gksudo nautilus' didn't work. I can't change permissions. They appear to change,but then default and the disk is still locked (showing lock symbol over folder for HD) 

I didn't find ntfs-3g in my packages menu, but did find ntfsprog. Tried using ntfsmount, but I'm really confused about the commands.

Should I be able to get read/write access to the Hd with ntfsprog, and if so, how? Literature suggested I could, but I'm lost.

Or, would I be able to install ntfs-3g package from a pen drive and run it?

Thanks again.


Oh -- 9.04 LiveCD/USB  --it would have to fit on 2.0 g pen drive. That's all I have. Still researching and trying things.

---

### Post by mcduck on 2009-08-05
> **Luxx said:**
> Thank you for your reply.



'gksudo nautilus' didn't work. I can't change permissions. They appear to change,but then default and the disk is still licked (showing lock synbol over folder for HD) 

I didn't find ntfs-3g in my packages menu, but did find ntfsprog. Tried using ntfsmount, but I'm really confused about the commands.

Should I be able to get read/write access to the Hd with ntfsprog, and if so, how? Literature suggested I could, but I'm lost.

Or, would I be able to install ntfs-3g package from a pen drive and run it?

Thanks again.

You won't be able to change permissions on a NTFS drive simply because NTFS doesn't understand permissions and ownerships as they are used in Linux and other Unix systems. So NTFS has no way way to store your permissions changes.

Open Nautilus with gksudo and you'll be able to access and modify your  files. You just can't change their permissions.

---

### Post by Luxx on 2009-08-05
> **mcduck said:**
> You won't be able to change permissions on a NTFS drive simply because NTFS doesn't understand permissions and ownerships as they are used in Linux and other Unix systems. So NTFS has no way way to store your permissions changes.

Open Nautilus with gksudo and you'll be able to access and modify your  files. You just can't change their permissions.

?? No I can't. I've been trying everything I can think of or look up for the last 6 hours. I honestly DID try it before I said it didn't work.

If I try to edit, delete or rename a file in the WINXP HDD from the ubuntu live CD, opening nautilus in terminal with "gksudo nautilus" I cannot move a folder or file to trash. I cannot rename. These options are grayed out. When I try to edit a file I get the following error:

The file"filename" is read-only. Would you like to replace it with the one you are saving?

I choose replace and then get the error:

Could not save the file filename. You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again. 

What is this about NTFS not understanding linux file systems? It was my understanding that "ntfs-3g" and "ntfsprog" were drivers/programs that would allow read-write access to NTFS file systems. The HDD I am trying to change files on is Windows XP Home. Did I misread something?

---

### Post by mcduck on 2009-08-05
> **Luxx said:**
> 
What is this about NTFS not understanding linux file systems? It was my understanding that "ntfs-3g" and "ntfsprog" were drivers/programs that would allow read-write access to NTFS file systems. The HDD I am trying to change files on is Windows XP Home. Did I misread something?

Yes, the driver does allow reading and writing NTFS file systems. But it doesn't add any features that aren't part of the flesystem itself. ;)

The things that aren't supported are things that aren't part of NTFS. Windows doesn't use file ownerships & permissions like they are used in Linux, so Microsoft didn't include any way to store such permissions in their file systems. And without a way to store the permissions commands like "chmod" and "chown" used to change the permissions are useless.

Still, that shouldn't be a problem. The permissions for Windows file systems are set for the whole filesystem at the time it's mounted. So it's just that you can't change permissions of individual files on these systems.

Actually I bet your problem here is that your Windows crashed, so the filesystem wasn't cleanly unmounted. And now when you try to mount it Linux detects that there's something wrong with the filesystem and mounts it as read-only to protect it.. It should be possible to mount the drive manually from command line with the "force"-option to solve that issue..

---

### Post by ugm6hr on 2009-08-05
> **mcduck said:**
> Actually I bet your problem here is that your Windows crashed, so the filesystem wasn't cleanly unmounted. And now when you try to mount it Linux detects that there's something wrong with the filesystem and mounts it as read-only to protect it..

I have never encountered this, except with regard to partition manipulation.  Nevertheless, unsafe unmounting (i.e. crashes) have been documented as causing problems.

I would still suggest using 9.04 first; a 2G USB will work fine (just need to wipe it first).  Use the Netbook Remix for simplicity of USB installation.

This is the ntfs-3g driver: [http://packages.ubuntu.com/jaunty/ntfs-3g](http://packages.ubuntu.com/jaunty/ntfs-3g)

I think it is on the NBR Live USB, since I have used it to delete files on XP partitions before.  Uncertain how you would track it down for Feisty, since it is obsolete.

---

### Post by rob2uk on 2009-08-05
There's a way to do this without booting another OS, and it's probably a bit safer...

Start the PC without a CD in the tray, and keep mashing F8 until you get a list of boot options.

First, try 'enable VGA mode' and see if that gets you into Windows.

If not, try again choosing 'safe mode with networking'.

From there you should be able to visit the nvidia site and download an archived driver for your card

---

### Post by Luxx on 2009-08-05
Yeah... I tried all Windows options that didn't require a Windows CD... no luck. This happened before with the previous physx driver, but somehow after several tries we were able to get in with VGA mode and disable write binding and were good to go. But the current physx driver seems to be a little more stubborn. Write binding was already disabled and VGA mode still gave us a black screen.

At this point I WANT to use Linux to fix a Windows problem. I just really like the idea of it. :D I converted to Linux a few years ago after having to reinstall chipset drivers on a Win98 SE comp every few days and finally decided to try something else -- ANYTHING else. I admit I have been frustrated at times, but I have not been disappointed. Linux always seems to have a solution. At the same time I don't mind having a Windows computer at home as well... for the time being.

After getting some sleep, I'm setting up the bootable USB and will try again. Thank you all for your help. I'll report back soon.

---

### Post by rob2uk on 2009-08-05
The trick may be to find out which files are installed by the driver package, then scour the System32 folder for them.

Don't just delete them, change the file extensions so that the OS can't find them or load them.

After that you should be able to get back into Windows, albeit with a very low screen resolution and colour depth (4 bit, anyone?)

---

### Post by Luxx on 2009-08-06
....making USB version of coasters...:confused:

I first tried using USB Startup Disk Creator to put 
ubuntu-9.04-desktop-i386 on a 2.0 GB USB drive I had cleared. 
USB Startup Disk Creator did not recognize .img file. 
USB had files on it but did not boot.

Cleared  USB device completely.

Installed ImageWriter and followed instructions per [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) under Ubuntu, Graphical interface. I noticed the code showing in Details box said something about unmounting device and then it looked like it froze, How do I know when writing is finished? I tried to duplicate the message but on second try I got:
 
Image: /home/user/Desktop/ubuntu-9.04-netbook-remix-i386.img
Target Device: Unknown USB Flash Memory (/dev/sdb)
Executing: dd if=/home/user/Desktop/ubuntu-9.04-netbook-remix-i386.img of=/dev/sdb

I also got the following two messages when trying to see what happened with the USB drive:

Cannot mount volume.
Unable to mount the volume.
Details
mount wrong fs type, bad option, bad superlock on /dev/sb1.
missing codepage or helper program, or other error
In some cases useful info is found in syslog -try
dmesg | tail or so [OK]

Error
Unable to mount 2.0 GB Media
DBus error org.freedesktop.DBus.Error.NoReply. Message did not recieve a reply (timeout by message bus) [X Close]

I should have run it from command line. I seem to have better results  generally when I do.

---

### Post by ugm6hr on 2009-08-06
> **Luxx said:**
> I should have run it from command line. I seem to have better results  generally when I do.

This is how I created my NBR LiveUSB.

Format USB drive vfat first - just to be certain.

---

### Post by Luxx on 2009-08-07
I've tried this a few times now and I'm beginning to think the Windows computer BIOS is lying about the ability to boot from USB. I've made sure USB boot is enabled and USB first in boot order as well as second with CD (empty) first. I see the computer checking the USB, but nothing happens. That is to say it still tries to boot from HDD with the screwed up video drivers after checking USB and CD.

I reformatted USB with vfat and I'm trying it again. 

If it doesn't work this time I might try booting with the Fiesty Fawn CD again and see if I can transfer the ntfs-3g package with the USB. I'm wondering if I will have to also transfer and load dependecies and if all this will run from a live OS (not installed).

---

### Post by ugm6hr on 2009-08-07
> **Luxx said:**
> If it doesn't work this time I might try booting with the Fiesty Fawn CD again and see if I can transfer the ntfs-3g package with the USB. I'm wondering if I will have to also transfer and load dependecies and if all this will run from a live OS (not installed).

This will work, but is not easy due to the difficulty in finding Feisty packages.

Easiest to get a CD-R to burn 9.04 to.

---

### Post by Luxx on 2009-08-13
I burned a new Ububntu live CD, 9.04, and was able to get the access I needed to get into the Windows computer and rename the Physx files and dlls. This theoretically should have allowed a boot into VGA mode, name the files and dlls back and uninstall Physx properly. So, on the Ubuntu end of things I'm calling this a successful resolution.

Unfortunately there were other issues and I'm going to need something like a BartPE disk anyway. A large number of installed programs were zipped before the Physx drivers were installed and the registry is an impossible mess.

Thank you all for your help and input. :)

---

