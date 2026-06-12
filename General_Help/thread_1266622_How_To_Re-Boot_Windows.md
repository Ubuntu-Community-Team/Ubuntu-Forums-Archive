---
title: "How To Re-Boot Windows"
date: 2009-09-14
forum: General Help
---

### Post by coltsjon on 2009-09-14
I need to boot windows.  I have my XP disk ready and available but when i insert it into the drive and re boot the system ignores it and i cannot enter the installation to put windows back on. i have tried changing the BIOS settings so that it reads the disk drive first but this hasn't helped I truly do enjoy using ubuntu and plan to put it on my new computer when it arrives, i just want to have a windows computer for convenience.  I do not dual boot the OS and i plan on making this computer solely a windows.  Please tell me how i can boot the CD and start the installation.

---

### Post by quixote on 2009-09-16
This may be a dumb question, but are you sure that XP CD is bootable?  Not all .iso are.  I'm not sure how it works with a Windows iso in that case, but I think you boot with some other bootable Windows media, then run "setup.exe" or whatever it might be on the CD drive.

Another problem might be that the CD itself has somehow become bad.  If it's supposed to boot, does it boot in any other computer?

---

### Post by coltsjon on 2009-09-16
The CD works fine, on any other computer it boots and I can begin installing XP.  When i put it into my drive it will show up so I know the computer recognises it's there, it just will not run setup even when I re start with it in the drive.  I might be doing something wrong seeing as I am quite new to the whole ubuntu package.  In the end I will probably end up just wiping the HD and re installing windows but I'm trying to avoid that as long as possible.

---

### Post by Chronon on 2009-09-16
Try removing all other boot options except for the CD drive.  Ability to boot from the drive is entirely up to the contents of the disk and your BIOS.  Ubuntu has no influence over this.

---

### Post by ubongo2008 on 2009-09-16
any recent mobo has an bootmenu besides the bios which you could also try (somtimes F2 or F12 or ESC it depends)

---

### Post by coltsjon on 2009-09-16
tried removing all other boot options, text came up saying press any key to boot from CD i pressed some keys and it didn't respond and went on booting up the system like normal, i tried this a few times and with different keyboards nothing worked... no luck with the F2 menu either.

---

### Post by Chronon on 2009-09-16
Can you boot from an Ubuntu Live CD?  Are there jumper settings that might be preventing the drive from booting?

Here's a page with a checklist of things that might prevent booting from disk: [http://www.computerhope.com/issues/ch000217.htm#056](http://www.computerhope.com/issues/ch000217.htm#056)

> If you are unable to boot from a CD or DVD it's possible you may be encountering one or more of the below situations.

   1. Need to press a key to boot to the CD or DVD
   2. CD or DVD is not bootable.
   3. Not setup properly in CMOS.
   4. Bad CD / DVD disc.
   5. Jumpers not set properly.
   6. Cables or other drive related issues.
   7. Bad CD drive.


---

### Post by coltsjon on 2009-09-16
it does prompt me to press any key to boot from CD, but when I press nothing happens and it times out, it's frustrating because theres no reason for the keyboard not to be working... i've tried multiple times and nothing seems to work.  would wiping the HD be an advisable choice and then just install windows from there? if so is there a way for me to do it myself or should i take it to a computer shop and get them to do it.

---

### Post by Ocxic on 2009-09-16
the windows install is incompatible with linux partitons.  For some reason the installer needs to copy files to the computers HD, even if the hard drive is not formated yet, how they acomplish this i don't know.

I have this issue myself every time i need to install windows over a linux partition, and had to delete the partition or re-format to fat32 before the installer will boot.

---

### Post by coltsjon on 2009-09-16
i probably have tried it the hard way and most likely have failed, you'd think it would be simple just to get rid of it and put windows back on but it has been much mor e of a challenge than i thought, i plan on wiping the HD now so any ideas would be great, or if anyone comes up with a solution to the problem which is switching from ubuntu back to windows help there would also be appreciated.

---

### Post by Chronon on 2009-09-16
Based on what ocxic said, I would boot a Live CD and delete the existing partitions.  Just write a single partition to the disk and set its type to be FAT32.  Hopefully, the Windows disk will be willing to proceed after that.

---

### Post by coltsjon on 2009-09-18
got it fixed.. used a program called kill disk.  just put it on a CD and put it into the drive, menu came up giving me options, i just chose to wipe the drive, once thats done put the XP CD in and began installing the windows back on it.  Best of all it was free no need to pay some store... i recommend Kill Disk for wiping drives because it was quite simple.

---

### Post by quixote on 2009-09-18
Glad to hear you got it sorted.  I hadn't realized windows was that persnickety about owning the whole drive.  I thought so long as it was first and on the first partition, it was okay.  Nasty OS, if you want my opinion :D

---

