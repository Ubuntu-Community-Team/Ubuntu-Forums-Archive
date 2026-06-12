---
title: "Floppy Access Issues"
date: 2010-08-07
forum: General Help
---

### Post by and003 on 2010-08-07
I am having trouble trying to use a 1.44 MB floppy drive on my computer. I have tried to mount the drive on my computer, but all I get is the following message:

Unable to mount location
No media in the drive

I have visited the threads of those on other forums posted by people who had this issue and have found a clue. One post mentioned that if I were to type "id" in a terminal, the floppy would be recognized as "25(floppy)". I tried that, but "25(floppy)" didn't come up.

Also, when I tried using KFloppy to format a floppy disk, I got the following message:

Internal error: device not clearly defined

However, when I used the 'lsmod' and "cat /etc/fstab" commands, they strangely seem to recognize that my computer has a floppy.

I am attaching documentation to this post for analysis. This documentation includes information about a failed attempt to format a disk using Disk Utility. Also, I am using Ubuntu 10.04 (Lucid Lynx) as my operating system.

---

### Post by and003 on 2010-08-14
Today I reinstalled Ubuntu 10.04 and tried to mount the floppy. When I  tried to mount the floppy during the tryout phase with the CD, I  received the following messages:

Unable to mount location
Error  mounting:
mount: you must specify the filesystem type

Unable  to mount location
Error mounting:
mount: /dev/fd0 is not a valid  block device

When I finished installing Ubuntu 10.04 and tried to  mount the floppy drive again, I was confronted with this following  message:

Unable to mount Floppy Disk
Error mounting: mount  exited with exit code 1: helper failed with:
mount: I could not  determine the filesystem type, and none was specified

Also, when I  tried to use the Disk Utility to format a floppy, I received this  message:

Error creating partition table: helper exited with exit  code 1: In part_create_partition_table: device_file=/dev/fd0, scheme=0
got  it
got disk
committed to disk
BLKRRPART ioctl failed for  /dev/fd0: Invalid argument

This is the current situation with my  Ubuntu installation so far. Does anyone have ideas?

---

### Post by and003 on 2010-08-21
I found a step-by-step solution to my floppy access issues at the following URL:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

### Post by labinnsw on 2011-04-16
> **and003 said:**
> I found a step-by-step solution to my floppy access issues at the following URL:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

Unfortunately it is hidden, which makes it a bit of a hassle when all you have time for is the answer. So here it is:

> Problem solved, thanks to peter b!!!

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.

Thank you, peter b!!!

PS: Is this a bug???

Thanks for providing the link.

---

### Post by murphyac on 2011-04-30
The method cited by labinsw worked beautifully for me until a few days ago.  I had udisks and udisks-doc pinned to version 1.0.1-1build1 in Lucid Lynx (10.04) and they survived a number of upgrades.  Then I got the, in retrospect, wacky idea to upgrade to Maverick Meerkat (10.1).  There went my floppy access.  Maverick changed my udisks and udisks-doc to 1.0.1+git20100614.  Now I am unable to mount the floppy with the error message "no media in drive", even with a floppy in the drive that was previously read in Lucid.
Synaptic allows me to mark the packages for reinstallation, but the "Force version" option is grayed (blacked) out.  Any suggestions?  Should I just wait until I upgrade to Natty Narwhal (11.04) and then try to regain my floppy access afterward?
Thanks in advance for any help.
Angela Murphy

---

### Post by murphyac on 2011-04-30
Found a workaround in another thread:

             Make sure you have a floppy disk in the drive
             Open a terminal window.
              Type:  udisks --mount /dev/fd0

This mounts the floppy drive and it can then be used.  There must be a disk in the drive, however, otherwise an error message "Mount failed, fd0 is not a valid block device" appears.

Hope this helps others who update to 10.1 from 10.04.
Angela Murphy

---

### Post by crossleyd on 2011-11-12
murphyac:

Your solution worked for me. Only one that did. Thanks. Ubuntu 11.10.

Danny Crossley.

p.s. It's stopped working again!

---

### Post by vandamme on 2012-01-04
udisks --mount /dev/fd0 works once in a while (10.10). I think I'll just throw out all my floppies and be done with 'em.

---

### Post by vanquishedangel on 2012-03-21
> **vandamme said:**
> udisks --mount /dev/fd0 works once in a while (10.10). I think I'll just throw out all my floppies and be done with 'em.

I have tried all of this in Lubuntu 64 bit 11.10 and all failed, but I was able to use the command line to format the disk tho.

I need to update my bios is why but i made a discovery and opened the bios file with wine, it saved to a folder (c:\swsetup\SP54788) so i went to that folder (/home/USERNAME/.wine/drive_c/swsetup/SP54788) and found an .iso file (/home/shawn/.wine/drive_c/swsetup/SP54788/BIOS CD) moved it to a directory in linux and used xfburn to burn it to a disk. then rebooted with the disk in the drive and hit f10 setup, in the first menu it has a option to use a rom, i choose it and selected cdrom, it updated the bios. There was an option for usb there to.

I have an hp dc5750

---

