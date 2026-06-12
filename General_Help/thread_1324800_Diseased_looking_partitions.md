---
title: "Diseased looking partitions"
date: 2009-11-12
forum: General Help
---

### Post by Squid Tamer on 2009-11-12
I hate to only ever ask for help around here, but I have yet another problem.

I was installing Ubuntu 9.10 on someone's computer, but during the install something went wrong with the partitions. It gave me an error and sent me back to the partitions screen. It looked correctly set up, so I just hit "Forward" again. The installation finished without a hitch.

Later, while looking for all the storage space that I was supposed to have, I loaded up Gparted and found this: (Screenshot)

It appears that... well...something  bad has happened. I was originally going to put Ubuntu on a 200 GB ext3 partition, but now it appears to be on a 89 GB ext4 partition, but with grub on the original sda1 or something. When I moved the boot flag to sda7, it wouldn't boot. I have put it back where it used to be, and it works again.

So, before I put too much work into setting the computer up, is there any hope for fixing this? How would I go about it, if so? Thanks!

---

### Post by wilee-nilee on 2009-11-12
After reading the post again I think I get what your trying to do, you want a storage partition and a main distro partition. There are a lot of people on the forums who use this method so help should be on the way, I don't do it this way I just store off the computer, so I have little chance of losing stuff and can change distros at my whim.

---

### Post by running_rabbit07 on 2009-11-12
If there is nothing else stored on the drive, I would say delete everything and start a new partition table.

Feel free to keep asking questions. That's what UF is here for.

---

### Post by wilee-nilee on 2009-11-12
Here is a link to another person asking about what I think your tryin to achieve ranch hand gives a good description.

[http://ubuntuforums.org/showthread.php?t=1321157](http://ubuntuforums.org/showthread.php?t=1321157)

---

