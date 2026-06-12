---
title: "Partition and mounting help please"
date: 2009-07-08
forum: General Help
---

### Post by Cool Javelin on 2009-07-08
Dear helpful Xubuntu people:

I have Xubuntu Jaunty on an old machine with 2 IDE hard drives (sda is 4GB and sdb is 12GB.)

When I installed Jaunty, I used sdb for /usr, and sda for / (root).

I think all other folders (/var, /home, /etc,) ended up on sda.

I want to make a dual boot now using Damn Small Linux (DSL,) and would like to repartition sdb into 2 or more parts.

I got gparted but I can't unmount /usr from sdb because it is in use. The system is too limited to use any live install CD like straight Ubuntu.

So, I would like to move /usr to sda temporarily, tell xubuntu I have moved it (I assime there is a startup file somewhere that tells Linux how the mounts work,) resize the partition, then move /usr back.

Please, instructions on how to make a folder on sda, move the files, and reassign the mounts.

After I install DSL, I may repartition again to optimize space for both.

Thanks for any help you might offer.

Mark.

---

### Post by Woody1987 on 2009-07-08
You should be able to use the xubuntu live cd to do this. Boot it up and run gparted from within there to shrink and partition sdb. Another possiblity would be to copy /usr to sda and then change fstab accordingly so that it doesnt look at sdb for /usr. The second option is DANGEROUS and could potentially kill your system. Try the first method first.

---

### Post by michy99 on 2009-07-08
You can use a Gparted Live CD which does not have all that other stuff on it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Cool Javelin on 2009-07-10
Thanks both Woody and Michy:

I did Woody's second idea, made a folder on / (sda) called usr1 and copied /usr (from sdb) to /usr1.

I then booted the xubuntu alternate install into rescue mode,
(the live CD didn't boot as there is not enough memory.) and edited fstab to not mount sdb and also renamed usr1 to usr.

All is well so far.

I resized sdb and added sdb2 and sdb3.

I was able to install DSL, but didn't let it change the boot sector (It did create a grub menu.)

I haven't been able to go back to using sdb1 as usr yet, but I think I can do. It is a low priority now.

Thanks to both of you, I am going to mark this as closed and repost if I need more help.

Mark.

---

### Post by Cool Javelin on 2009-07-10
OK,I don't know how to mark this is solved.

Mark.

---

