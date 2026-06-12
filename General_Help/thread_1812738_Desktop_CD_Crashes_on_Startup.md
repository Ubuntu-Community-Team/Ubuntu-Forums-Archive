---
title: "Desktop CD Crashes on Startup"
date: 2011-07-26
forum: General Help
---

### Post by megabenman on 2011-07-26
I know this is a common problem but I haven't found any solutions after searching, so if anyone can enlighten me that would be a big help.

I'm using an old Dell, 3.0 GHz P4 with 256MB ram.  The windows XP partition has crashed so I'm attempting to boot into linux to see if the files are recoverable.  Using the xubuntu live CD, it gets to the point where it shows a blank desktop (with the xubuntu background) and the "X" cursor.  The cursor can be moved for a bit, but after a while it becomes frozen and nothing happens.  One time it went to the screensaver before it showed the desktop and froze immediately after starting that.

Any tips on how to fix this?

(Forgot to mention this is 11.04)

---

### Post by mikewhatever on 2011-07-26
With only 256MB of RAM minus the amount shared with the graphics, I'd guess it runs out of memory. I'd recommend trying a light weight distro, especially if there is no way to add more RAM - Lubuntu, AniX, Puppy should probably work for you.


PS: I didn't know 'crashing' was common (whatever that means). Anyway, thanks for the info.

---

### Post by JC Cheloven on 2011-07-26
> **mikewhatever said:**
> PS: I didn't know 'crashing' was common (whatever that means). Anyway, thanks for the info.
:lolflag:

As to the subject: If you're only trying to recover files, with your amount of ram I'd also suggest [Puppy Linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm").

If you are willing to install linux afterwards, perhaps you like Puppy itself. Not bad at all. But if you prefer to stick within the ubuntu family, I suggest LUbuntu. With that short memory I'd follow this path:
- Donlowad an alternate ubuntu cd (not the live "desktopp" cd) from [here]("http://www.ubuntu.com/download/ubuntu/alternative-download").
- Use it to partition including some swap area, and install a command-line system (no graphical interface yet).
- Boot in the command line system and run "sudo apt-get update", then "sudo apt-get upgrade", then "sudo apt-get install lubuntu-desktop"
- Reboot. You should get into LUbuntu.

EDIT: you need an internet connection to follow this path. I suggested that way for safety, but the [LUbuntu live cd]("http://lubuntu.lafibre.info/10.04/") should in theory run and install in your system.

---

### Post by megabenman on 2011-07-26
Thanks for the replies.  I'll try lubuntu and puppy linux.
As much as I'd love to install linux on it, this is the company's computer so I don't really have that authority haha.

---

### Post by mikewhatever on 2011-07-26
> **megabenman said:**
> Thanks for the replies.  I'll try lubuntu and puppy linux.
As much as I'd love to install linux on it, this is the company's computer so I don't really have that authority haha.

Hm..., do you have the authority to recover files, or else, what are you trying to do?

---

### Post by megabenman on 2011-07-27
I used Puppy linux which booted successfully.  However, it is unable to find the harddrive.  I tried GParted and the Unmount/Mount program, and none of them were able to detect the harddrive, only the CD.  When the computer boots up it tells me there is an error on SATA 0 so I know the computer can detect the harddrive, since when I pull the harddrive out it says that SATA 0 isn't there.

Is there another live CD/program I can try or is this harddrive a goner?

---

### Post by wildmanne39 on 2011-07-27
Hi, it sounds like the drive is gone, You can try to mount it with disk utility if puppy has a disk utility.

---

### Post by JC Cheloven on 2011-07-27
> **wildmanne39 said:**
> Hi, it sounds like the drive is gone, You can try to mount it with disk utility if puppy has a disk utility.

It has. In fact I remember there was a launcher for it on the desktop (well, I don't have puppy installed right now, and the appearance of puppy's desktop changes quite a lot between releases...). 

Anyway, there is a "disk mount" utility over there. Start it and try mounting the disk.

Or if you succed to boot LUbuntu, there is a "disk utility" tool in the system admin menu.

---

