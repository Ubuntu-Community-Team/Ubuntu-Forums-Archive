---
title: "partitioning for multiboot system"
date: 2009-10-30
forum: General Help
---

### Post by cenzorrll on 2009-10-30
hi all, i was thinking setting up a multiple boot system with something around 4 OS's

my goal is to have one stable always working never crashing system. and three experimental systems that i can screw around with big time.

i was thinking of setting it up as so:
  - 512mb boot partition
  - swap partition (usual size)
  - ~10gb partition for the stable OS
  - extended partition with three partitions for the testing OS's

i was also thinking i might want to have a home partition that is shared between all the OS's (they'll all be linux, most likely some form of Ubuntu)

i've read in other threads that issues can come up with a shared home folder and the best way to do so is to have a separate user folder for each system

any thoughts?

---

### Post by ajgreeny on 2009-10-30
You can either do things that way with a single /home partition and different username for each, or you can probably do it more economically with small root partitions for each (10gb) and a separate /data partition.  Doing things this way will mean all distros have access to all your data files, docs, photos, music, videos, etc etc, without any duplication of those files.  All the configuration files and folders for each distro will go straight into the root partition for that one, keeping them separate from each other to avoid possible conflicts.

The most annoying thing may be getting the same config files for things like thunderbird and firefox, if you use them for email and browsing, so you may need to make a new group for email and internet and then make the ~/.mozilla-thunderbird and ~/.mozilla folders in the home partition of one of the distros read/write for members of that group, making sure that each user is a member, of course.

There may be other ways to do it, so wait for other peoples ideas as well.  With regard to extended vs primary partitions, if you have no windows, you can make the whole disk into an extended partition and get rid of the limit on numbers straight away.

---

