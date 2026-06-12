---
title: "Trying to dual boot...."
date: 2009-07-07
forum: General Help
---

### Post by Gusx1 on 2009-07-07
Hi, i'm currently trying to get Vista and Ubuntu run, i currently have Vista installed and i am burning all the anime etc on my computer to clear up space. But everytime i do it seems my partition space keeps going down. I want at least 30 gigabytes for Ubuntu... Heres my problem

[http://img126.imageshack.us/img126/3442/fsdfdsfsdfs.jpg](http://img126.imageshack.us/img126/3442/fsdfdsfsdfs.jpg)

---

### Post by sedawk on 2009-07-07
I think the shrink operation is not freeing up space because
there are still used blocks at the end of the disk.
So you need a "shrink tool" that can relocate blocks or
you have to defrag the disk using windows defrag tool.

(The sysinternals suite contains some nice tools to check the
 disk usage of your disk (gui) and it has a tool "contig" to
 defrag single files. So instead of defragging the whole disk
 you can look for the file(s) that are still at the end
 of the disk and if that are not many different ones you 
 try to run "contig" on those files instead of a full defrag.)

It's a pity that there is no good defrag util for Linux doing
defrags of FAT32 and NTFS. Missing it a lot ;-)

---

### Post by Gusx1 on 2009-07-07
After even more deleting i get less space... I need a really good solution to this so i can get Ubuntu installed. If anyone can help it's much appreciated..
[http://img6.imageshack.us/img6/436/fsfsdfsdfsdfsdf.jpg](http://img6.imageshack.us/img6/436/fsfsdfsdfsdfsdf.jpg)

Also to the poster above, i tried defrag, etc. I use tuneup utilities as well as windows stuff to clear a lot of junk off of my PC.

---

### Post by kandieyman on 2009-07-07
You may already know this, but the real problem is that Vista by default creates an NTFS partition flag that is new in Vista (Page File). The amount by which you can shrink the partition will seem arbitrary regardless of what you do and will always be small relative to the size of the actual partition. I personally recommend a fresh install of Vista after partitioning for Ubuntu. That is what I did, and I am glad that I did.

---

### Post by Dustin2128 on 2009-07-07
actually, 30GB would be quite simple. Just stick the disc in your computer and pick the option that installs wubi. You can have partitions up to 30GB and it's incredibly simple. It sorta works like an application actually.

---

### Post by akakingess on 2009-07-07
> **kandieyman said:**
> you may already know this, but the real problem is that vista by default creates an ntfs partition flag that is new in vista (page file). The amount by which you can shrink the partition will seem arbitrary regardless of what you do and will always be small relative to the size of the actual partition. I personally recommend a fresh install of vista after partitioning for ubuntu. That is what i did, and i am glad that i did.


+1

---

### Post by sdlynx on 2009-07-07
I suggest using the partition editor (GParted) from the Ubuntu live disc.  I've had no problems messing with partitions using that.

---

### Post by raymondh on 2009-07-07
> **Gusx1 said:**
> Hi, i'm currently trying to get Vista and Ubuntu run, i currently have Vista installed and i am burning all the anime etc on my computer to clear up space. But everytime i do it seems my partition space keeps going down. I want at least 30 gigabytes for Ubuntu... Heres my problem

[http://img126.imageshack.us/img126/3442/fsdfdsfsdfs.jpg](http://img126.imageshack.us/img126/3442/fsdfdsfsdfs.jpg)

Hi,

Just a couple of thoughts.

There is a 4 partition (whether primary or extended) limit per HD.  You already have 4.  Where do you plan to put Ubuntu, which will require it's own partition?

You have some decisons to make whther you want to give up the EISA and/or the 2.5GB.  

One option is to install thru WUBI.  Just remember that since it is installed inside windows, when Vista crashes, so does your Ubuntu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Another option is to delete the 2.5GB (which will bring the primary partitions to 3), shrink C:drive and install Ubuntu (EXTENDED partition) in the freed-up space which will be the 4th partition.

There's a 3rd option ... which is to erase everything and re-install Vista and it's recovery partition (D:drive) in front of the drive.  That way, you'll have 2 more partitions to play with ... 1 for ubuntu and another for a SHARED storage accessible to both Vista and Ubuntu.  YOU WILL NEED A ORIGINAL INSTALL DISC FOR THIS OPTION, not the recover disc supplied by the manufacturer.

Links on NTFS and Vista resizing:

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://gparted-forum.surf4.info/viewtopic.php?id=2892](http://gparted-forum.surf4.info/viewtopic.php?id=2892)  (post no. 1)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Good luck.

---

### Post by kandieyman on 2009-07-07
No! Do not do what sdlynx is recommending. gParted cannot correctly resize NTFS with that flag. It will corrupt the partition.

---

### Post by sdlynx on 2009-07-07
> **kandieyman said:**
> No! Do not do what sdlynx is recommending. gParted cannot correctly resize NTFS with that flag. It will corrupt the partition.

really? it worked for me...
sorry bout that then

---

### Post by TMAN 1 on 2009-07-07
I had this problem.........  Just a thought,but what size HDD do you have? I had a 160 gig HDD in my puter and found that trying to run Vista and Ubuntu on it,there wasn't enough room.Any Windows just takes up too much space,so I installed a 320gig HDD and have had no problems like yours since then.  Perhaps give this a try.

---

### Post by raymondh on 2009-07-07
> **kandieyman said:**
> No! Do not do what sdlynx is recommending. gParted cannot correctly resize NTFS with that flag. It will corrupt the partition.

It may or may not corrupt the partition.  If it does, you will need the orginal installation disc (windows) to repair.  Given the 50-50 chance, I have always used the Vista Management tool to shrink a Vista partition....after defrag.... and in small steps.

   	*The size of the available space can be restricted by the amount of space currently allocated to on the hard drive for the virtual memory page file, System Restore max size, and hibernation files. The location of the files on the hard drive plays a big part here because these files are marked as unmovable, and Disk Management is unable to relocate them. As such, if these unmovable files are located in the middle of the total amount of free space on the disk, then only the amount of free space on the other side (to the right) of these files will actually be available for the new partition. This will result in you showing that you have x amount of free space, but not being able to use it for your partition.* 

Copied from [http://www.vistax64.com/tutorials/95398-disk-management-shrink-partition.html](http://www.vistax64.com/tutorials/95398-disk-management-shrink-partition.html)

---

### Post by kandieyman on 2009-07-07
I didn't mean to offend in any way, and it is possible that some people will not have that problem, but I have seen it too often to expect it will not happen. Besides, if you do not mind running the risk of corrupting the partition, then just do a fresh install like I recommended before.

---

### Post by sdlynx on 2009-07-07
> **kandieyman said:**
> I didn't mean to offend in any way, and it is possible that some people will not have that problem, but I have seen it too often to expect it will not happen. Besides, if you do not mind running the risk of corrupting the partition, then just do a fresh install like I recommended before.

haha well I guess I lucked out

---

### Post by akakingess on 2009-07-07
Please remind me to follow your posts raymondhenson!  Sorry, that was my way of thanking you for your assistance and excellent information/resources. Thanks for all of your time and willingness to share your knowledge.

---

