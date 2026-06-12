---
title: "I keep having to fsck"
date: 2010-04-21
forum: General Help
---

### Post by a_z1_9scores on 2010-04-21
I have Kubuntu 9.10 (going to upgrade to kubuntu 10.04 as it looks good). About a month ago, I got the "mount of filesystem failed..." error on this page: [http://ubuntuforums.org/showthread.php?t=1305434](http://ubuntuforums.org/showthread.php?t=1305434). The solution worked great, until I restart and log back into Windows then I have to do it all over again. How to I make the fsck permanent?

---

### Post by thomasaaron on 2010-04-21
You don't really make fsck permanent. Ubuntu will automatically run it every so many boots.

Here are instructions for running fsck from a live CD, just to make sure you are doing it correctly...

-------------------------------------------------------
To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them.

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.
------------------------------------------------------

---

### Post by freesitebuilder on 2010-04-21
I've found that I'm still getting this error even after using the recommended solution - I'm holding on until 10.04 when I may do a clean install to see if that solves it. :(

---

