---
title: "gparted &quot;Can't have overlapping partitions&quot; error"
date: 2012-05-15
forum: General Help
---

### Post by shawest on 2012-05-15
Hello Ubuntu,
I currently have my laptop partitioned into a Windows partition and a Linux partition. I want to make my Windows 7 partition bigger so I can install a game on it, and so I'm trying to shrink my Linux computer to free up space.

I'm booting from an Ubuntu CD at the moment and using gparted to try to change my partitions. 

Previously, what I had was roughly
[W____][[L________]]    where W is my Windows partition and L is my Linux partition, which is inside an extended partition
So in order to move space from my Linux partition to my Windows partition, I shrunk L, leaving me with
[W____][U__[L______]] where U is a block of 20 GiB unallocated space, still inside the extended partition that includes my Linux partition.
Now I want to shrink the extended partition to expose the unallocated space, so I can expand my Windows partition into it. Everything up to here works, but this is where I start getting problems. I want something like
[W____][U__][[L______]]
but when I try to do this, I get an error saying "Can't have overlapping partitions." I don't see where the overlap is occurring, though.
My end goal is to have something like
[W______][[L______]]
where I just have a larger Windows and small Linux partition than I started with.

Currently, running 
> fdisk -l
 gives me
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648    77815733    37678043    7  HPFS/NTFS/exFAT
/dev/sda3       229586944   248018943     9216000    7  HPFS/NTFS/exFAT
/dev/sda4        77815806   229586943    75885569    5  Extended
/dev/sda5       118775808   223311871    52268032   83  Linux
/dev/sda6       223313920   229586943     3136512   82  Linux swap / Solaris
So it doesn't look like there is anything overlapping? Unless I'm just missing something....

