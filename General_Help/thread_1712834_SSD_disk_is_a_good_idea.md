---
title: "SSD disk is a good idea?"
date: 2011-03-23
forum: General Help
---

### Post by vcrpcant on 2011-03-23
Hi,

I've read in some site that a SSD disk is very good, because it's more faster opening programs.

Is it true?

However, in another site I've seen that those disks only permit a finit number of writes to each sector, so it will "die" someday :confused:

Also, it seems the best are the intel ones.

The price per GB is also a litle bit expensive, bu I'd like to give it a try if there's no drawbacks.

---

### Post by antaios256 on 2011-03-23
while I'm not an expert on SSD i can say that yes they are faster, to write to ram is ridiculously faster than waiting for a HDD to spin up, initialize heads, search for the available track, then write the data. 

as for reliability you would have to check reviews of each specific drive, from each manufacturer. as with any "NVRAM" device the electronics will eventually die. but this is not to say that you wont be able to get 10 years out of it. it just depends on whether you are using the drive in a personal environment or in a corporate central backup/share drive. 

also take into account your environment at home/work/school where ever you plan on using this device. as with any electronics, magnetic interference can cause data-loss. - again this is highly unlikely unless you work in a weld shop where magnetic fields are in abundance.(had my cellphone and all cards in my wallet erased first week on the job in the weld shop)

as for the best out there. take into consideration OC2 technology - tends to have far faster read and write speeds. they make there own drives and also have joint efforts with other manufacturers (maxter and such)

---

### Post by Thund3rstruck on 2011-03-23
> **vcrpcant said:**
> Hi,

I've read in some site that a SSD disk is very good, because it's more faster opening programs.

Is it true?

I have a 250 GB SSD drive in my Win7 Alienware M17X Laptop, which acts as my primary gaming and programming rig and I must admit that it has blown me away. I've been using Falcon Northwest and Alienware rigs for a long time but never with a SSD disk and its performance is vastly superior to standard Sata HDDs (especially RAID-ed HDDs). 

Games have virtually no load times and games that used to have trouble with texture pop-in (e.g. Dragon Age: Origins) run smooth as butter on the SSD disk. 

As for the finite writes; most people think of standard flash media when talking of SSD disks but as I understand it the technology is related but very distantly. 

If my drive only lasts 5-7 years or so I don't care because the performance improvements are worth it.

---

### Post by pl@yer on 2011-03-23
Puppy linux addresses this by having an image file that is expanded to a RAM drive. The image file is only written to when the system is shutdown, to save writes. (at least I think it works that way)

The speed in Puppy is pretty impressive. I wonder if something similar could not be done with any distro.

---

### Post by pqwoerituytrueiwoq on 2011-03-23
> **pl@yer said:**
> Puppy linux addresses this by having an image file that is expanded to a RAM drive. The image file is only written to when the system is shutdown, to save writes. (at least I think it works that way)

The speed in Puppy is pretty impressive. I wonder if something similar could not be done with any distro.
speed achieved this way should exceeded a SSD (except boot speed which uses the HDD/SSD)

---

### Post by cascade9 on 2011-03-23
Yeah, a decent SSD should be a lot faster opening programs (or booting up) than a HDD. Besides the faster transfer sppeds, the acess time (time from issuing the 'get this data' to when the data starts flowing) is a LOT faster on a SSD. 

Yes, there is only as finite number of writes wto an SSD, but its a pretty bug number with the newer SSDs, and with things like TRIM (in the kernel with full support from 2.6.33 onward) the limited number of writes problem is far less of a worry. 

Yeah, they are expensive per GB, but if you only use the SSD for /root, its not really an issue. Though that will be slightly slower, having /home on a HDD means that some program settings will still need to be loaded from the HDD

Intel makes nice SSDs, but they arent the only company that do. Personally, i'd adoind intel SSDs, intel is already far to big a player in the computer world, I really dont want to see intel getting any more laverage over the market with stoage as well to all the other junk they already have. 

> **pl@yer said:**
> Puppy linux addresses this by having an image file that is expanded to a RAM drive. The image file is only written to when the system is shutdown, to save writes. (at least I think it works that way)

