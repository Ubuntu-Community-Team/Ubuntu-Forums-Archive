---
title: "File system mystery, unmountable disk and auto mounting."
date: 2010-01-29
forum: General Help
---

### Post by moforilla on 2010-01-29
I started to run out of space on the single disk I have in my system, so I added a new one. 

I had used this disk previously for a Fedora distro. The disk has a normal set of partitions on it. /boot / swap / and home, the same as my current disk arrangement.

I connected this disk to my system and booted my machine. After logging in I noticed that a lot (80%) of cpu was being chewed up. The processes mountall and udevd were doing something.

I mounted the drive to see what was on it. I mounted what I thought was my old /home to /mnt/oldhome and had a look. What I was seeing was my current /home in /mnt/oldhome. I started up gparted to get a visual look of what has happening. Gparted showed both disks to be mounted and both using the same mount points.

When trying to umount this new disk it doesnt seem to allow it. I'm guessing that my system is auto mounting the new disk.

What is going on? If it is auto mounting how do I turn it off and how can I make the new disk usable?

---

