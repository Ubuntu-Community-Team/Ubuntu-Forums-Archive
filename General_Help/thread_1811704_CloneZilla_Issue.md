---
title: "CloneZilla Issue"
date: 2011-07-25
forum: General Help
---

### Post by timZZ on 2011-07-25
Hi,

This is an odd place to seek help about CloneZilla but since I am unable to post an item on the official forums I have seeked out a place where people are helpful.

The issue I am having is moderately simple to explain.  I am using CloneZilla to image the harddrive in it's current state for restore later, however, during testing to see if this system would work I am running into an interesting problem.

When imaging CloneZilla is grabbing the correct hard drive size but on the restore it is dropping a large number of MB and thus end result is CloneZilla refuses to restore the image because the target hard drive appears too small.

I.e. 

55 GB ==> Image *works and image is created and verified*
44 GB <== Image *Fails because the hard drive appears too small*

In this example both the 55 GB the image was taken from and the 44 GB the image is trying to be restored too is the same hard drive.

This issue is on both the current CloneZilla download and apart of the GParted package.

Anyone else run into this problem?

---

### Post by Mark Phelps on 2011-07-25
Clonezilla will NOT allow you to restore a partition to a drive or space that is smaller than the one you imaged -- even if the image file itself is smaller (which it generally is).

So basically, you can't "restore" a 55GB image to a 44GB space.

---

### Post by timZZ on 2011-07-25
Mark - Correct and I agree with you.

The problem I am having is ... Computer A was cloned and 15 minutes after the cloning process I attempted to prove the system works by restoring the clone back on Computer A.

So we are not talking a different hard drive or different computer. I am talking that when it takes an image it is seeing the hard drive as 55 GB, which is confirmed but when I attempt to restore the image the hard drive is incorrectly being shown as 44 GB.

So to re-cap -> There is a disagreement between the imaging process and the restoring process in regards to the actual hard drives size and it is unfortunate that the later see's the hard drive to be smaller.

So it is not so much I am trying to purposely restore a larger image to the machine it is that I believe the restore process is incorrectly sizing the hard drive.  I have tried it on multiple IBM Thinkpad's with all the same results and this might be a good indicator I am doing something wrong.

---

### Post by Mark Phelps on 2011-07-25
timZZ:  Sorry, I misunderstood your situation.  We get the "how do I restore to a smaller drive" question here all the time -- and I thought that was your situation.

Have no explanation as to why Clonezilla should see two different sizes for the drive -- one for backup, the other for restore.

I know that there are differences between what drive sellers report and what drives actually allow --but that is due to different size measurement schemes.  That's not enough to explain what you're seeing.

Have you tried looking at the drive info using GParted or the Disk Utility -- and seeing what they report?

---

### Post by kevjonesin on 2011-07-25
Hi,

   I also tried a similar experiment about two weeks ago using the Clonezilla that came bundled in the Parted Magic CD*.

   I had the same issue until I used gparted to remove the original partition, hence reverting to unformatted space, on the drive I was attempting to re-install the Clonezilla image to. 
   Was able to install image after that.


   I assume it was like trying to put a jar in a jar with the exact same dimensions. Doesn't work. They have to differ by at least the thickness of the walls.



*I've really come to appreciate the Parted Magic CD. Free to download and burn. Has a few handy apps in the "extras" menu, like grub utilities and "PLOP Bootloader", which can be quickly accessed  before launching it into a utility optimized live linux OS (that can run disc-less in RAM!).

---

### Post by timZZ on 2011-07-26
kevjonesin - I will try that shortly!

The other item that maybe different from others is my image is being stored on a server using the SSH option not locally on a USB drive.  I have noticed that 99% of the examples show people using a USB drive to restore the image.

---

