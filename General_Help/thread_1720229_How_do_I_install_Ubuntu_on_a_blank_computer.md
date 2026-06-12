---
title: "How do I install Ubuntu on a blank computer?"
date: 2011-04-03
forum: General Help
---

### Post by MagnetsNextToMotherboard on 2011-04-03
I'm trying to install Ubuntu on a blank computer that I just got a new hard drive for, but I get this on a black screen with white text:

"BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system"

Maybe I didn't make the CD correctly I made like 3.. Please help.:confused:

---

### Post by mick463 on 2011-04-03
I had a similar problem once.Try going into the bios and changing the HDD to be a sata drive not a sata drive with a EIDE signal,this was done for win xp in the bios for some motherboards as XP cn not read a true sata signal for some reason.If you look in the bios for the hard drive and have a play around you will find it.It worked for me.
Cheers mick463.

---

### Post by MagnetsNextToMotherboard on 2011-04-03
I don't have any options like that in my bios. What is the "Live file system"????

---

### Post by techunit on 2011-04-03
You made the live cd incorrectly try using Imgburn to make the disk.

---

### Post by Habeouscorpus on 2011-04-03
Burn the disk slowly, and if possible, download a new .iso from the torrent. (The torrent program makes sure everything's downloaded correctly.) I've had this problem myself.

---

### Post by briguy40 on 2011-04-03
I had this problem with an install of Maverick.

A couple of things I woud try:

First, follow this guide [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) to check the integrity of your download and cd. This was my problem.

Second, and I know it's silly and don't know why it works, but download dban (Darik's boot and nuke) and zero your drive with the quick wipe option. As I said, I don't know why it would make a difference, but I've yet to get a clean install on Backtrack4 or Sabayon without doing it first, especially on hd's that have been "pre-owned".

---

### Post by MagnetsNextToMotherboard on 2011-04-03
Ok I'm about to try torrenting it. But, what torrent do I use from this page: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download) ? "Desktop" or "Alternate"?

---

### Post by Learning Linux 2011 on 2011-04-03
I would just go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
choose the 64-bit version and download it from there.

I assume everything in your computer can run a 64-bit operating system.  If not, try the 32-bit CD.

What operating system and/or program(s) are you using to burn the CD's?

---

### Post by techunit on 2011-04-03
> **MagnetsNextToMotherboard said:**
> Ok I'm about to try torrenting it. But, what torrent do I use from this page: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download) ? "Desktop" or "Alternate"?
Desktop Much more friendly for new users.

---

### Post by mick463 on 2011-04-04
Mate i had that exact same thing happen to me go in to bios and look for Integrated peripherals or something like that it depends on what type of bios you have  then make sure the sata port  is in native mode and not in native IDE mode.It should be enabled as disabled will make it work in legacy IDE mode.Just take your time and i am pretty sure it will work.

---

