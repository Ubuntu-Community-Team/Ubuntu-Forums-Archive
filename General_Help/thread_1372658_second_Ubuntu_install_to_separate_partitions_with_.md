---
title: "second Ubuntu install to separate partitions with GRUB2"
date: 2010-01-04
forum: General Help
---

### Post by wyatt roberts on 2010-01-04
I have 2 ubuntu installs, 9.10,- one on each of 2 hard drives. I like the first one best because it's the most mature - I just started the second with a new hard drive. I should mention that the system is identical but for two eSata drives, both of which boot nicely. I have multiple partitions on the second drive. Here's what I want to do:

I have tarred the system and Home partitions from the original (mature) install (disk1).
I want to untar them to separate partitions on Disk 2 (the new, larger one)

I then want to have Grub 2 on the new disk 2give me the option of choosing the new install or the original (mature) install from disk 1 (untarred on disk 2)

My understanding is that I can either update-grub OR grub-mkconfig, with the latter given preference based on:

"grub-mkconfig - /usr/sbin/grub-mkconfig - a script for making a new  /boot/grub/grub.cfg file.

As far as I know this command is supposed to be used in preference to update-grub in Karmic Koala and later versions of Ubuntu. Earlier version of Ubuntu didn't seem to contain this script. This command is more versatile than update-grub because we can use the -o option to have the results printed to a any filename and file path we like. That's a useful feature.

This script also runs other scripts and programs such as grub-mkdevice.map and grub-probe and then generates a new grub.cfg file." 
from: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")

That is my plan: copy the tarred system.tgz to a partition, copy the tarred home.tgz to a separate partition, untar them and then run: grub-mkconfig - /usr/sbin/grub-mkconfig

I'm trying a lot of things for the fist time with Ubuntu... I'm hoping someone who had done something similar can review this plan and confirm it ought to work...

I posted this on Absolute Beginners but few lookers and no takers (13/0), I am pretty close to an absolute beginner, but maybe I picked the wrong forum to ask the question on...  I bet lots of folks have alternative distributions on their hard drive with Ubuntu, I just want a second Ubuntu...I break things frequently, have looked for this answer... I know there are no guarantees with this, I would just like an experienced eye to look at the process here before I break something that might be noticed by someone with more experience...

Thanks,
Wyatt

---