A screenshot of my gparted is at
[http://web.mit.edu/shawest/Public/Pictures/gpartedScreenshot.png](http://web.mit.edu/shawest/Public/Pictures/gpartedScreenshot.png)

The /dev/sda6 (!) thing looks a little sketchy, since the file system is marked as "unknown" and when I right click it and look at the information, it says "Unable to detect file system!"

I'm not sure if this is related, since I'm not trying to move it or anything, but it is inside the extended partition that I am trying to resize (although it is at the end I am not touching), so I don't know if it is somehow the source of my problem.

I've tried searching the forums, and nothing I was able to find seemed to explain why I'm getting this "Can't have overlapping partitions" error every time I try to shrink my sda4, so I'd really appreciate any help people can give me.

---

### Post by oldfred on 2012-05-15
Is swap encrypted? It will be unknown if it is.

I do not see overlap either but running boot info script does the math and points it out in most cases. Post link from Boot-repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by gordintoronto on 2012-05-15
When you shrink a partition, it shrinks the right end. To add to the Windows partition, you need space from the left end. To do what you want, you would need to backup an entire partition, delete the partition, extend the Windows partition, recreate the (shrunken) deleted partition, restore the contents.

Your second "diagram" should look like:
[W_____][L_____][U__]

Good luck; I hope you have excellent backup.

---

### Post by shawest on 2012-05-15
First off: Thanks for the responses!

gordintoronto:
I believe gparted is moving the partition, not just clearing space to the right. I've been shrinking with the "move/resize" command, and dragging the leftmost side towards the right, and the diagram of the partitions shows the unallocated space to the left of the Linux partition, not the right

oldfred:
I ran boot-repair awhile ago. It fixed sda6, so I can now see that it is linux-swap, although it didn't allow me to resize my Windows partition like I wanted to. The url frm that was
paste.ubuntu.com/989736
I tried to see if I could just restore my computer to its previous state before I started dealing with this repartitioning stuff, but it would not let my Linux partition expand into the last (leftmost) remaining MiB of unallocated space, so since the start location of my Linux partition is now different from what it used to be, booting back into it failed.

I booted back in from the CD and ran boot-repair again, and it still won't let me move my Linux partition back into that leftmost MiB, and I have no idea why. I haven't tried restarting yet to see if I can at least log into it, but even if this does work, it would be good to restore that MiB back into my Linux partition.

EDIT:
Also, the url for my second boot-repair is
paste.ubuntu.com/990046

EDIT again:
Logging back into my Linux partition worked after running boot-repair. Still don't know what's going on with that 1 MiB of unallocated space before my Linux partition, or why I can't move the space I free up from my Linux partition outside of its extended partition, though.

---

### Post by oldfred on 2012-05-15
If you shrink your LInux partition, you then have to move it right, then move the start of the extended partition right so you can then expand the Windows partition.

I might suggest a NTFS shared data partition as I often do suggest. Then you can have data that you use for both Windows and Ubuntu without writing into the Windows partition. For whatever reason many end up with issues if they write too much data into Windows. Best just to set the c: drive partition as read-only in Ubuntu. 

I have my Firefox & Thunderbird profiles in the shared as well as all the photos. Then Firefox, Thunderbird & Picasa are all using the same data and are the same in both systems.

---

### Post by efflandt on 2012-05-16
Something that may be confusing you (and gparted) is that if you look at the output of sudo fdisk -l, your partitions are not in numerical order.  sda3 is **after** sda4 (how did that happen?).  So which partition are you trying to extend?  sda2 is the partition before sda4.

You did not post the full output of sudo fdisk -l, but it looks like sda3 already goes to the end of the drive.  You should have put code tags around the fdisk output to keep its formatting and make it easier to follow columns (**#** in message window instead of quote).

---

### Post by miasmablk on 2012-05-16
perhaps 
```
sudo sfdisk -l
```
will be a bit more informative

---

### Post by Boudreaux on 2012-10-26
I know this post hasn't seen much action since May 15, but it was the first I found while looking for a solution to a similar problem.  I hope that my input is able to help someone else having similar problems.

I am loaning an old dual boot computer to someone who is not Linux savvy (or computer savvy in general).  He loaded up the windows part to 99.9% with multimedia files, and everything has been brutally slow ever since.  I needed to increase the size of my windows partition by taking from somewhere else - the data partition.  (This was easier than trying to explain where things really go when you "save them in fire fox".... no, they aren't really "inside" fire fox, they go to the hard drive.... anyway.)

My initial setup differs from original post in that  I have: 

[W: ntfs]   [[L: ext4] [L: swap]]   [DATA:ntfs]

Resizing Data part was easy, however moving the extended part with my two Linux parts was not working. I essentially followed the same logic described previously: 

> 
[W____][[L________]]    where W is my Windows partition and L is my Linux partition, which is inside an extended partition
So in order to move space from my Linux partition to my Windows partition, I shrunk L, leaving me with
[W____][U__[L______]] where U is a block of 20 GiB unallocated space,  still inside the extended partition that includes my Linux partition.
Now I want to shrink the extended partition to expose the unallocated  space, so I can expand my Windows partition into it. Everything up to  here works, but this is where I start getting problems. I want something  like
[W____][U__][[L______]]
but when I try to do this, I get an error saying "Can't have overlapping  partitions." I don't see where the overlap is occurring, though.
My end goal is to have something like
[W______][[L______]]In order to get the extended partition to give up it's unallocated space, I found that if I change the way that GParted looks at partition alignment, it would work. . . When looking at the dialog box for "resize/move dev/sda2" there is an option to change the alignment from MiB to Cylinder - click to change it and... Voilà!   To resize my sda1 (windows), I had to switch back to MiB.  I am not sure of the logic here, but this trick did eliminate the "overlapping partition" error.

---

### Post by cnolanAU on 2012-11-08
> When looking at the dialog box for "resize/move dev/sda2" there is an option to change the alignment from MiB to Cylinder - click to change it and... Voilà! To resize my sda1 (windows), I had to switch back to MiB.

@Boudreaux, thanks, your solution worked for me when increasing the size of my extended partition by moving the beginning of the partition. To resize the contained logical partition I switched back to MiB alignment.

---

