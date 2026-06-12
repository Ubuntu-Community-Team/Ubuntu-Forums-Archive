---
title: "Building a new box"
date: 2009-10-24
forum: General Help
---

### Post by Nugar on 2009-10-24
Hi all,

First of all, I apologize if this is not the right forum for this question.

Soon (Dec, most probably) I'll be building a new box. I've been using Ubuntu full time on my home PC since maybe Jan of this year.

Now I'm planning going 64 bit and formatting all my disks as ext*. Right now, I'm running my main disk as ext3 and two other disks that have some old information and are formatted as ntfs. I also left them like that since I used to dual boot, but now I haven't boot into XP in a lot of time. Any windows software I need, I use through VMWare.

So what I plan to do is using a 320GB sata drive and install Ubuntu there again, formatting it as ext4, adding a 1.5tb drive, formatting it as ext4 too and transferring all my current files there so I can reformat a couple of smaller drives too.

Now here are my questions:

[LIST]
[*]How does this sound? Sound? (pardon the pun)
[*]How is 64-bit Ubuntu working as compared to 32 bit? I need to use it since I plan to use up to 16gb RAM
[*]How is it working with large disks?
[/LIST]
I think that's it for now. 

Thanks in advance for any comments,

---

### Post by blueridgedog on 2009-10-24
[*]How does this sound? Sound? (pardon the pun)

Sounds good.

[*]How is 64-bit Ubuntu working as compared to 32 bit? I need to use it since I plan to use up to 16gb RAM

Take a look:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Ubuntu recommends 64 at this point.

[*]How is it working with large disks?

The disks you describe are no longer considered large (isn't life funny?).  I believe Ubuntu will support any disk you can buy.  

Personally I have still with ext3 though as I have had no problems with it.

---

### Post by Nugar on 2009-10-24
Thanks blueridgedog, I'll start my reading in that direction.

Cheers,

---

### Post by mdlueck on 2009-10-24
I prefer ext3 on a smallish /boot partition, and xfs for all other partitions.

A while ago, grub was having a problem booting from an xfs drive, thus the separate /boot partition ala ext3. Might be working now, just I do not care to get burned again.

---

### Post by shaggy999 on 2009-10-24
64-bit has been working pretty awesomely for me with 9.04. I don't have any problems with the exception of there is no 64-bit build of zsnes and I had to find a hacked up package, but once I found that it works flawlessly.

Flash works
Google Earth works
Compiz works
Sound works
Virtualbox works
Dosbox works
zsnes works (after finding a seperate package)

The only thing I would suggest is to use ext2 or ext3 for your /boot partition and for your seperate 1.5 TB drive you might want to look into using LVM and putting an ext4 partition on top of that so you can easily grow or shrink partitions in the future as needed, or add drives easily to the storage pool without reformatting.

---

### Post by Nugar on 2009-10-25
I'm taking notes, guys... keep 'em coming!

With all this information, when I build this I can have a good start, and start thinking into another way of doing things, quite different from my old windows world.

---

