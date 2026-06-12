---
title: "Raid 5 set up- not being recognized on Ubuntu"
date: 2012-05-30
forum: General Help
---

### Post by ltanaka on 2012-05-30
Hello, I am trying to transfer files from a Raid 5 set up that was set up to be used on an IMAC to another hard drive.

The problem right now is that I can not get it to mount.

The logo shows up on the side, but I get this message when I click on it:
"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

What do I do?
I would like to get the external hard drive mounted without having to reformat or lose any information on it.
I am brand new to ubuntu. 

Thank you!

---

### Post by ltanaka on 2012-05-31
No one have any help? Links to places that talk about it? or any wisdom to share?

---

### Post by steeldriver on 2012-05-31
I looked at your thread yesterday  but I don't understand what you're doing

What exactly are you trying to mount? afaik you can't generally just mount the underlying block device of a raid array, especially not just one of the array members (with the possible exception of RAID1)

Is the original array Linux or some kind of fake raid / hw raid?

---

