---
title: "Need help Ubuntu won't boot."
date: 2010-04-17
forum: General Help
---

### Post by ShadeFinale on 2010-04-17
This morning, ubuntu was working fine and everything, but when I had come home and tried to boot up my computer, there were some problems with ubuntu's built in disk checking. At first, it said this:

Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.

I pressed CONTROL-D, and this came up.

/dev/sda5 contains a file system with errors, check forced.
Filesystem checks are in progress (ESC to cancel):
/dev/sda5: Duplicate or bad block in use!--------------------}
/dev/sda5: Multiply-claimed block(s) in inode 151205: 700445
/dev/sda5: Multiply-claimed block(s) in inode 151262: 700445
/dev/sda5: (There are 2 inodes containing multiply-claimed blocks.)

/dev/sda5: File /usr/bin/debconf0communicate (inode #151205, mod time Fri Oct 2 14:15:53 2009)
  has 1 multiply-claimed block(s), shared with 1 file(s):
/dev/sda5:     /usr/lib/libformw.so.5.7 (inode #151262, mod time Mon Oct 12 08:12:40 2009
/dev/sda5:

/dev/sda5: UNEXPECTED INCONSISTENCYL RUN fsck MANUALLY. (i.e., without -a or -p options)
mountall: fsck / [947] terminated with status 4
mountall: Filesystem has errors: /

init: mountall main process (943) terminated with status 3

Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.

After that had come up, I decided to put in my ubuntu install cd, and booted off of the live cd option to look at the partitions because my windows install does not see the ubuntu partitions even before the problem ever arose.

What I had found was not very assuring, as my 33gb partition for ubuntu's files was marked unpartitioned, and was split between sda5 as 2 partitions, a 33gb one now marked as an extended partition, and one which totaled over 1 million GB, with negative byte count or something similar, along with a swap file also having such an unbelievably high unpartitioned space.

I need help to restore my ubuntu partition's data to working condition, as the last backup I made was around 5 days ago and I had stored new information on my hard drive that hadn't been backed up in that time frame.

I will be willing to re-install ubuntu and will be able to make an image of my current hard drive if needed in order to back it up, but I would rather not in hopes that the problem can be fixed before I have to reformat and repartition everything.

Any help would be greatly appreciated.

---

### Post by john newbuntu on 2010-04-17
Boot from an Ubuntu liveCD and run:
sudo e2fsck -C0 -p -f -v /dev/sda5

If it gives any errors, run:
sudo e2fsck -f -y -v /dev/sda5

List the outputs you get in both cases.

---

### Post by friedshan on 2010-04-17
You can just type fsck and say y to all the stuff u seem ok :lolflag:

I mean type fsck in the screen where those errors appear ;)

---

### Post by ShadeFinale on 2010-04-17
Thanks, I'll try that and get back to you as soon as I can, it's late here so I'll probably try it first thing in the morning.

---

### Post by ShadeFinale on 2010-04-17
Thank you so much for the help, it has been fixed and I now have an oppertunity to back-up my recent work.

The first command you asked me to try did not do anything but redisplay the previous errors, but the 2nd said that it copied over the multipy-claimed blocks and now I can boot.

---

