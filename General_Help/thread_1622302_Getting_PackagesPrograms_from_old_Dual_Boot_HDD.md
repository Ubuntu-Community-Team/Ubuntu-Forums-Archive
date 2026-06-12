---
title: "Getting Packages/Programs from old Dual Boot HDD"
date: 2010-11-15
forum: General Help
---

### Post by Darren_Thomas on 2010-11-15
We had an old PC sat in the corner running Ubuntu 10.04 acting as a basic HTTP server, but it has pretty much died. (Was dual booting with windows XP)

I have installed Ubuntu (same version) on a newer PC.

I need to copy over all the packages/programs that were setup on the old PC.

I have put the old HDD in the new PC, but i am not seeing the Ubuntu file structure, only as if i was viewing it in windows.  e.g. i can see the ubuntu folder with root.disk file etc.

Can anyone help with this?

Thanks

Darren

---

### Post by Darren_Thomas on 2010-11-15
Bump

---

### Post by SeijiSensei on 2010-11-15
If the computer died, but the disk drive is still intact, you might be able to put it in a new machine and boot it from there.  Linux is pretty flexible about stuff like this.

You can see which packages were added to the system by looking in the old drive's /var/cache/apt/archives directory.  You'll have to review the contents of /etc/apache2 to see where the website files are located.  Probably some are in /var/www, but you might have others in custom directories if you're using multiple virtual hosts.

Do the websites use scripts?  How about dynamic content that might be stored in a MySQL or PostgreSQL database?  If so, you'll need the databases as well.

I'd really try the first option if you haven't done so yet.  You might be pleasantly surprised to find everything comes up without a hitch.

---

### Post by galvatron408 on 2010-11-15
if you connected your old drive to your new computer and your old drive still works, all you have to do is mount the drive.

open up your terminal, and run "sudo fdisk /dev/sdb" (sda would be your first drive and sdb should be your second drive). At the prompt, type "p" and press enter. This will print your partition table. Take a note of your linux partition.

my partition table looks like this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       23897   181704708    7  HPFS/NTFS
/dev/sda3           23898       38913   120615989+   5  Extended
/dev/sda5           23898       38297   115667968+  83  Linux
/dev/sda6           38298       38913     4947988+  82  Linux swap / Solaris

If this was your drive, you would be interested in /dev/sda5. So, now that you identified it, just do the following... (first type "q" and press enter to quit)

sudo mkdir -p /mnt/olddrive
sudo mount /dev/sda5 /mnt/olddrive
cd /mnt/olddrive and everything should be there
(remember, yours is most likely going to be sdb)

---

### Post by Darren_Thomas on 2010-11-16
Thanks for the suggestions guys...

I originally tried booting from the old HDD, it starts to boot, but then (i presume as it tries to load the gfx driver) i lose the output to the monitor.  But i can load the recovery option and get to the command line.

On the new PC with a fresh install of Ubuntu i can see the contents of the new drive, so i presume its already mounted ok?

I have recently found out (via google) that with the dual boot install on the old PC, it has installed using Wibi.

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

> It is not a [virtual machine]("http://en.wikipedia.org/wiki/Virtual_machine"), but creates a stand-alone installation within a [loopmounted device]("http://en.wikipedia.org/wiki/Loop_device"), also known as a [disk image]("http://en.wikipedia.org/wiki/Disk_image"), like [Topologilinux]("http://en.wikipedia.org/wiki/Topologilinux") does. It is not a [Linux distribution]("http://en.wikipedia.org/wiki/Linux_distribution") of its own, but rather an installer for [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29").[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#cite_note-WubiFAQ-0")
 While Wubi does not install Ubuntu directly to its own [partition]("http://en.wikipedia.org/wiki/Disk_partitioning")  this can also be accomplished by using LVPM, the Loopmounted Virtual  Partition Manager, to transfer the Wubi-generated Ubuntu installation to  a dedicated real partition, including a bootable [USB keydrive]("http://en.wikipedia.org/wiki/USB_keydrive").[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#cite_note-WubiFAQ-0")  The advantage of this setup is that users can test the operating system  and install the drivers before they install it to a dedicated partition  (and avoid booting and functioning risks).
 Wubi adds an entry to the Windows boot menu which allows the user to  run Linux. Ubuntu is installed within a file in the Windows file system  (c:\ubuntu\disks\root.disk), as opposed to being installed within its  own [partition]("http://en.wikipedia.org/wiki/Disk_partitioning"). This file is seen by Linux as a real hard disk.[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#cite_note-WubiFAQ-0") Wubi also creates a [swap file]("http://en.wikipedia.org/wiki/Swap_file") in the Windows file system (c:\ubuntu\disks\swap.disk), in addition to the [memory]("http://en.wikipedia.org/wiki/Random_Access_Memory") of the host machine. This file is seen by Ubuntu as additional [RAM]("http://en.wikipedia.org/wiki/Random_Access_Memory").

**I have subsequently found that the old PC is not working as it has run out of disk space.  I missed this fact as the HDD still has 12GB left on it, but as the install by Wubi is on a virtual partition, it is the partition that has run out of room** :oops:

So.  I think i need to get hold of a LVPM to transfer the installation to the new HDD/PC.

Any suggestions on this would be a great help. As Ubuntu is very new to me and a LVPM is even newer [-o<

Thanks

Darren

---

