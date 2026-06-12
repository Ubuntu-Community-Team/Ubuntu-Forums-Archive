---
title: "A strange Windows 7/Ubuntu 9.10 dual boot problem - could this affect others as well?"
date: 2009-11-15
forum: General Help
---

### Post by ispyamoose on 2009-11-15
This is a really strange problem that I came across, and I'm hoping that someone could help identify what might have gone wrong. I fixed the problem, but I'd like the problem not to happen again.

On my computer, I had Windows 7 Professional 64-bit and Ubuntu 9.10 in a dual boot, with the default GRUB loader. I did not install Ubuntu using Wubi (torrents at my university are blocked), so I had it installed side by side. I had no problems booting into either operating system. Here's the the really strange part: I had not booted into Ubuntu for about a week. I had been using Windows 7 full time for the last week, since I have to use it for some of my schoolwork. Everything was working perfectly until this morning when I booted my computer up. The screen said "Loading GRUB" or something like that (no error messages), and then the computer would go into an endless boot cycle. I ended up having to use a friend's computer to download/burn an .iso for Ultimate Boot CD (which I'm keeping by the way, ha), using a utility to boot Windows 7 up, creating a repair disc for Windows 7 under maintenance tools (I got W7 upgrade for $30 from Microsoft, haven't gotten the discs in the mail yet... grr), rebooting to the repair disc, and then opening the command prompt portion and typing: bootsect /nt60 C: /mbr

Pretty ridiculous in my opinion. What on earth could have gone wrong? I ALWAYS shut down my computer properly. I almost bet money that Microsoft probably had something to do with it (since I hadn't booted into Ubuntu for about a week). I checked the system restore information to see if Windows 7 had installed an update last night before I shut off the computer, and it had (but I can't find out what it is, because the new update refuses to show up in Windows Update).

So anyways, Windows 7 is working normally now. I think I'll probably create a disc image for Windows 7 before trying to install Ubuntu again. :shock:

---

### Post by Lucky75 on 2009-11-15
Which OS did you install first? Are they on the same drive? I have a feeling you had ubuntu installed first and then installed windows 7. Windows 7 always needs to be the first partition on the drive, and it will overwrite whatever is there with it's own bootloader.

---

### Post by ispyamoose on 2009-11-15
> **Lucky75 said:**
> Which OS did you install first? Are they on the same drive? I have a feeling you had ubuntu installed first and then installed windows 7. Windows 7 always needs to be the first partition on the drive, and it will overwrite whatever is there with it's own bootloader.

No, I installed Windows 7 first. And yes, they are on the same drive. I've done a lot with partitioning before.

---

### Post by ranch hand on 2009-11-15
There are not many problems with MS an grub2.

You should be able to get it straightened out by following thes instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You will need a LiveCD.

---

