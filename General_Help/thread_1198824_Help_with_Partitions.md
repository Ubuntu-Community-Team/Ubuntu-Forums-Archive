---
title: "Help with Partitions"
date: 2009-06-27
forum: General Help
---

### Post by romac1991 on 2009-06-27
Okay, so I'm a linux virgin and i was very excited to get my disk in the mail. I installed it, and I guess didn't really understand the bit about drive partitions, but it went ahead smoothly so I figured it was alright. But whenever I tried to download anything it told me I did not have any space on my disk. So I looked all over forums and places and I started trying to mess with the drive partitions on Vista. Vista had 280 GB of the Disk to itself, and it looked like Ubuntu barely had any. So I freed up space from Vista ( I think, I don't know what I'm doing) and I tried to get Ubuntu to work again. It didn't work, so for some reason I thought installing Ubuntu again would make it work, it didn't, so now I have two partitions ( I think ) for Ubuntu on my disk. I just want to get the partitions right so I have enough room to operate Ubuntu, and I want to delete the other Ubuntu I stupidly installed.

This is all very confusing to me, but I'm still excited about getting into Linux. 
I heard the Linux Community was supposed to be great at things like this, so I was hoping I'd find some friendly and helpful people to help me leave Vista behind.
Any help is greatly appreciated, thanks.

oh, and PS, if this has already been answered 100,000 times and its pissing you guys off, just yell at me where to find it. I've searched it quite a few times on here but didn't find exactly what I was looking for.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7529264") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7529264")

---

### Post by finlost on 2009-06-28
How big is your newly created to be Ubuntu partition?

---

### Post by -kg- on 2009-06-28
No problem.

First, go to the link on "How To Partition" in my signature block and read the pages.  This will give you a good grounding on what you're going to do.

