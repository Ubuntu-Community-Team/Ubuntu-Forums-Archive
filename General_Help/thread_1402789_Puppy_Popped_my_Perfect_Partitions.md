---
title: "Puppy Popped my Perfect Partitions"
date: 2010-02-09
forum: General Help
---

### Post by grizato on 2010-02-09
Ok, this is not a matter of life or death for me.

I am just an experimental geek.

I had a three partition HD originally, one blank, one with my home directory and one empty one.

Then, I used unetbootin and put puppy on my empty partition. Now, puppy works, but I wantt a way to switch.

I can reinstall, I just want a way of having several linux OS's on a hard drive.

---

### Post by oldfred on 2010-02-09
While somewhat dated as it used grub legacy and grub2 does not like to be installed to a PBR. You cannot share /home with other installs but you can share data, so you should store data in a separate partition and mount it in every install if desired.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by grizato on 2010-02-11
Thanks!

Evrything's working so far.

For anybody else, [this]("http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_") is what I finally used.

WOW! Grub is cool!

---

