---
title: "Problem resizing Linux partition in Ubuntu-Vista dual-boot system with GParted"
date: 2010-07-13
forum: General Help
---

### Post by BlackDeath3 on 2010-07-13
I recently installed Ubuntu on one of my laptops with Vista to create a dual-boot. After realizing that I hadn't given myself enough space on my Linux partition, I decided to use my Ubuntu Live CD to use GParted, to resize partitions. I had plenty of empty space in my Vista partition, so I shrunk it to give Linux some more space. Since Vista is directly to the left of Linux, I had to move the data to the left before growing the Linux partition. However, every time I thought that GParted had finished, it threw me some error 'fsck' or something like that. After closing the window, GParted refreshed, and the Linux partition had indeed grown. The problem is, the amount of free space available never changed. It's like the extra space given to the partition was automatically filled with something. I tried this two or three times, and every time the partition grew, so did the amount of used space, but the free space remained the same. Any ideas?

---

### Post by HudsonHawk on 2010-07-13
Hi!
You should run a drefrag before you would like to resize a  windows partition. If it's not solve your problem, run it again, until the Gparted says:"OK". :):P
I hope it solves your problem. :)

---

### Post by BlackDeath3 on 2010-07-13
Thanks for the response, I'll have to try that once I get home :)

---

### Post by chaosx9 on 2010-07-14
If the defragging doesn't work, open a root terminal on the live cd (Alt+F2>gksu gnome-terminal) then type in "fsck /dev/(partition)". It'll show you the name you should use for the linux partition (mine's /dev/sda5). It'll check the filesystem on the linux partition for you.

---

