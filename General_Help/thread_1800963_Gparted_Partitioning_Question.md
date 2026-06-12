---
title: "Gparted Partitioning Question"
date: 2011-07-09
forum: General Help
---

### Post by BeastMode on 2011-07-09
Hello, All!

Once again, I find myself in a position to go full time, on at least one computer in my home, to Ubuntu.  On a side note, I'm not overly thrilled with the new Unity, but I'm certain that before 11.10 comes about, most of what irritates me about it will be fixed.

My problem is now not really involving Ubuntu, but to commit this computer to full time Ubuntu, I've decided to remove the Windows Partition completely.  (I can access what I need through VirtualBox.  I don't think anyone really ever gets COMPLETELY away from Windows, but that's a different subject.)

Anyway, here is a picture of my partition table.

[IMG]http://websitedesignoforlando.com/Screenshot.png[/IMG]

What I'd like to do is completely remove the windows partitions, which are obviously the first two on here, and then extend my Ubuntu partition to the left to fill in what will then become unallocated space.  However, when I try this, I don't have the option to grow my Ubuntu partition to the left.  

Thus, my question.  How DO I do that?  I know I've heard of it being done before, and I can't be the first to have run into this situation.

Can someone help me?

---

### Post by aeronutt on 2011-07-09
A bit hard to tell from that picture, but the partition your changing can't be mounted. Most likely, you'll want to run Gparted from liveCD (or another linux partition if you have more than one).

---

### Post by BeastMode on 2011-07-09
> **aeronutt said:**
> A bit hard to tell from that picture, but the partition your changing can't be mounted. Most likely, you'll want to run Gparted from liveCD (or another linux partition if you have more than one).

Whoops.  I meant to point this out in advance and forgot to.  

Yes, I DO have to mount it from the Live CD.  I just wanted to post it here from Ubuntu and not from the Live CD, so I just used Gparted from my install to show the table.

---

### Post by oldfred on 2011-07-09
From LiveCD you can delete the windows partitions. You may want to backup before hand just in case you decide to go back. And/or make recovery DVDs.

Your Ubuntu install is inside the extended partition. While not very standard to not have primary partitions other than the extended you can move extended all the way left. I prefer not to move partitions left as it has to copy & verify all data. Slightly more risk but do able.

I would prefer to create a separate /home in a new partition and move all your /home into that partition. I have several links if you are interested in that option. 

You seem to have several swaps?

---

### Post by BeastMode on 2011-07-09
> **oldfred said:**
> From LiveCD you can delete the windows partitions. You may want to backup before hand just in case you decide to go back. And/or make recovery DVDs.

Your Ubuntu install is inside the extended partition. While not very standard to not have primary partitions other than the extended you can move extended all the way left. I prefer not to move partitions left as it has to copy & verify all data. Slightly more risk but do able.

I would prefer to create a separate /home in a new partition and move all your /home into that partition. I have several links if you are interested in that option. 

You seem to have several swaps?

Thanks for your response.

I'll answer the simple question first.  I think the "swaps" are my recovery partition that Windows 7 puts on, but everything else is simply what Ubuntu did when it installed.

As for the left/right issue and the home folder move, I'm not really sure what you're talking about, but let me put it this way.  I suppose I don't really care where my partitions lie, as long as that unallocated space (which I know has to be formatted to an ext extension) that will exist once I kill the Windows Partitions is usable inside my Ubuntu partition.

---

### Post by wildmanne39 on 2011-07-09
> **BeastMode said:**
> Thanks for your response.

I'll answer the simple question first.  I think the "swaps" are my recovery partition that Windows 7 puts on, but everything else is simply what Ubuntu did when it installed.