The speed in Puppy is pretty impressive. I wonder if something similar could not be done with any distro.

Running puppy with a SSD (using the standard settings anyway) is pointless....No need for a fast drive if you are only writing to the drive on shutdown. ;) 

Yes, you can get other distros to run purely in RAM if you want to hack around.

---

### Post by vcrpcant on 2011-03-23
Thanks everyone! I think I'll give SSD a try :)

Regards

---

### Post by 1clue on 2011-03-23
Careful!

What are you using it for?  A laptop, definitely SSD is worth it just from power savings.  However I have yet to see server hardware using an SSD, and for a good reason.

The SSD still uses the disk interface, SAS or SATA.  That interface has a speed limit.  There are mechanical drives that approach that limit, especially if you're using RAID.

The SSD saves you for the first read.  If you shut down absolutely every time, then maybe an SSD is OK for you.

Standard Linux, including Ubuntu, uses spare RAM as a disk cache.  I have WAY more RAM than I normally need, and the system reports most of that being used as a disk cache if I've been up for awhile.  I don't shut down every time I leave the system, sometimes I am up for months at a time.  The second and subsequent times I read, I'm directly accessing RAM through the swap interface.  There are absolutely zero SSD drives out there that can beat that, and if you have sufficient memory then your system automatically does it.

Yes there is a limit to the number of writes you can make to any part of an SSD.  It's a pretty big number though, so as long as you have lots of free space you will probably be fine.  If you run it packed full then it's quite possible you could "burn a hole" in it.

---

### Post by JRV on 2011-03-23
This is a list of tips to stop unnecessary write to an SSD from the eeeuser.com forum. 
> 
Four Tweaks for Using Linux with Solid State Drives

Published in September 4th, 2008
Posted by Tom in tips

SSDs (solid state drives) are great. They’re shock resistant, consume less power, produce less heat, and have very fast seek times. If you have a computer with an SSD, such as an Eee PC, there are some tweaks you can make to increase performance and extend the life of the disk.

   1. The simplest tweak is to mount volumes using the noatime option. 
      By default Linux will write the last accessed time attribute to files. 
      This can reduce the life of your SSD by causing a lot of writes. 
      The noatime mount option turns this off.

         Open your fstab file:
         sudo gedit /etc/fstab

      Ubuntu uses the relatime option by default. For your SSD partitions (formatted as ext3), 
      replace relatime with noatime in fstab. Reboot for the changes to take effect.

-------------------------------------------------------------------

   2. Using a ramdisk instead of the SSD to store temporary files will speed things up,
      but will cost you a few megabytes of RAM.

         Open your fstab file:
         sudo gedit /etc/fstab

      Add this line to fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

      tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

      Reboot for the changes to take effect. Running df, you should see a new line with /tmp mounted on tmpfs:

      tmpfs 513472 30320 483152 6% /tmp

--------------------------------------------------------------------------------------------------------

   3. Firefox puts its cache in your home partition. 
      By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
      Complete the previous tweak to mount /tmp in RAM, and you can put the cache there as well.

      Open about:config in Firefox. Right click in an open area and create a new string value 
      called browser.cache.disk.parent_directory. Set the value to /tmp.

