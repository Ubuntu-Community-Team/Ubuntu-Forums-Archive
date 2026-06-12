---
title: "Changing the structue of the file system"
date: 2009-06-30
forum: General Help
---

### Post by HuBaghdadi on 2009-06-30
Hey,
I have this file system structure:

/dev/sda2          /
/dev/sda3          /media/sda3
/dev/sda4          /media/sda4

How to make sda3 and sda4 part of the / file system?
I mean I want to have only 
/dev/sda2          /
Any ideas?
Thanks.

---

### Post by thespirit3 on 2009-06-30
If I understand you correctly, you want to drop the /media/disk mounts and mount them elsewhere?

In which case, in /etc/fstab you could simply do:-
 
/dev/sda2 /  ext4  defaults  0  0 
/dev/sda3 /data/music  ext4  defaults  0  0
/dev/sda3 /data/video  ext4  defaults  0  0 

assuming you wanted them mounted in /data/music etc and the FS type is ext4.  Of course, you'd need to make sure these mount points / directories exist, and you'll want to make sure you have permissions to write to them.

Although, I think ubuntu uses labels or UUID's by default now (in case number of partitions change) - you can check UUID's by the following:-

ls -l /dev/disk/by-uuid/

replace the '/dev/sda2' (for example) with tha above UUID and this should still work.  However, the 'classic' old fashioned way should also work, albeit less flexible.

I think the GUI should honour fstab and not screw with anything ...

---

### Post by HuBaghdadi on 2009-06-30
My hard disk is partioned as this:

Device      Directory      Size
/dev/sda2   /              45 GB
/dev/sda3   /media/sda3    45 GB  
/dev/sda4   /media/sda4    45 GB 

What I want to do is to merge sda3 and sda4 into sda2 so the sda2 will be 135 GB

---

### Post by tgalati4 on 2009-06-30
That would be difficult in Linux.  Get yourself a 1 TB drive and copy everything to a large single parition.

Mark Twain said:  Put everything in a basket.  And watch that basket!

---

### Post by michy99 on 2009-06-30
1. Back up everything in sda3 and sda4 to another drive,

2. Boot from a Live CD and open Gparted. System->Administration->Partition Editor. Or use a Gparted Live CD.

3. Delete sda3 and sda4.

4. Expand sda2 to use the free space.

5. Delete sda3 and sda4 lines from /etc/fstab.

---

### Post by HuBaghdadi on 2009-07-01
There is no "Delete" option in the GParted tool, just unmout option.
Yes, I logged as a super user.
Ubuntu 8.10

---

### Post by sedawk on 2009-07-01
Here is my recommendation:

mount sda2 or sda3 to /home (/etc/fstab)
or create a big partition sda2=sda2+sda3 and
mount it as /home.
E.g. when you fill /home (by error) to 100% your
OS doesn't stop working. But if you fill up / to
100% you might be in trouble...

(When mounting sda2 to /home it will hide your old data in old /home.
 so make sure to copy everything from /home to /media/sda2 first, e.g
 by using "sudo rsync -av /home/ /media/sda2/")

In case you can create a backup of /home (e.g. to a USB stick formatted
with ext2/ext3) and you can reinstall the computer without losing
any data, I recommend this:

/dev/sda1: /        16 GB for Ubuntu
/dev/sda2: /altos   ("alternate os") 16 GB (free) to test new Ubuntu or
                    Fedora or ...
/dev/sda3: /home    the big disk for your data

(If you want a 4th partition,e.g sda4 for swap I highly recommend
to use an extended partition for sda4 and put real stuff to
the logical partitions sda5,sda6,sda7,sda8. So swap would be
sda5, not sda4).

( It is not a default feature of Ubuntu, but some linux distros
use the LVM (Logical Volume Manager) by default. With this tool it would
have been easy to solve your problem, e.g. resizing a logical volume
(in your case for /) and adding space (partitions) to it
are some of the important features of LVM. )

---