As for the left/right issue and the home folder move, I'm not really sure what you're talking about, but let me put it this way.  I suppose I don't really care where my partitions lie, as long as that unallocated space (which I know has to be formatted to an ext extension) that will exist once I kill the Windows Partitions is usable inside my Ubuntu partition.Hi, first the swap is a linux partition and you only need one. Here is a guide for resizing partitions you should have a look at it before you begin and oldfred is one of the best to listen too, so if I say anything that goes against what he says please follow his directions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Blasphemist on 2011-07-09
I can't speak to the not having any primary partitions other than the extended as my very similar situation was when I shrunk windows instead of deleting it. If you highlight the extended partition from the list, you can re-size it to include the space to the left that available from deleting the windows partitions. With that done you could create new partitions in that space as I did. I now have a bunch of distro's installed. In my screen shot you can see I created 5 new partitions in that space. I did leave ubuntu, sda5, in the same place. The warning in another post on not moving a partition may be accurate. I really just didn't care where it was and knew I had enough free space to do what I wanted so I didn't have to research moving natty's partition. I recommend creating something like what I did so you can be a distro experimenter. Especially with the gnome shell coming up that is a good idea.

---

### Post by BeastMode on 2011-07-10
> **Blasphemist said:**
> I can't speak to the not having any primary partitions other than the extended as my very similar situation was when I shrunk windows instead of deleting it. If you highlight the extended partition from the list, you can re-size it to include the space to the left that available from deleting the windows partitions. With that done you could create new partitions in that space as I did. I now have a bunch of distro's installed. In my screen shot you can see I created 5 new partitions in that space. I did leave ubuntu, sda5, in the same place. The warning in another post on not moving a partition may be accurate. I really just didn't care where it was and knew I had enough free space to do what I wanted so I didn't have to research moving natty's partition. I recommend creating something like what I did so you can be a distro experimenter. Especially with the gnome shell coming up that is a good idea.


I certainly can appreciate what you're saying about experimenting with distros, but I'd really like to be able to have much of this free space for my ubuntu portion.

Is moving the /home folder really the best way to do this, and what happens WHEN I do that?

---

### Post by oldfred on 2011-07-10
If you prefer to upgrade in place a separate /home is less essential. But you still should be backing it up.

If you want to be able to easily install the new version of Ubuntu a separate /home makes it easier as then you can overwrite the system partition (reformat & reuse) and just mount the existing /home in the new install (without reformating) and you preserve all your user settings and data. User settings are most of the things you customize, but you may have a few system settings in /etc and might want a list of installed apps before reinstalling if you do that type.

If you want the separate /home I have these links. They are all the same except they use different commands to copy the data from your current /home to your new one. I reviewed them all and used the one that made more sense to me in how it was explained.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Blasphemist on 2011-07-10
When you expand the extended partition to the left you'll have new available space. You can create a partition in that space and not touch any of the existing logical partitions in the extended partition. You can then follow this instruction to cause it to show up as a folder in your file system. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I have a ntfs partition that I use to store music, pictures, video, downloads, etc. that are available to me from all linux distro's and from windows. You could use that space the same way. If you don't need it available from windows since you've removed that, don't use ntfs as I did and psychocat did, use EXT4 and change her commands to reflect that.

---

### Post by BeastMode on 2011-07-11
I marked this thread as solved, and though I'm sure I got some great advice from some of you, I don't think I did it quite anyone's way.

Here's what I did, and I'm really sure it's "tom-ae-to" / "tom-a-to" here, but this worked very well for me, and even served as a good backup for my install.

In short, I used good old GPARTED herself to do what I needed to do.  I first copied the old "sda5" from gparted to my external hard drive.  Once I did that, and rebooted back to the live CD, I then pretty much wiped my entire hard drive clean by deleting all of the partitions, except for my Windows Recovery partition, sda3.  Then, I created an extended partition with the unallocated space, pasted my backup from the hard drive into that extended partition, created a swap partition in there as well, reinstalled GRUB, and everything was GOOD TO GO.  I had to update the GRUB to get it to stop seeing Windows 7 at startup, but that was it.

Gparted is quite the handy tool!

---

