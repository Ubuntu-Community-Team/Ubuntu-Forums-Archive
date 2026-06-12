---
title: "Questions RE: dd"
date: 2012-03-07
forum: General Help
---

### Post by Ghost_Mazal on 2012-03-07
Lo Guys ,

I am searching for a clone solution for my server's hdd.
Clonezilla fails as the destination HDD is 10 gig smaller than the
source. 947gig to 932gig. I only have 250gig data on the server , but alas , that stupid limitation of clonezilla that can't see that there is enough space.

So the next thing I want to try is dd.
I know that when you do for example dd if=/dev/sda of=/dev/sdb it will copy the whole disk to the destination block by block , even the unused space. 
Or I could do dd if=/dev/sda of=/media/sdb/sda.img to clone it to an image. This is the 2 uses I know of.

Question 1: - Will dd also fail because the destination is 932gig  like clonezilla does ?

Question 2: - Copying the whole 947gig , even if only 250gig is used will take extremely long. Is there a way so that only the used space is cloned ?

Question 3: - If I use option 2 , cloning to an image , will dd still do the whole 947gig ? And then again as in question 1 will it fail cos the destination is 932gig , or will it adjust ?

Question 4: - Any other better cloning software that can actually clone only used space and see there is enough space available on the destination for the 250gig of data ?

This cloning of my drive has become such a big headache.

Any help appreciated , thanx.

---

### Post by The Cog on 2012-03-07
It is my understanding that using dd to clone the larger drive to the smaller one will work except for the end that cannot of course be copied. It is likely that the clone will seem to work perfectly, but that it will fail in use when it gets full enough that it wants to use the non-existent part of the filesystem.

I suggest that you use something like gparted to resize the source disk's partition until it can be cloned perfectly onto the smaller disk.

---

### Post by spiky001 on 2012-03-07
Hi

I had the same problem BUT on a much smaller scale As mentioned already I used gparted to resize the partition then used used dd if=/dev/xxx of=/home/user,
I also piped it with gzip as someone in the forums helped with
dd if=/dev/xxx bs=4096 | gzip > /home/user/file.img.gz
Yes it will take a long time

---

### Post by Ghost_Mazal on 2012-03-07
My problem is , I tried the gparted resize route , but it didn't work. It resized the partition , but upon reboot it throwed my server in a looping boot and couldn't start up again. Everyone on the world of google says "Resize with gparted" , but in my case that just doesn't work. :(
 
I eventually got the server going again , and it showed the new space as 876gig in Ubuntu and in gparted (that's what I resized the source to) , BUT when I go to clonezilla it still sees 942gig on sda1 :confused:
 
That's why I am looking at other options. I am simply amazed that there is no proper linux software that can clone reading just the data and see the empty space on the destination is enough. Amazed.

---

### Post by dcstar on 2012-03-08
> **Ghost_Mazal said:**
> 
..........
That's why I am looking at other options. I am simply amazed that there is no proper linux software that can clone reading just the data and see the empty space on the destination is enough. Amazed.

That's because you obviously have no idea about how filesystems are structured. Linux supports a multitude of filesystems, and any process that tries to resize one has to then adjust the structure of the filesystem to take that into account - and it will need that tool to support the particular filesystem it is working on. **dd** is not that tool.

**gparted** already has tools to resize (most) partitions correctly when copying, all you had to do was use it and then follow all the instructions in the various HOWTOs on editing /etc/fstab and fixing the UUIDs that change when a partition is resized and your system would have probably worked ok.

---

### Post by Ghost_Mazal on 2012-03-08
> **dcstar said:**
> That's because you obviously have no idea about how filesystems are structured. Linux supports a multitude of filesystems, and any process that tries to resize one has to then adjust the structure of the filesystem to take that into account - and it will need that tool to support the particular filesystem it is working on. **dd** is not that tool.
 
**gparted** already has tools to resize (most) partitions correctly when copying, all you had to do was use it and then follow all the instructions in the various HOWTOs on editing /etc/fstab and fixing the UUIDs that change when a partition is resized and your system would have probably worked ok.
 
Gparted broke my system completely like I already said.
 
Anyway , I found a way that works using rsync. I can now clone a drive to any other size drive with rsync. Clone will run super fast every day and none of this partition resizing is necessary at all.
 
Tested is successfully with a Xubuntu install. Moving over to the server to test that now.
Will be so glad if the rsync way works on server as well , but I see no reason why it shouldn't.

---

