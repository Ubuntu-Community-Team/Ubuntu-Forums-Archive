---
title: "error unknown filesystem grub rescue"
date: 2012-05-19
forum: General Help
---

### Post by uefi on 2012-05-19
Hi

My motherboard asrock p67 pro3 with uefi.
After starting computer I got error: 'error unknown filesystem grub rescue'

First i installed win7 64bit (Games and other users).
 Then Ubuntu 12.04 64bit (Main system). Installer dont create efi partition and windows was starting all the time not grub.  In liveCD with boot repair (awesome program)  I know that. So I reinstalled ubuntu with efi partition.
Then installed Linux Mint (testing purposes).
To this point grub work and all systems work.

In windows not used space changed to 2 partitions (one encrypted with truecrypt) and after reset i got error: error unknown filesystem grub rescue'

What happend? Boot repair say again: 
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, >200Mo, start of the disk, boot flag).
Do you want to continue

Info
[http://paste.ubuntu.com/995665/](http://paste.ubuntu.com/995665/)

sda8 is truecrypt partition

---

### Post by uefi on 2012-05-19
Fixed
In boot repaIr I choosed fix mbr. Now there is no boot device at all:)
Then in boot repair choosed default which installed grub (no grub only ubuntu start).
So again in boot repair choosed default (fixed grub, it see all systems, both linux work but not win)
Next with windows DVD choosed fix (didnt find any system but anyway selected first option) and in next screen clicked first option (automatic boot fix) which fixed win.

But still whould like to know what break mbr? Default partition manager in Win7 or Win trueCrypt? Somebody got such problems in the past?

---

### Post by YannBuntu on 2012-05-19
Hello
Looks like you are not using EFI indeed.
For my information, please could you run Boot-Repair, click "Create BootInfo" and indicate the new URL that will appear? (it won't change your boot)

---

### Post by uefi on 2012-05-23
Thx for reply
[http://paste.ubuntu.com/1003660/](http://paste.ubuntu.com/1003660/)
I hope it will help to improve boot repair app.

---

### Post by wilee-nilee on 2012-05-23
> **uefi said:**
> Thx for reply
[http://paste.ubuntu.com/1003660/](http://paste.ubuntu.com/1003660/)
I hope it will help to improve boot repair app.

Make a post at the boot-repair thread linking here several problems I see in the script let the thread helpers there be your help.
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

mainly you have multiple linux installs one needs to be the grub/boot control, and you are missing some files for this in one.

---

### Post by YannBuntu on 2012-05-23
Hello

**@uefi:** thank you. You last ran Boot-Repair from your installed Ubuntu, so i guess its GRUB is repaired. Can you access all your systems (Ubuntu+Mint+Win) now ?
FYI you are not using EFI at all now. (I think you disabled EFI mode in your BIOS, did you?)

**@wilee-nilee:** good eyes, i hadn't seen the missing core.img in Mint ;) (not sure it's useful as Ubuntu is the main OS). Which other problems do you see?

---

### Post by wilee-nilee on 2012-05-23
> **YannBuntu said:**
> Hello

**@uefi:** thank you. You last ran Boot-Repair from your installed Ubuntu, so i guess its GRUB is repaired. Can you access all your systems (Ubuntu+Mint+Win) now ?
FYI you are not using EFI at all now. (I think you disabled EFI mode in your BIOS, did you?)

**@wilee-nilee:** good eyes, i hadn't seen the missing core.img in Mint ;) (not sure it's useful as Ubuntu is the main OS). Which other problems do you see?

Mainly the grub control should be the ubuntu, hard to tell from the script at times, I have not read every post here. There are two active partitions as well the sda6 has a bootflag, so with the efi stuff there I was not sure if it was a problem.

The script run through the bootrepair might be a better indicator of which OS is in the mbr linked though not sure. 

I was really just trying to make sure that you see the thread again, I have basically told people to link up with the main boot-repair thread. I remove any auto emails after 24 hours, so not sure what others do. Several of us look at the thread to make sure you are set up if needed I see oldfred there on occasion, all good help.

---

### Post by YannBuntu on 2012-05-23
ok, thank you.
I think the boot flags are not a problem as GRUB is used. And B-R has disabled efi in fstab too, so efi files won't interfer.
FYI i haven't found yet a command to determine which OS is booted by the GRUB in the MBR, but here we see in the log:
```
boot-repair is **executed in installed-session** (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)

=================== OSPROBER:
/dev/**sda7**:System w u&#380;yciu - Ubuntu 12.04 LTS **CurrentSession**
```

so i guess GRUB is ok (except if SGD has been used) and sda7 is probably the default OS in GRUB menu :)

---

### Post by wilee-nilee on 2012-05-23
> **YannBuntu said:**
> ok, thank you.
I think the boot flags are not a problem as GRUB is used. And B-R has disabled efi in fstab too, so efi files won't interfer.
FYI i haven't found yet a command to determine which OS is booted by the GRUB in the MBR, but here we see in the log:
```
boot-repair is **executed in installed-session** (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)

=================== OSPROBER:
/dev/**sda7**:System w u&#380;yciu - Ubuntu 12.04 LTS **CurrentSession**
```so i guess GRUB is ok (except if SGD has been used) and sda7 is probably the default OS in GRUB menu :)

Yeah that would make sense, I have limitations in this area for sure. I'm just a casual user really I could not code my way out of a paper bag, so I use a stop if I don't know approach and consider some things probably not needed at times

Funny thing though when you think the answer could not be this, it is, yesterday a user just needed the bootflag on a ubuntu partition for the grub boot I had not even considered that. :)

Really my main concern always is not to brick a users set up so I somewhat follow a pattern of analysis the best I know anyway, lol.

---

### Post by uefi on 2012-05-24
Yes in second post added 'fixed' and changed thread title to solved before any other user reply.
Didnt change anyfing in BIOS(UEFI).  So it still in efi mode.
Probably should change mbr to sda6 where efi grub exist(like in beggining). Currently its pointing to sda7. But its works so currently dont want any more problems if dont needed.

missing core.img in Mint
What it do or not do? I only see that Mint think for like 15 seconds before login screen, which is quite long if u look on ubuntu and longer before i corrupted mbr somehow.

---

### Post by YannBuntu on 2012-05-24
Hello
IMHO the bootflags don't have any effect as they are now, so it's ok. 

I'm not sure if the missing core.img can have consequences or not. If i were you, i would type "sudo grub-install /dev/sda && sudo update-grub" from Mint , then once again from Ubuntu (if you want Ubuntu to be the default entry in GRUB), then check if Mint boots faster or not.
If you don't want to take any risk, just don't change anything.

---

