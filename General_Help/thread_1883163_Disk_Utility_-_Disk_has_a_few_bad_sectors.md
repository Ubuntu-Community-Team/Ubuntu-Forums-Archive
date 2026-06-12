---
title: "Disk Utility - Disk has a few bad sectors?"
date: 2011-11-18
forum: General Help
---

### Post by cottfcfan on 2011-11-18
The dreaded message appeared in Disk Utility.
My drive has several partitions.
Is there anyway I can find out where the bad sectors are?
And more importantly can I do anything about it?
I also have Windows 7 installed. Is there a program I can run from there, to see if I get the same result?

---

### Post by Gremlinzzz on 2011-11-18
> **cottfcfan said:**
> The dreaded message appeared in Disk Utility.
My drive has several partitions.
Is there anyway I can find out where the bad sectors are?
And more importantly can I do anything about it?
I also have Windows 7 installed. Is there a program I can run from there, to see if I get the same result?

[http://www.ehow.com/how_113636_fix-sectors-hardfix-sectors-hard.html](http://www.ehow.com/how_113636_fix-sectors-hardfix-sectors-hard.html)
:popcorn:

---

### Post by dabl on 2011-11-18
If it truly has blocks going bad, I would not plan on using it much between now and the time you replace it.   In other words, it's not likely that it is now finished deteriorating ...

I like the Parted Magic live USB stick (or live CD) for such purposes:

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

It has "Smart Control", a GUI front end for smartmon-tools. It also has "testdisk" and another hdd hardware checker.

---

### Post by philinux on 2011-11-18
> **cottfcfan said:**
> The dreaded message appeared in Disk Utility.
My drive has several partitions.
Is there anyway I can find out where the bad sectors are?
And more importantly can I do anything about it?
I also have Windows 7 installed. Is there a program I can run from there, to see if I get the same result?

But more importantly does it show the disk as healthy. Green icon.

---

### Post by cottfcfan on 2011-11-18
Thanks for the replies guys.
Philinux.. The icon is still green even though the message says "Disk has a few bad sectors".

Gremlinzzz... I followed the link as the problem was indeed on my windows 7 partition.
It did something, and took a while, but disk utility still reports the problem.

At least my ubuntu & xubuntu partitions report clean.
I just hope the problem doesn't get any worse.

---

### Post by philinux on 2011-11-18
> **cottfcfan said:**
> Thanks for the replies guys.
Philinux.. The icon is still green even though the message says "Disk has a few bad sectors".

Gremlinzzz... I followed the link as the problem was indeed on my windows 7 partition.
It did something, and took a while, but disk utility still reports the problem.

At least my ubuntu & xubuntu partitions report clean.
I just hope the problem doesn't get any worse.

Green mean disk is healthy and its passed the check. Most disks eventually get re mapped sectors. The disk itself does it with internal software. The thing to do is check the status and the reallocated sector count for changes.

---

### Post by cottfcfan on 2011-11-18
Thanks Phil.
The reallocated sector count shows just one bad sector, on my Windows 7 partition which is hardly ever used.
Ive backed up all my data & clonezilla'd my 2 'buntu partitions, to cover my back.
Other than that I'll just keep an eye on it.
I'll mark this thread as solved.

---

### Post by philinux on 2011-11-18
> **cottfcfan said:**
> Thanks Phil.
The reallocated sector count shows just one bad sector, on my Windows 7 partition which is hardly ever used.
Ive backed up all my data & clonezilla'd my 2 'buntu partitions, to cover my back.
Other than that I'll just keep an eye on it.
I'll mark this thread as solved.

My GF's laptop had hundreds of bad sectors and was still healthy with no read wrote errors at all.

---

