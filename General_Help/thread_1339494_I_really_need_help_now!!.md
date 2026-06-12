---
title: "I really need help now!!"
date: 2009-11-27
forum: General Help
---

### Post by garretts228 on 2009-11-27
I cannot get my cd rom to mount, and when i go to explore the drive /cdrom it is blank.  When i put in a audio cd and go to one of the music playing programs it will show up the songs for example Track01.cda, Track02.cda, etc... It will also play the songs, but thats the only thing i have gotten to work is playing a music cd, and i know there is files on there because I went onto this computer im on know and poped in the cd and all the files are there and working??  I really need this done today, i need to print out some work, and this laptop i have is the most portable thing around.

Computer:
Compaq Presario 1625

Ram:
96mb

CPU:
AMD-K6 266mhz

CD drive:
ATAPI CD-ROM: TOSHIBA CD-ROM XM-170BC

I think this is the Hard Drive:
HITACHI_DK226A-32U

---

### Post by Some Penguin on 2009-11-27
On the bright side, the fact that you can see the tracks on audio CDs suggests that the hardware is functioning and that the kernel is properly detecting your CD drive (given that it's an ATAPI CD drive and not something more unusual like an old Zip or Travan drive I'd be surprised if it didn't).

Some steps to try:

- dmesg | grep -i cd 
  and attempt to determine which device file it corresponds to.  I'd think it'd be something like /dev/hdb or /dev/hdc -- haven't run an ATAPI system for a while.

- mount -t iso9660 /dev/hd[bc] /cdrom
  and if it returns an error message of some sort, post it back into the thread.

---

