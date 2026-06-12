---
title: "Ubuntu not working after install"
date: 2011-01-26
forum: General Help
---

### Post by Framjad on 2011-01-26
Hi All,

Im relatively new on the Linux/Ubuntu scene and recently I decided to finally ditch windows completely and opt for full Ubuntu immersion by deleting the Windows partition and resizing my Ubuntu one. I then decided, in my foolish wisdom, to completely reinstall Ubuntu 10.10 on the new partition. I don't think this worked. The install took approx 8 hours to complete, which I thought was odd, as it got stuck on the "update-grub" section saying things like-

Buffer I/O error on device sda, locical block 6
Buffer I/O error on device sda, locical block 7
Buffer I/O error on device sda, locical block 8

ata1.00: status: { UNC } 
ata1.00: status: { DRDY } 

end_request: I/O error, dev sda, sector 52

etc. 

Finally it installed but when I tried to boot Ubuntu it came up with

something like this

[http://dominikengbers.gmxhome.de/bug.JPG](http://dominikengbers.gmxhome.de/bug.JPG) (this isn't my picture, I'm actually not in the position to use my laptop right now)

I've looked at the forums and they said to type exit after that. This just seemed to lead to more of the first thing

Buffer I/O error on device sda, locical block 6
Buffer I/O error on device sda, locical block 7
Buffer I/O error on device sda, locical block 8

ata1.00: status: { UNC } 
ata1.00: status: { DRDY } 

and also bits like this (again not my actual computer)


[ 64.060350] ata1.01: device reported invalid CHS sector 0
[ 64.060423] ata1: EH complete
[ 94.816062] ata1: lost interrupt (Status 0x58)
[ 94.820022] ata1: drained 32768 bytes to clear DRQ.
[ 94.856514] ata1.01: limiting speed to UDMA/33:PIO4
[ 94.856580] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 94.856648] ata1.01: failed command: READ DMA
[ 94.856720] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[ 94.856724] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 94.856874] ata1.01: status: { DRDY }
[ 94.856960] ata1: soft resetting link
[ 95.044523] ata1.00: configured for UDMA/66
[ 95.060285] ata1.01: configured for UDMA/33
[ 95.060350] ata1.01: device reported invalid CHS sector 0
[ 95.060421] ata1: EH complete

I tried to boot my Live CD to see what was going on but it did the same thing as above.

I am practically, if not completely, illiterate when it comes to computers, so any help would be greatly appreciated. 

My computer is Dell Inspiron 6400

Ignore the smileys, I fon't know why they are there

---

### Post by acplusplusprogrammer on 2011-01-26
Well, I think you should:

OPTION 1
1) Insert the Ubuntu installation CD
2) Don't install and select the option TRY UBUNTU (the live version, the one that runs from the CD)
3) Open the terminal (from the live version) and write "sudo touch /forcefsck" . This should make the "scandisk"

OPTION 2
1) Insert the Ubuntu installation CD
2) Install Ubuntu, choosing to ERASE and USE ALL THE DISK
3) Go on untill the installation is complete


ANYHOW
Peraphs there are some damaged sectors on your harddisk. But can't really say

---

### Post by Framjad on 2011-01-26
Thank you so much for your helpful reply, after doing Option 2, my computer is now working. Awesome. 

Framjad

---

