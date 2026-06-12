---
title: "Hard drive woes."
date: 2010-01-17
forum: General Help
---

### Post by tom.swartz07 on 2010-01-17
Alrighty. 

So, I'm by no means a "beginner" to Linux, but for some reason, I'm having the HARDEST time trying to copy my hard drive. 

A few weeks ago, I was unable to boot my computer because bad blocks in my drive 'appeared' over my current and most used partition, for 9.10. I discovered there were 101 bad blocks on the drive, so I called western digital and had them send me a new one. In the meantime, running fsck on the drive managed to sort out the bad blocks for the time being. 

The replacement drive arrived on Friday, and since then, I've been trying to clone my current drive to the replacement. Using Clonezilla, I kept getting the error "bad partition table on /dev/sdb". Alright, I tried a bit-by-bit transfer using dd, but for some reason, the transfer fails on the last partition, leaving the replacement drive unbootable. 

What do you think I should do? Does it sound likethet sent me another faulty drive, or am I just doing something stupid? I've copied my drive before, but ive never had these problems- i just popped in Clonezilla and away it went. 

I'm really leary about this drive, I have many important files for school and TONS of music. The school files, I can back up, and the music could be shuffled to another external drive, but I reallydo no want to go through all of the time and effort to move it to a new drive that may already be failing. 

Does anyone know what I should do? Is there some way to test the 'health' of the drive before I spend hours rebuilding my filesystem?


I'm at the point now where I'm going to just install fresh ubuntu on the drive and copy partitions and files over from there, but again, if the drive fails in another 3 months, I'm going to go nuts!

---

### Post by Crafty Kisses on 2010-01-17
For the new drive you might want to look into **[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")**. Now for the decision of you keeping the drive is really up to you. Now again I'm not sure if the drive is bad, from the sounds of it, it doesn't sound like the actual drive is bad but if you are having doubts and WD is willing to send you another one, go ahead and send it off. That is of course if you think there is something actually wrong with the drive and it's defective.

---

### Post by john newbuntu on 2010-01-17
You might also want to use smartmontools to check the new drive.  I am not sure if WD provides you with a tool (in Linux) to check disk diagnostics.  If they do, then try that.

---

### Post by tom.swartz07 on 2010-01-17
its not really necessary that i look for a Linux-only tool, I have windows 7 on the drive also.


My biggest problem is that im quickly running out of cds. haha.
I had one cd-rw, but it got scratched and is now unusable.

So far, Ive been looking into running any future tools...


Today is the day that I finally copy this freaking drive! haha

---

