---
title: "Oddity in GParted"
date: 2010-10-05
forum: General Help
---

### Post by bushpilot on 2010-10-05
I have found an oddity in GParted, in which it is giving wrong information. 

I have two installs of Ubutu, one being a wubi installation, and the other being on a partition.  I'll use screenshots to explain.

The following is from GParted, from my partioned Ubuntu install:

[IMG]http://lh5.ggpht.com/_TQi1qB7zvw4/TKtqjWM0U5I/AAAAAAAAArM/eJCPkpCGz_U/s720/Screenshot%20Ubuntu.png[/IMG]

Note the 2.49 mb unalocated at the end.  That is wrong, it is actually part of the sda3 partition.

Here i what I get from Dis Manager (correct info):

[IMG]http://lh3.ggpht.com/_TQi1qB7zvw4/TKtlo5yQmqI/AAAAAAAAArE/BIyPqIZkcSg/s800/Disk%20Utility.png[/IMG]


And confirming the above, here is what GParted in wubi says:
[IMG]http://lh6.ggpht.com/_TQi1qB7zvw4/TKtlo2pjLEI/AAAAAAAAArI/dfgQlTKd7dA/s720/Screenshot%20Wubi.png[/IMG]


Any ideas as to the cause or the fix?  I have rebooted several times and uninstalled and reinstalled gparted.

BTW, this causes no problems, it is just a slightly annoying oddity.  The partition seems to work correctly.

Greg

---

### Post by srs5694 on 2010-10-05
I suspect what you're seeing is version differences in GParted and how they handle small unallocated bits of space. I've seen the same thing; some versions of GParted seem more likely to quietly hide small bits of unallocated space than do other versions. This is probably related to the issue of how partition alignment is handled -- old versions aligned on cylinder boundaries, but new versions align on 1 MiB boundaries. If you mix and match partitioning tools, you can have small unallocated blocks between partitions.

As a side note, if you want to know with precision how your partitions are laid out, GParted is a poor tool, because it rounds values in its summary displays. You can get more details on individual partitions by right-clicking them and selecting Information. That will give you partition start and end values in sectors, but only one partition at a time, which makes comparisons awkward. I also don't know of a way to get information on how many sectors the disk holds out of GParted. You can more easily obtain more precise information from fdisk by typing "sudo fdisk -lu /dev/sda" (or whatever the device is, or omit the device to get information on all devices at once). The result will be a listing of partitions, with start and end sector numbers, along with the total size of the disk. As a general rule, fdisk provides more complete and more reliable information on MBR disk partitions than does GParted or any other libparted-based tool.

---

### Post by bushpilot on 2010-10-06
Thanks, I think you are correct!

Greg

---

