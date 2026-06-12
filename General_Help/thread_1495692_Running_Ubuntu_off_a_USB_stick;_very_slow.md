---
title: "Running Ubuntu off a USB stick; very slow"
date: 2010-05-28
forum: General Help
---

### Post by gawain2 on 2010-05-28
Many thanks to the poster who helped me get Ubuntu running.

Now that I'm on Ubuntu, I love the look of it. Navigating the OS menus is fast and programs are generally fast once they're running, but they're extremely slow when first opened (basic programs like Firefox, OpenOffice Writer, etc.). Is this because I'm running Ubuntu off of a USB stick? I don't know if I'd make the full switch if programs typically open this slow, but otherwise I love Ubuntu.

---

### Post by burton247 on 2010-05-28
LiveCDs are always slower, USB should be faster. But the data has got to travel through the USB port, where as from hard drive it travels via SATA/IDE. If it is a modern laptop it's likely to be SATA. To my knowledge these are 2-3 times faster than USB. 

Also in personal experience I installed arch on a USB drive, this was a group up install, barely any services running, no graphical login, running Xmonad WM and it was still slower than Ubuntu that was on my hard drive.

---

### Post by bumanie on 2010-05-28
NAND gate flash memory like that most commonly in a flash drive has slow read/write speeds compared to a hard drive - in general terms, the above thread is correct that flash is a approximately 3x slower.

---

### Post by marcottebj on 2010-05-28
I found that the brand of flash drive makes a significant difference (believe it or not).  I installed Ubuntu on two different brands, and one ran MUCH slower than the other (painfully slow).  I'm using a 16GB PNY Attache, and it flies!  Try changing brands.

---

### Post by gawain2 on 2010-05-28
Thanks for the very helpful replies!

If the brand matters, it's a Duracell 8 GB flash drive. At any rate, I'm guessing that Ubuntu will run faster than Windows on my laptop once I install it on my hard drive. And now that I see that PDF-Xchange Viewer can be run perfectly on Linux through Wine, I'm going to make the full switch to Ubuntu. :)

---

### Post by marcottebj on 2010-05-28
sounds good, but don't give up the portability of having it on a thumbdrive just because your first attempt ran slow.  I'm running it off a thumbdrive right now, and it screams.  I can't tell a difference between having it on the HD, or the stick.  Honestly.  I did notice a discernable difference depending on the stick I was using, however.  As I said,  I got the best results with the PNY Attache (8GB and 16GB).

---

### Post by bakegoodz on 2010-05-28
Many of the cheaper flash drives are slow, like only read 16 MB/s and slower and write at half the speed. A good clue is that the specifications don't tell you the speed of the drive.

There is one thing I know that can help with the speed on flash memory. By default linux updates the file access time of every file that is read, which really bogs down flash. To disable this just add: noatime option on your drive in the /etc/fstab file
example:
/dev/sda1 /    ext4    noatime,errors=remount-ro 0       1

---

### Post by C.S.Cameron on 2010-05-28
If you think Ubuntu is slow on a flash drive you should see XP on a flash drive.

---

### Post by marcottebj on 2010-05-28
Lol

---

### Post by gawain2 on 2010-05-29
Well, now it's running at a respectable speed off of the USB stick, but I've got a new problem: Firefox crashes constantly. Seemingly anytime there is some slowdown, Firefox crashes. It's especially prevalent when Flash is involved.

Can this, too, be blamed on running the OS off a USB stick? Surely this isn't normal...

---

### Post by marcottebj on 2010-10-12
I have no issues with Firefox crashing when running booting from my flash drive.  As I said, I'm using a PNY Attache'.  I've had the best luck with that brand of flash drive.  I've used my bootable flash drive on 6 different PCs.  I've never had a problem.  I'm running Ubuntu 10.04

---

