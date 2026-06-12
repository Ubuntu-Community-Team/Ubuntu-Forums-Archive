---
title: "Trying to recover data from broken ubuntu, how do I access home folder?"
date: 2011-06-01
forum: General Help
---

### Post by Vigh on 2011-06-01
Hi my fathers computer running ubuntu 10.10 is failing to boot and I want to access the private data in the home folder in order to recover data onto another disk. How do I go about doing this? As far as I can remember its not encrypted but am still unable to access the data to backup.

Regards

---

### Post by glene77is on 2011-06-01
> **Vigh said:**
> Hi my fathers computer running ubuntu 10.10 is failing to boot and I want to access the private data in the home folder in order to recover data onto another disk. How do I go about doing this? As far as I can remember its not encrypted but am still unable to access the data to backup.

Regards

Vigh,
I have always used a Live-CD.
Usually I make use of : 
(1) Parted-Magic Live-CD 
(2) Puppy Linux 5.25 Live-CD.
Both are simply GREAT for reading all HD file formats and copying out. 

----------------------------------------------------------------------------------------------------------------
Here is my method which should work IF grub is working OK and the OS files are intact. 
Hope someone from the forum will also come to the rescue and help interpret my code. 
Some experience IS required, so always ask for help. 

If you have a grub screen,
... enter 'c' 
... enter my code for Ubuntu 10.10 Bare Bones Bootup as copied from my grub.cfg :
### code
### menuentry "---< -U- >--- Ubuntu 10.10 (hd0,5) Bare-Bones-Bootup .........."
### {
   set root=(hd0,5)
   linux /vmlinuz root=/dev/sda5 ro
   initrd /initrd.img
### }
### endcode.
Change my partition from "5" to yours, assuming that the Ubuntu 11.04 was completed, of course.
------------------------------------------------------------------------------------------------------------------------

HTH   :)

---

### Post by Vigh on 2011-06-01
Thanks for replying, how do I do what you've suggested. I live booted using part magic but its still not displaying the data. How do I take ownership of the folder?

---

### Post by Vigh on 2011-06-02
Solved the problem. Folder was encrypted. Recovered with new tool ecryptfs-recover-private in live-cd.

---

