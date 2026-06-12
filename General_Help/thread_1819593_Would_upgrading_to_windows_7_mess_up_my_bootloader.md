---
title: "Would upgrading to windows 7 mess up my bootloader?"
date: 2011-08-06
forum: General Help
---

### Post by shresthanator on 2011-08-06
Right now I have my machine set up with ubuntu and windows home vista home basic, using the GRUB bootloader. I installed ubuntu after I installed windows on my hard-drive, so everything worked out.

However I do remember once that I tried installing windows after ubuntu was on my machine, and windows just messed everything up. The windows boot-loader did not play nicely with ubuntu, so I had to go back and do everything in the reverse order. So now I'm thinking about upgrading my vista to windows 7 (not buying the OEM OS just an upgrade). Would this mess with grub? Does any one have any experience with this?

---

### Post by oldfred on 2011-08-06
Any install of windows or most auto repairs of Windows writes the Windows boot loader to the MBR.

You need to have a Ubuntu liveCD of your current version, so you can easily reinstall the grub2 boot loader to the MBR. After restoring grub's boot loader, boot Ubuntu and run this to find the new Windows install.
```

sudo update-grub
```

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by x-D on 2011-08-06
THIS METHOD I'M ABOUT TO SHOW YOU CAN BE DONE USING:

. A LIVE CD
. A LIVE USB
. OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU (IF YOU CAN ACCESS IT IN SOME WAY)

> **shresthanator said:**
> Right now I have my machine set up with ubuntu and windows home vista home basic, using the GRUB bootloader. I installed ubuntu after I installed windows on my hard-drive, so everything worked out.

However I do remember once that I tried installing windows after ubuntu was on my machine, and windows just messed everything up. The windows boot-loader did not play nicely with ubuntu, so I had to go back and do everything in the reverse order. So now I'm thinking about upgrading my vista to windows 7 (not buying the OEM OS just an upgrade). Would this mess with grub? Does any one have any experience with this?

A much easier way for the inexperienced user would be to do this:

First of all, download a program for Ubuntu called Boot-Repair - get this by doing:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```

Run Boot Repair, (search for it in Unity), or go to:
System--->Administration--->Boot-Repair menu in gnome 2/ classic mode.

Go through the settings for the program using this as a resource: (feel free also to contact me) [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and then after going through with this program (2 mins or so maximum)

Do this:

```

sudo update-grub

```

It should work without doing this, but just to be safe, we will do this so it will definitely Update the new installed Version of GRUB with Windows 7 and Ubuntu in the records! :guitar:

---

### Post by apollothethird on 2011-08-06
> **x-D said:**
> A much easier way for the inexperienced user would be to do this:

First of all, download a program for Ubuntu called Boot-Repair - get this by doing:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Run Boot Repair, (search for it in Unity), or go to:
System--->Administration--->Boot-Repair menu in gnome 2/ classic mode.

Go through the settings for the program using this as a resource: (feel free also to contact me) [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and then after going through with this program (2 mins or so maximum)

Do this:

```

sudo update-grub

```It should work without doing this, but just to be safe, we will do this so it will definitely Update the new installed Version of GRUB with Windows 7 and Ubuntu in the records! :guitar:

Hi, x-D.  Maybe I'm missing something, but if the user install Windows (reinstalled or repaired Windows) he couldn't get to System->Administration->Boot-Repair.  If the system wouldn't boot, I believe he'd have to do what Oldfred suggested, or I'm missing something.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by oldfred on 2011-08-06
You can use boot repair or Supergrub but should also download those as liveCDs. I often have several ways and have used either Ubuntu liveCD or Supergrub.  I prefer to boot from ISO as then it is updateable. I used to have stacks of old version CDs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by apollothethird on 2011-08-06
> **oldfred said:**
> You can use boot repair or Supergrub but should also download those as liveCDs. I often have several ways and have used either Ubuntu liveCD or Supergrub.  I prefer to boot from ISO as then it is updateable. I used to have stacks of old version CDs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Thanks.  I'll be downloading the iso's and testing them for future boot problems I might experience and for recommending them to other Ubuntu users who might have boot problems... as the boot problems are a frequent occurrence in the forums.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by x-D on 2011-08-06
> **apollothethird said:**
> Thanks.  I'll be downloading the iso's and testing them for future boot problems I might experience and for recommending them to other Ubuntu users who might have boot problems... as the boot problems are a frequent occurrence in the forums.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Yeah, it's fine, the one thing you are missing, is that this program can be used with a Live Disk, and obviously to Install Ubuntu in the first place, the BIOS are configured to allow him/her to boot from the CD/DVD Drive.

Right, so they can boot into the Live Disk, and then follow on from my instructions :)

---

### Post by x-D on 2011-08-06
> **oldfred said:**
> You can use boot repair or Supergrub but should also download those as liveCDs. I often have several ways and have used either Ubuntu liveCD or Supergrub.  I prefer to boot from ISO as then it is updateable. I used to have stacks of old version CDs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Hey... Using Boot-Repair (from a Live Disk) is what I suggested... no fair :) only kidding hahaaaa :P

I haven't heard of Supergrub? Is it pretty much the same thing as boot repair?

:guitar:

---

### Post by apollothethird on 2011-08-06
> **x-D said:**
> Yeah, it's fine, the one thing you are missing, is that this program can be used with a Live Disk, and obviously to Install Ubuntu in the first place, the BIOS are configured to allow him/her to boot from the CD/DVD Drive.

Right, so they can boot into the Live Disk, and then follow on from my instructions :)

Yes.  I had caught on to that (installing into live disk) before posting my last message.  I should have acknowledged that in my message.

Thanks for sharing the gem!

I can't imagine any problems in using it.  But if I do encounter any I'll let you know.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by oldfred on 2011-08-06
@x-D
I was just trying to expand on your good suggestion on boot repair. I slightly prefer to have fully bootable CD. But you can download it into your liveCD/USB but then next time you also have to re-download it as it cannot be saved on your Ubuntu liveCD.  If you have persistence set, you could save it on a liveUSB.

Super grub was the standard with grub legacy, but the change to grub2 was so large that it took awhile for supergrub to catch up. Many distributions still use old grub legacy also. So Supergrub now has 3 versions, one to boot just about anything, one to reinstall a grub2 boot loader and one for grub legacy.

---

### Post by x-D on 2011-08-07
> **oldfred said:**
> @x-D
I was just trying to expand on your good suggestion on boot repair. I slightly prefer to have fully bootable CD. But you can download it into your liveCD/USB but then next time you also have to re-download it as it cannot be saved on your Ubuntu liveCD.  If you have persistence set, you could save it on a liveUSB.

Super grub was the standard with grub legacy, but the change to grub2 was so large that it took awhile for supergrub to catch up. Many distributions still use old grub legacy also. So Supergrub now has 3 versions, one to boot just about anything, one to reinstall a grub2 boot loader and one for grub legacy.

Sounds good, like something that might be of use to my legacy machines. I was only joking you know :) about the stealing part :)

---

