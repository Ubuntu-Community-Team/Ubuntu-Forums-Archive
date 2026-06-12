---
title: "ext4 shrinking; gparted verbose"
date: 2010-01-21
forum: General Help
---

### Post by Hirager on 2010-01-21
I am in process of reverting my data from ext4 (second partition) to ext3 (fourth partition; / in between). I do it so: 1. Copy files to ext3. 2. Delete files from ext4. 3. Resize partitions. All because of little spare free space. Now I got stuck. I have read a few topics about problems with very long processing time of such operations. There was mentioned info about progress of the work. Something about how many cylinders got moved, etc. Is any way possible to see the progress of gparted opened in window-only mode (not by terminal)? I ask because I get very annoyed, not knowing how much is done. I assume, that unless I cancel, the process won't get stuck or damaged, right? If someone could estimate time of shrinking partition by 25 GB (middle-right of 500 GB disk), I would be very thankful. And one last thing. Can you recommend me a partition manager which will get the work done faster than gparted (I am ready to take the risk)?

---

### Post by tommcd on 2010-01-21
On a large hard drive this can take a few hours. When I grew my /data partition from ~180GB to 200GB after deleting a partition before it the process took a few hours.  How long has it been for you?
How are you using Gparted? Are you running it from the Ubuntu live CD or the Gparted live CD? None of the partitions you are working on should be mounted when you do this. I am pretty sure Gparted would warn you of this if they were mounted though. So if it carried out the operation then the partitions were probably not mounted. The Ubuntu live CD does not automatically mount any partitions when you boot from it.

I like using a Parted Magic live CD for partitioning tasks:
[http://partedmagic.com/](http://partedmagic.com/)
If I remember correctly, Parted Magic does show the progress and the estimated time to completion of it's operations.

And welcome to the Ubuntu forums!

---

### Post by Hirager on 2010-01-21
Well, now it is something like ninth hour of work. What I am most curious about, is if I can see how much progress has been done. I hope it is finishing now (9 hours for moving right border 25 GB to the left seems not to be so time-consuming as moving beginning of partition.) I hope it's not case like guy's from gparted forum (he waited for a month and got nothing, USB 1 TB drive though). I use Ubuntu Karmic x64 LiveCD. Of course no partitions mounted. Not sure about "round to cylinders". I think it IS checked somewhere...

---

### Post by tommcd on 2010-01-21
Nine hours does seem a bit long.
In you first post you said:
> I am in process of reverting my data from ext4 (second partition) to ext3 (fourth partition; / in between). I do it so: 1. Copy files to ext3. 2. Delete files from ext4. 3. Resize partitions. 
So are you trying to grow the fourth partition into the second partition with the third partition (root) in between them? I did not think you could do that. Usually the partitions have to be contiguous to resize one partition to take up the space left by deleting another partition.

---

### Post by Hirager on 2010-01-21
Exactly the process goes like this:
1. Move data from ext4 (left) to ext3 (right).
2. Shrink ext4.
3. Move / ext3 (10 GB) left.
4. Grow /home ext3 left.
5. Repeat this till all necessary data is moved.
The thing is, that I have programmed all 3 steps to be done at once, so when shrinking is done, I will have to wait still more. Pity I didn't read about this slowness before I started it. Probably I would have had it done already with different software.
I am reading gparted forum topics for general knowledge and found out that I stacked another stupid thing on top of this mess. I shrink to extent, where is no more free space left. Probably all I am waiting for now is just packing the data...

---

### Post by tommcd on 2010-01-21
> **Hirager said:**
> 
5. Repeat this till all necessary data is moved. ...
The thing is, that I have programmed all 3 steps to be done at once, so when shrinking is done, I will have to wait still more. ...
This is probably why it is taking so long. Gparted is repartitioning your hard drive 3 times. Each time it starts over from scratch.
When I repartitioned my drive I deleted the partition I did not want. Then I grew my data partition into the unallocated space that was created after deleting the partition next to it. I did this in just one step. This took more than 3 hours if I remember correctly. So 9 hours for 3 resizing operations may not be longer than expected.

---

### Post by Hirager on 2010-01-21
Well, gparted at least informs which step it is currently doing. I am still in shrinking step. Hopefully, next partitions have free space inside them, so it will be much faster. Now when I read through many topics about it, I am sure, that now gparted tries to fit the bits in. When this mad tetris is done, it will be much relief for me. Now I am writing at gparted forum about this issue. I want them to include warning not to leave no space when shrinking.

---

### Post by tommcd on 2010-01-22
So did Gparted ever finish resizing your partitions?

---

