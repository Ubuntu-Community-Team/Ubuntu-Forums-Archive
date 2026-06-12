---
title: "A Computer Puzzle for you, and a problem for me"
date: 2009-07-15
forum: General Help
---

### Post by ddivney on 2009-07-15
Ok guys, there's a big problem on my end that can be seen as a puzzle for you guys.

My HP laptop came preinstalled with windows Vista.
When I installed Ubuntu, I accidentally formated my Vista Partiton as a Linux Swap. Now the partiton is back to NTFS, but Vista is gone. Now, there is a **third** partiton housing a special HP recovery manager, which will return the Vista Partiton to factory settings. Hopefully. 
However, the recovery manager gives error "100a" when I try to run it. 

HP email:

*Form your email it sounds that while using HP Recovery Manager to recover partition you get “error 100a” and you like to know what exactly it is.*
 
 *The “error 100a” occurs as you have created the dual partition and now as you are recovering the partition. It may also occur due to an extended partition on the drive.*


Now, there is an extended partiton, unfortunately it houses the logical partiton that ubuntu is installed on.

Ok guys, I want a dual boot system with ubuntu and vista. Have fun with this one, and please help.

---

### Post by lisati on 2009-07-15
A thought before the gurus come up with suggestions: did you make a set of recovery disks when you first bought the machine? 

I recently blew the dust off a set of recovery disks I made for my Compaq machine (Compaq is part of HP) and with them I was able to recreate even the recovery partition as well as the main XP installation. I'm guessing that doing something similar might be possible if the gurus can't come up with a less time-consuming option.

Edit: There are other options. One idea rattling around in the back of my thoughts: what would happen if you deleted all the partitions except the recovery partition? Not sure if that's realistic though

---

### Post by ddivney on 2009-07-15
Unfortunately, when I tried to make the recovery disks, HP's software for it gave me so much trouble I just gave up. I'm regretting that decision right now though...  The thought of deleting the partitions crossed my mind, but that would probably have to be done on a bootable partition manager right?

---

### Post by tariquepark on 2009-07-15
hi there
firstly , ALWAYS make your backup disks for vista because you WILL NEED THEM !!!!!
now to your problem, boot from a live ubuntu disk and use gparted to remove the ubuntu partition. then expand the ntfs back to its original size (assumedly the rest of the available disk) 
then rebooot and run the recovery from the recovery partition again
hopefully this should sovle your prob :)

---

### Post by manualqr on 2009-07-15
hm, but you want to keep ubuntu. so you could back up your ubuntu partition, do as tariquepark suggests, then reinstall ubuntu.. I think

---

### Post by BoneSaw on 2009-07-15
if you want vista back, you may have to toss the ubunutu partition from the moment. i have so many bad stories about people who rely only on the partiton and when the hard drive dies end up having to call hp to get recovery discs. these people are usually very unhappy with me.

---

### Post by bodybag on 2009-07-30
I had this problem before. I installed XP on my pre-installed Vista laptop, but I couldn't get a lot of the audio and webcam drivers to work. So today I went to recovery the entire laptop using the recovery partition.

First, I had to fix the MBR using a vista recovery ISO created by microsoft here: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Burn that ISO onto a cd, pop it into your computer, and run it.

When the vista installer comes up, you have to click repair computer, and then select the partition you want to fix (in this case, the recovery partition).

When the next screen pops up, click command prompt.
Then, type bootrec.exe /fixmbr
And bootrec.exe /fixboot

Once that is completed, type diskpart.
Then type: list disk
Then type in: select disk #            # - Being the disk the recovery partition is on.
Then type: list partition
Then type: select partition #           # - Being the partition the LINUX INSTALLION was on
Then type: delete partition

Basically, the recovery partition failed to reset the computer back to factory defaults because you had an extended partition that wouldn't allow the recovery manager to create the size partition that your computer came preinstalled with. 

Hope that helps.

If you want to dual boot, you will have to get vista disks from someone you know, create the Ubuntu partition you want FIRST, then install vista second, and use the product key you have on the bottom of your computer/laptop.

---

