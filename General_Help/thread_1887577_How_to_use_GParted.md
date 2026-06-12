---
title: "How to use GParted?"
date: 2011-11-27
forum: General Help
---

### Post by Macrotus on 2011-11-27
Hi all

I have one 640GB SATA 3GB HDD which contains the system (Ubuntu 11.10). I'd like to partition it. The should be about 50GB for Windows and the other 590GB for Ubuntu. There's already 22GB partition and GParted says it's some linux-swap.

How can I partition it?

---

### Post by oldfred on 2011-11-27
If you are totally reinstalling you can also delete the swap. Then make your NTFS 50GB partition with the boot flag as sda1 a primary partition.

I would also create a NTFS shared partition for any data you may want in both Windows & Ubuntu. I have my Firefox & Thunderbird profiles in a shared NTFS still even though I am not not booting XP (much:D).

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If you want lots of detail with screen shots, Herman's site is the place to go.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Macrotus on 2011-11-27
I'm not reinstalling the whole computer, I just installed 11.10 about 5 hours ago. 

Those introductions say that if I want to partition a disk, it shouldn't be started. But how can I turn it off if my OS is installed on it?

---

### Post by sudodus on 2011-11-27
Boot from the Ubuntu installation CD or USB drive. Gparted is there waiting for you :-)
(Have your hard drive running but ***do not mount it***)!

---

### Post by Macrotus on 2011-11-28
Thanks. It worked!

---

### Post by Mark Phelps on 2011-11-29
Glad to hear it's now working.  Please use the Thread Tools at the top of the thread and mark this thread as SOLVED.  thanks

---

