---
title: "Increasing Ubuntu Partition Size"
date: 2006-04-11
forum: General Help
---

### Post by vxj9219 on 2006-04-11
I have 76 GB of hard disk space on my Dell Inspiron 6000 and I am dual booting XP Pro and Breezy. WHen I first created the partition, I allocated 30 GB for Ubuntu. Now I want to increase the size of the Ubuntu partition without doing a clean install again. Is there any way to literally take some hard disk space from XP and give it to Ubuntu? Is there a tool similar to partition magic for ubuntu that I must use? How does it work?

---

### Post by Herman on 2006-04-12
The latest [GParted livecd]("http://gparted.sourceforge.net/livecd.php") would be the software of choice for that job. You can download the .iso for that and burn it to a CD. You can boot from that CD, and it has a very nice easy GUI to use, it probably isn't really necessary to explain too much about that, it's very intuitive.

What does seem to get a few people stuck though are some facts about Linux partitions. Linux partitions are not as easy to move around as other types you might be used to. The beginning point of a Linux partition is kind of fixed. You can resize them from the end, but if you want to move the point they begin from you can only do so by copying and pasting the whole partition.
When you do that, it will receive a new partition number, which means if you want to leave it like that you'll need to re-install the boot loader or at least edit it from [command line]("http://www.users.bigpond.net.au/hermanzone/p15.htm"), and also edit /etc/fstab with the new partition numbers.
You can avoid the need to do those things by copying the partion and pasting it one extra time, after deleting the original partition, so your Linux partition gets its old partition number back again. I don't know what this technique is really called but I call it 'partition leapfrog'.
You normally need to resize one or both of your partitions to a much smaller size and temporarily delete the swap area to give yourself some room to manouvre before you can do very much.
I here are a couple of links to previous threads on this subject, please ask again if there is anything you still feel unsure about after reading these:
[http://ubuntuforums.org/showthread.php?t=144699&highlight=partition+leapfrog]("http://ubuntuforums.org/showthread.php?t=144699&highlight=partition+leapfrog")
[http://www.ubuntuforums.org/showthread.php?t=125644&highlight=partition+leapfrog]("http://www.ubuntuforums.org/showthread.php?t=125644&highlight=partition+leapfrog")
I'll be lurking around if needed, I'm pretty sure you'll find it very simple once you give it a try though. Regards, (Herman) :D

---

### Post by vxj9219 on 2006-04-12
Thanks Herman. I installed gparted (before seeing your reply), split off 8 GB from ntfs and formatted it as ext3 (don't know why I did that, is it necessary?). Now I want to merge this with /dev/sda3. Here is the screenshot of my gparted, just to give you an idea of what exactly I want to do.

[IMG]http://static.flickr.com/53/127341045_3b9f6f5760.jpg?v=0[/IMG]



--Update--
Still haven't figured it out.](*,)

---

### Post by Herman on 2006-04-12
I think you'll need to use a live cd to do this because you can't copy and paste a partition using the partition you are copying and pasting from.
Looking at that screen cap makes it a lot easier to see what you want to do, thanks. :D
I would maybe do something like this,
1)  Shrink sda3 as small as  you can and copy and paste it right to the very end of the hard drive. It will likely receive the new number sda4.
 (By, the < 'beginning' I mean to the < left < , and  'end' > I mean to the > right > ).
2)  Delete both sda3 and sda7, you won't need those anymore. (I hope you will have everything [backed up first]("http://www.users.bigpond.net.au/hermanzone/p13.htm") of course, just in case).
3) Move your swap area down to the end of sda5 and shrink the extended partition it's in too.
4) Copy sda4 and paste it after the end of your swap area, it will get the old partition number back again, sda3, like it had before.
5) Resize the new sda3 as much as you need to fill up the free space if you want.
6) You have the choice to just leave sda4 there for a back-up copy, it won't take up very much room, when you really need the extra room, then delete sda4. I would recommend keeping it for now. (That's what I do anyway).

Looking at it you'll only gain a little bit of extra room in Ubuntu that way, unless you do delete sda4, but you  could resize Windows and sda5 smaller maybe first if you think it's a good idea, good luck with it, from Herman. :D

---

