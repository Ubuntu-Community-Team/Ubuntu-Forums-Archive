---
title: "Sharing files between OS's"
date: 2006-05-30
forum: General Help
---

### Post by timmyc(AUS) on 2006-05-30
Hi. I am new to Linux and have recently install Ubuntu as recomended by a friend.  I love Ubuntu, but it won't be used as my primary OS, due to my family prefering MS Windows. I am having issues with putting files (On Ubuntu) onto space which I allocated as space to use to share files between OS's.

Here is how my partitions are set up.

Partition 1 > 46.2GiB > Windows NTFS (Soley for use with MS Windows)
Partition 5 > 4.66GiB > Ext 3 (Root directory)
Partition 6 > 4.66GiB > Ext 2 (Boot directory)
Swap Partition > 1.3GiB > Memory Swap 
Partition 8 > 17.7GiB > vfat ("Space" directory intended for sharing between OS)

Every time i try to write to the Space directory I get the following error message.

[img]http://img216.imageshack.us/img216/297/untitled6sh.jpg[/img]

Now, my friend who recomended I try Ubuntu told me told me to install a Nautilus script which I have done. I have used this to write to the space folder but it only gives me temporary access to do so.

Is there a perminant solution to this, so as I don't have to use the script everytime I wish to write to that Space?


Thanks. Tim.

---

### Post by nanotube on 2006-05-30
you probably did not mount it with the correct umask.
click the first link in my sig, and go to "mounting drives" section, it will explain what's up.

---

### Post by aysiu on 2006-05-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Make sure you read the whole thing, since the first example is NTFS.

---

### Post by timmyc(AUS) on 2006-05-30
Thanks. I fixed it now. 
I fixed it by edditing my /etc/fstab and adding " defaults,uid=1000,umask=0077 " to the apropriate drive in the mounting process, and then remounting it.


Thanks again. Sorry it was such a noob question.

---

### Post by nanotube on 2006-05-30
[QUOTE=timmyc(AUS)]Thanks. I fixed it now. 
I fixed it by edditing my /etc/fstab and adding " defaults,uid=1000,umask=0077 " to the apropriate drive in the mounting process, and then remounting it.


Thanks again. Sorry it was such a noob question.[/QUOTE]
hey, we all go through this at some point. :)

---

