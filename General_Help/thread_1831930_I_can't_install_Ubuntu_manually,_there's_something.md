---
title: "I can't install Ubuntu manually, there's something wrong with the partitions"
date: 2011-08-24
forum: General Help
---

### Post by Hos4m on 2011-08-24
Hi.
I'm trying to install Ubuntu 10.10 on Dell Inspiron 1525 and I'm now on Windows 7 and I have 4 drivers.

When I got to the partitions section to manually install Ubuntu I got this:

[IMG]http://i52.tinypic.com/33mpn29.jpg[/IMG]

It says that I have no partition and If I try to make an ext3 partition for the installation, It'll format my hard disk.

What can I do?

---

### Post by fdrake on 2011-08-24
while in the live cd open the terminal and type:
```

fdisk -l
```

post here the results.

---

### Post by Hos4m on 2011-08-24
the results: [http://d.pr/iLwD](http://d.pr/iLwD)

---

### Post by Mark Phelps on 2011-08-24
Ok, first of all, folks should tell others that the fdisk option is a lowercase L, not a one.  As you discovered the hard way, using an option of "1" (a one) does not work.

Second, your post says you have four "drivers" -- you mean four "drives", right?

That being the case, you can NOT install Ubuntu into its own partition without removing an existing one, first. Why? Because four is the maximum number of Primary partitions you can have on a drive.

This means you will have to do a LOT of work to remove a partition and resize the existing partitions before installing Ubuntu. Do NOT use the installer to shrink the Win7 OS partition to install side-by-side.  That risks corrupting your Win7 install and rendering it unbootable.

And finally, if you do want to go ahead with dual-boot installation, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair the Win7 boot loader.

---

### Post by Hos4m on 2011-08-25
Sorry! I mean 4 partitions.

---

### Post by Quackers on 2011-08-25
That's the same thing as Mark Phelps has explained.
To create another partition for Ubuntu you must first delete an existing primary partition. Then you will probably need to shrink the C: partition to give some free space for Ubuntu to install into.
If you do that you should first defragment the Windows system.
You can then delete a partition and resize the C: partition using the Windows Disk Management console.
Once all that's done you can install Ubuntu using the "install alongside" option.

---

### Post by Nytram on 2011-08-25
The **fdisk** command needs to be prefixed with **sudo** in order to work, otherwise it unhelpfully does nothing:

> sudo fdisk -l

Could you post the output of this command again.

---

### Post by Hos4m on 2011-08-25
> **Quackers said:**
> That's the same thing as Mark Phelps has explained.
To create another partition for Ubuntu you must first delete an existing primary partition. Then you will probably need to shrink the C: partition to give some free space for Ubuntu to install into.
If you do that you should first defragment the Windows system.
You can then delete a partition and resize the C: partition using the Windows Disk Management console.
Once all that's done you can install Ubuntu using the "install alongside" option.

Check this, I have no primary partitions [http://d.pr/RvvA](http://d.pr/RvvA)

---

### Post by Hos4m on 2011-08-25
> **Nytram said:**
> The **fdisk** command needs to be prefixed with **sudo** in order to work, otherwise it unhelpfully does nothing:



Could you post the output of this command again.

Here: [http://d.pr/NIQj](http://d.pr/NIQj)

---