-------------------------------------------------------------------------------------

   4. An I/O scheduler decides which applications get to write to the disk when. 
      Because SSDs are so different than a spinning hard drive, not all I/O schedulers work well with SSDs.

      The default I/O scheduler in Linux is cfq, completely fair queuing. cfq is works well on hard disks, 
      but I’ve found it to cause problems on my Eee PC’s SSD. While writing a large file to disk, 
      any other application which tries to write hang until the other write finishes.

      The I/O scheduler can be changed on a per-drive basis without rebooting. 
      Run this command to get the current scheduler for a disk and the alternative options:

         cat /sys/block/sda/queue/scheduler

      You’ll probably have four options, the one in brackets is currently being used by the disk 
      specified in the previous command:

      noop anticipatory deadline [cfq]

      Two of these are better suited to SSD drives: noop and deadline. 
      Using one of these in the same situation, the application will still hang but only 
      for a few seconds instead of until the disk is free again. Not great, but much better than cfq.

      Here’s how to change the I/O scheduler of a disk to deadline:

         echo deadline > /sys/block/sda/queue/scheduler

      (Note: the above command needs to be run as root, but sudo does not work with it on my system. 
       Run sudo -i if you have a problem to get a root prompt.)

      You can replace sda with the disk you want to change, and deadline with any of the available schedulers. 
      This change is temporary and will be reset when you reboot.

      If you’re using the deadline scheduler, there’s another option you can change for the SSD. 
      This command is also temporary and also is a per-disk option:

         echo 1 > /sys/block/sda/queue/iosched/fifo_batch

      You can apply the scheduler you want to all your drives by adding a boot parameter in GRUB. 
      The menu.lst file is regenerated whenever the kernel is updated, which would wipe out your change. 
      Instead of this way, I added commands to rc.local to do the same thing.

         Open rc.local:
         sudo gedit /etc/rc.local

      Put any lines you add before the exit 0. I added six lines for my Eee PC, 
      three to change sda (small SSD), sdb (large SSD), and sdc (SD card) to deadline, 
      and three to get the fifo_batch option on each:

         echo deadline > /sys/block/sda/queue/scheduler
         echo deadline > /sys/block/sdb/queue/scheduler
         echo deadline > /sys/block/sdc/queue/scheduler   
         echo 1 > /sys/block/sda/queue/iosched/fifo_batch
         echo 1 > /sys/block/sdb/queue/iosched/fifo_batch
         echo 1 > /sys/block/sdc/queue/iosched/fifo_batch

      Reboot to run the new rc.local file.

      [update] Commenter dondad has pointed out that it’s possible to add boot parameters 
      to menu.lst that won’t be wiped out by an upgrade. Open menu.lst (Remember to make a 
      backup of this file before you edit it):

         sudo gedit /boot/grub/menu.lst

      The kopt line gives the default parameters to boot Linux with. Mine looks like this:

      # kopt=root=UUID=6722605f-677c-4d22-b9ea-e1fb0c7470ee ro

      Don’t uncomment this line. Just add any extra parameters you would like. 
      To change the I/O scheduler, use the elevator option:

      elevator=deadline

      Append that to the end of the kopt line. Save and close menu.lst. 
      Then you need to run update-grub to apply your change to the whole menu:

         sudo update-grub[end update] 

      Want to know how fast your SSD or other storage device is? 
      Using hdparm you can test the read performance of your disk:
  
         sudo hdparm -t /dev/sda

      The 4 GB SSD on my Eee PC 901 gets about 33 MB/s. 
      My desktop PC’s hard drive gets about 78 MB/s. 
      (What hdparm doesn’t show is that the seek time for an SSD is much, much lower than a hard disk.)


------------------------------------------------------------------

Turn off Journaling in EXT4

First thing's first, we can confirm that our ext4 partition is running a journal with

  sudo dumpe2fs /dev/sdaX | grep has_journal

Disabling journaling is rather easy, the only drag is that to make structural changes to a filesystem, 
the filesystem cannot be mounted with read/write privileges. So, run a live cd and hit

  sudo tune2fs -O ^has_journal /dev/sdaX

And it's done. Now when you boot, the change will be noted and the disk will be checked for errors. 
When the system is finally up we can run this again to confirm that in fact ext4 is running without a journal

  sudo dumpe2fs /dev/sdaX | grep has_journal

should now return nothing.

With this quick fix, no more constant IO peaks. I can now watch youtube videos without constant freezes.


---

### Post by 1clue on 2011-03-23
Using tmpfs judiciously can use several **gigabytes** of RAM, not several megabytes.  Consider the cost of RAM compared to the cost of an SSD, they're not that far apart.

Changing your firefox temp dir to /tmp can cause problems.

Instead change it to /tmp/$USER/firefox-tmp instead.  This avoids name collisions with other users.

IMO disabling journaling defeats most of the point in having ext4.

I've been trying to justify an SSD for quite some time now.  It will probably happen at some point, but I still haven't done it.  I'm not an opponent of the idea, but unless you're using a laptop or have a specific read-seldom purpose where first-time reads are critical, chances are you won't gain as much from it as the hard-core proponents claim.

---

