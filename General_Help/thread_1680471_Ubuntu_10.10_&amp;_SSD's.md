---
title: "Ubuntu 10.10 &amp; SSD's"
date: 2011-02-02
forum: General Help
---

### Post by simolokid4 on 2011-02-02
Hi ubuntuforums,

I've been reading up on what to do and what not to do when setting up an ssd. So far I discovered not to use ext3 as the ssd's life would... be cut down very much. So I'm thinking ext4?

I simply want the basic functionality of the thing without it breaking in the first year or so.. ;)
So, when setting up ubuntu 64 bit 10.10 and an ssd (OCZ SSD Vertex2 60gb's), on a ext4 filesystem. Will I get native support or will I have to tweak things in order to let it all work ?

Thanks a lot in advance,

Kind regards,

Simolokid

---

### Post by HHBones on 2011-02-02
ext4 is, pretty much, ext3 with journaling. If you care about it, it would NOT be a good idea, and it's actually worse than ext3. I'd say use FAT or ext2. However, the difference in lifetime should be small, especially if you've made sure that Ubuntu won't make tons of writes.

Open Terminal, and type this:

sudo gedit /etc/fstab

and replace relatime with noatime. This will stop Ubuntu from writing 'last write time' to disk, which will extend your life.

Then, add this line to /etc/fstab:

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

This will create a file system on your RAM for temporary files, saving you
precious writes.

If you're a Firefox user, Firefox will store your cache in your home folder.
Remember- WRITES ARE BAD. Reboot your system and run df in Terminal after 
making those changes. Make sure the output looks like this:

tmpfs 513472 30320 483152 6% /tmp

Then, 
Open *about:config* in Firefox. Right click in an open area and create a new string value called *browser.cache.disk.parent_directory*. Set the value to */tmp*.


Finally, the storage device scheduler by default, cfq- Completely Fair Queueing (ironic, huh?). Let's fix that! This is copy-pasta from an article about it:


An I/O scheduler decides which applications get to write to the disk  when. Because SSDs are so different than a spinning hard drive, not all  I/O schedulers work well with SSDs.The default I/O scheduler in Linux is cfq, completely fair queuing.  cfq is works well on hard disks, but I’ve found it to cause problems on  my Eee PC’s SSD. While writing a large file to disk, any other  application which tries to write hang until the other write finishes.The I/O scheduler can be changed on a per-drive basis without  rebooting. Run this command to get the current scheduler for a disk and  the alternative options: 



cat /sys/block/sda/queue/scheduler



You’ll probably have four options, the one in brackets is currently being used by the disk specified in the previous command:



noop anticipatory deadline [cfq]



Two of these are better suited to SSD drives: noop and deadline.  Using one of these in the same situation, the application will still  hang but only for a few seconds instead of until the disk is free again.  Not great, but much better than cfq.


Here’s how to change the I/O scheduler of a disk to deadline:  



echo deadline > /sys/block/sda/queue/scheduler


(Note: the above command needs to be run as root, but *sudo* does not work with it on my system. Run *sudo -i* if you have a problem to get a root prompt.)


You can replace *sda* with the disk you want to change, and *deadline* with any of the available schedulers. This change is temporary and will be reset when you reboot.


If you’re using the deadline scheduler, there’s another option you  can change for the SSD in Ubuntu. This command is also temporary and  also is a per-disk option:   



echo 1 > /sys/block/sda/queue/iosched/fifo_batch



You can apply the scheduler you want to all your drives by adding a  boot parameter in GRUB. The menu.lst file is regenerated whenever the  kernel is updated, which would wipe out your change. Instead of this  way, I added commands to rc.local to do the same thing.


Open rc.local:  



sudo gedit /etc/rc.local



Put any lines you add before the *exit 0*. I added six lines  for my Eee PC, three to change sda (small SSD), sdb (large SSD), and sdc  (SD card) to deadline, and three to get the fifo_batch option on each: 


echo deadline > /sys/block/sda/queue/scheduler

echo deadline > /sys/block/sdb/queue/scheduler

echo deadline > /sys/block/sdc/queue/scheduler

echo 1 > /sys/block/sda/queue/iosched/fifo_batch

echo 1 > /sys/block/sdb/queue/iosched/fifo_batch

echo 1 > /sys/block/sdc/queue/iosched/fifo_batch



Reboot to run the new rc.local file.


It’s possible to add boot parameters to menu.lst that won’t be wiped  out by an upgrade. Open menu.lst (Remember to make a backup of this file  before you edit it):  



sudo gedit /boot/grub/menu.lst



The kopt line gives the default parameters to boot Linux with. Mine looks like this: 



# kopt=root=UUID=6722605f-677c-4d22-b9ea-e1fb0c7470ee ro



Don’t uncomment this line. Just add any extra parameters you would like. To change the I/O scheduler, use the elevator option: 



elevator=deadline



Append that to the end of the kopt line. Save and close menu.lst.  Then you need to run update-grub to apply your change to the whole menu: 



sudo update-grub

And you're done.

That's about it.

---

### Post by tednix on 2011-02-02
I've been thinking about building a new computer and so this thread caught my eye.  After seeing these instructions I think that I would stay away from a SSD for now and hope that future kernels provide optimized support.

---

### Post by simolokid4 on 2011-02-02
So, when I do all that tweaking in order to make my ssd last a bit longer, it will work without problems?

(In theory ofc )

Also; HHBones: which filesys. would u recommend? FAT or ext2?

Guess I'll go to the shop tomorrow then =)

---

### Post by sdennie on 2011-02-02
The reason people would recommend not using ext3 is because of the journaling.  ext4 is also journaled so there is no reason to choose it over ext3.  Having said that, modern big name SSDs (Intel, OCZ, etc) have enough write cycles and spare blocks that even with a default journal commit time of 5 seconds, an SSD will probably last longer than a traditional hard drive under "normal" usage.

To put it into perspective, I'd had a 40GB Intel SSD for about a year now.  I've done about a dozen OS installs on it, and have used ext4 for each install.  I compile code on it, run VMs on it, etc.  The SSD has a SMART data attribute (accessible via System->Administration->Disk Utility) called Endurance Remaining that tells you how close the disk is to becoming unwritable.  After a year, that Endurance rating has dropped 1%.  At this rate, the disk is likely to last longer than me.

---

### Post by MooPi on 2011-02-02
Thanks for the info sdennie, as I just purchased a Crucial SSD and have installed Ubuntu to it. My interest is in the use of trim to optimize the disk or is it already a function in the kernel. The info online is confusing.

---

### Post by cariyawa on 2011-02-03
Follow this guide and it is very concise.

[http://www.vanstormbroek.nl/blog/?p=58]("http://www.vanstormbroek.nl/blog/?p=58")

---

### Post by piquat on 2011-02-03
The best place I've found for info on setting this up is the manufacturers own forums.

They have a Linux/Apple forum:

[http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-OCZ-SSD-Support-for-Linux-and-Apple-OSX](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-OCZ-SSD-Support-for-Linux-and-Apple-OSX)

And I don't see much about partition alignment in this thread either which is another thing that should be given some attention.  Top sticky in that forum is a great guide for that.  In fact, most of the stickies there are pretty useful.

Good luck!

---

### Post by mastablasta on 2011-02-03
> **HHBones said:**
>  I'd say use FAT 
 i wouldn't use fat... FAT32 has a limit on the size so 6GB video or ISO or something like that will be a no go on that set up.
 
otherwise it is still fine except it throws data all over the place.

---

### Post by tredegar on 2011-02-03
There was much discussion on the eeeuser.com forums about the SSD the early EEE's had, and "Wearing it out".
[This]("http://wiki.eeeuser.com/ssd_write_limit") EEE wiki page has a sensible analysis of the issues, and the bottom line is "don't worry about it".

Sine I read that (? three years ago) I have been running ext3, *without* the **noatime** option, on my heavily-used 4GB EEE701 for years now - and (as predicted) I have had no  problems at all.

So, my advice would be to go ahead and use whatever filesystem you like.

---

