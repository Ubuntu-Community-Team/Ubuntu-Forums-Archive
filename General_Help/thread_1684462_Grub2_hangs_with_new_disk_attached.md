---
title: "Grub2 hangs with new disk attached"
date: 2011-02-09
forum: General Help
---

### Post by _2009 on 2011-02-09
Hi,

I originally posted this in the server platform forum, but after having no joy there after a fortnight I thought I'd cast my net a bit wider.

I've searched the web for the answer to this but can't find a solution that seems to fit my scenario.

I have a ubuntu 9.10 server that has and IDE drive with LVM on top for the server OS, "systemvolumegroup" that contains root and swap lv's. It also has 4 sata drives in a software raid 5 array with LVM on top that has a "data_vg" containing a data lv. I've just added a Highpoint rr2720 card for some extra SATA ports. My intention is to create a second software raid array.

I have the rr272x_1x driver installed and working:

Code:

> cat /proc/scsi/rr272x_1x/8
RocketRAID 272x_1x controller driver v1.0 (Jan 18 2011 21:49:20)

Controller 1: RocketRAID 272x SATA Controller
------------------------------------------------

Logical devices
------------------------------------------------

Here's the problem:

    Attach a new disk to the rr2720 and don't initialize it - server boots fine.
    Attach a new disk to the rr2720, initialize it and set up as JBOD - grub2 hangs on "grub loading."
    Remove disk from rr2720 and then attach the disk when the server is up - server freezes


I was hoping that option 3 would enable me to run update-grub just in case that was the problem.

I hope someone can help, I'm banging my head against the wall with this!

Please let me know if you need any more information.

---