You will want to boot to the Live CD to the desktop and launch GPartEd from "System/Administration/Partition Editor" (that's on the top panel at the left with "Applications," "Places," and "System").  GPartEd will scan your disk(s) and then show your disk graphically (you should know this, having read the link and having seen the screen shots).

You will see your Vista partition and whatever Ubuntu partitions that were installed.  You will want to delete any Ubuntu partitions you have (don't forget to "Apply" those operations!).  Check how much free space you have once you have done this.  Personally, I would prefer to have *at the very least* 20 GB of free space (how much you need depends on what you want to do with Linux...if there's a bunch of software you would like to load, you might want a bit more, but if you're storing/accessing stored files, you can access them right from your Vista partition), but I would think a *bare minimum* of 8 GB (and frankly, that's pushing it, IMHO).

If you feel you don't have enough free space, boot back into Vista and, using Vista's Disk Management, try to free a little more space.  If you have trouble, or still can't free enough space, defragment Vista (several times, if possible) and try again.  With a Vista partition of 280 GB, I should think you should be able to squeeze a bit more space, if necessary.

If you have enough space, close GPartEd and launch the installer from the desktop.  When you get to the partitioning part of the installer, select "Install To The Largest Contiguous Free Space" if you just want to do a standard install, or "Manual Partitioning" section if you want to add other partitions, like a separate /home partition, etc., or if you would like to use ext4 formatting in your partitions (default is ext3).

In the case of manually partitioning your drive, you will need at a minimum a / (root) and a swap partition, plus whatever other partitions you wish to make.  You will have to mark each partition's mount point and formatting, as well as the size and position on the disk of the partitions.

---

### Post by romac1991 on 2009-06-28
I believe it's 2.50 gb.

---

### Post by thefunks on 2009-06-28
I'm having a similar problem. I only set aside 8GB for Ubuntu initially and now I want to set aside much more, taking it away from Windows XP.

---

### Post by Polaris96 on 2009-06-28
The bad news about this is that you guys are stuck using parted or (shudder) fdisk.  This is not an area where I'd be comfy giving "cook book" directions.  

As was mentioned before, you need to read the Documentation and How To for both commands.  Better yet, print them out so you can refer to them as you go.

I have never lost data resizing a windows partition.  They say it's possible, though, so you want to bear that in mind before you start.  

If it were me, I would shrink the windows partition and create a new extended/ logical partition from the empty space.  Then, I would assign several of the major directories (maybe /var, /opt, and /home) to the new space using fstab.  That way you only need to resize one partition instead of two.

So far as having two LINUX systems at once:  If you only have two partitions and one is windows, I believe you only have one Linux system.  I'm not saying it's impossible, but I've never seen two OS's share a partition.  You almost certainly overwrote the origianl Linux install when you reinstalled.

Oh yeah, one other thing:  If you want to see what the Kernel thinks you have for disks open a terminal and type:

cat /proc/partitions

---

### Post by romac1991 on 2009-06-28
this is what came up in terminal, but i don't know what it means



   8        0  312571224 sda
   8        1   12289693 sda1
   8        2  295041757 sda2
   8        3          1 sda3
   8        5    2441848 sda5
   8        6     176683 sda6
 179        0      15680 mmcblk0
 179        1      15651 mmcblk0p1

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by romac1991 on 2009-06-28
alright well i'm reading the information from your signature, and it's kind of confusing but ill finish it

i do have a question though about moving partitions
this is how my gparted reads

/dev/sda1          fat32              Recovery            11.72 Gib
/dev/sda2          ntfs                Vista 64             281.37 Gib
unallocated       unallocated                              2.50 Gib
/dev/sda3          extended                                  2.50 Gib
      /dev/sda5    ext3           /                             2.33 Gib
      /dev/sda6    linux-swap                               172.54 Mib


okay so from what i understand i have to move my first /dev/ over?
but that seems like it is named something that i don't want to mess with.
I am reading that material, but i can really use some pointed help here...

---

### Post by romac1991 on 2009-06-28
Alright...
Well this has certainly lost its appeal very quickly. There's a lot to read and do and it's kind of confusing and I don't think i can get the help I'll need to set this up. 
I guess I'll just pick it up a while from now when I feel like wasting days on this.

---

### Post by presence1960 on 2009-06-28
it is suggested that you read and fully acquaint yourself with what it is you are going to do before you actually do it. Installing & configuring a new OS is not the same as recovering Windows from a recovery partition or recovery CD/DVD. Those have all your drivers and configure your partitions for you automatically. If you have ever installed windows from a windows install CD/DVD (not a recovery one) then you know the difference. Putting a new OS on your machine is no small task if you have never done it before. That's why you need to study . here are a few links for you:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a free pdf Ubuntu pocket Guide that has a great how to section on the install process (step by step)

I am sorry you feel that way, but it seems to you that this will take days because you were totally unprepared for doing this because you didn't find out what you needed to do and how to do it. Like any other major task planning is critical.

---

### Post by -kg- on 2009-06-28
> **romac1991 said:**
> this is what came up in terminal, but i don't know what it means



   8        0  312571224 sda
   8        1   12289693 sda1
   8        2  295041757 sda2
   8        3          1 sda3
   8        5    2441848 sda5
   8        6     176683 sda6
 179        0      15680 mmcblk0
 179        1      15651 mmcblk0p1

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

When you come back to it, you can see in the above that the screenshots didn't post.  That's because you can't link to an image that is on your computer...you have to upload it.

Try the above using the "Attachments" function (the paperclip image at the top, next to the "Smilies" drop-down.  That will allow you to upload your images to your message.

By reading your partition list, I can see that you really don't have enough room to install ubuntu.  You have a 2.5 GB Extended partition that contains your Ubuntu partitions and 2.5 GB of unallocated space outside of the Extended partition.  Altogether that's 5 GB of space that you would be able to allocate to your Ubuntu installation...not really enough.

You really need to be able to shrink your Vista partition to free up some more space.  It is highly advisable that you shrink your Vista partition with Vista's partition manager rather than GPartEd.  While GPartEd *will* handle the job, there have been some problems reported where Vista was rendered unbootable or unusable after using it.

Let me boot into Vista, and I'll try and give you step-by-step on doing it.  While you may not need it, someone else reading this thread might.

Oh, and thefunks; I'm pretty sure that GPartEd will handle XP partition operations fine.  **_If I'm not mistaken,_** XP has no issues with them...it's only Vista that has the problems.

I could be mistaken, though, so do some research on it.  I've never had to deal with these issues myself...I've always either had multiple hard drives or have installed my Windows OSes on separate partitions in the first place, with other partitions to hold my software and data files, usually with free space already present, to boot.

---

### Post by presence1960 on 2009-06-28
you are not mistaken -kg-, XP reacts fine when resized with gparted.

---

### Post by -kg- on 2009-06-28
Ok, I am now in Vista, [IMG]http://www.freesmileys.org/smileys/smiley-angry023.gif[/IMG] and thanks for the confirmation, Presence.

Now, in order to shrink your Vista partition, you will need to boot into Vista (well DUH!) and launch "Control Panel/Administrative Tools/Computer Management," and then launch "Disk Management" which is under "Storage" on the left sidebar.

You will then be presented with a Window similar (but not the same) as GPartEd's window.  You will see your Recovery partition and then your Vista partition which should be labeled as "C:".

Right-click on your "C:" drive and select "Shrink Volume."  You will then be presented with a window which will show you how much the partition can be shrunk.  Personally, I would take all it will give me.  For instance, when I do this with *my* "C:" drive, it says I have 73 GB in my C: partition and can shrink it around 22 GB.

Of course, if you can shrink it significantly smaller, you might want to leave more room, since files on Windows partitions will fragment significantly faster with less room.  All in all, I would shrink it about 20 GB.  That should give you room in which to install and run Ubuntu with ease.

One other consideration:  Of course, the information you gave me doesn't tell me how full your Vista partition is.  If you have a lot of files (pictures, videos, music files, games, etc.) in it, you may have it nearly full and won't be able to shrink it very much.

If you have a $#l+load of files in your Vista partition, you're going to have to decide what goes and what stays.  You can always put pictures and music on CD or DVD and store them that way.  You might want to consider loading any videos on DVD and play them from the drive.  If it's a whole bunch of games, you might want to consider installing another hard drive.

Anyway, once you've shrunk your Vista partition, you will want to boot back onto the Live CD, launch GPartEd as above, and delete all the Ubuntu partitions (/dev/sda5 ext3 / 2.33 Gib and /dev/sda6 linux-swap 172.54 Mib) that were created, including the Extended partition (/dev/sda3 extended 2.50 Gib).  This will free up all that hard drive space and give you the 2.5 GB of space that's taken up by all that, plus the 2.5 GB of unallocated space, plus the space you free up by shrinking the Vista partition.

If you were able to free up 20 GB by shrinking your Vista partition, then 25 GB of unallocated space should be more than enough for a good installation of Ubuntu.  Just select "Use Largest Contiguous Free Space" in the partitioning phase of the installation, and you should be good to go.

---

