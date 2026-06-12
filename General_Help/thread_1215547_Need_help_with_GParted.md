---
title: "Need help with GParted"
date: 2009-07-17
forum: General Help
---

### Post by felinoel on 2009-07-17
I set up the correct partition for to be booted from, and it came up with an error from the operating system, if that fixable? If not, I could resize the partition so it has only enough room for the data in it, and then install the windows and linux in the empty spaces, then later drag the data from the messed up partition, right?
Also, what does this lba flag mean?




For information as to the cause of my problem, see here...
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1214570](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1214570)

---

### Post by felinoel on 2009-07-17
...

---

### Post by hansdown on 2009-07-17
Hi felinoel.

Patitioning is not something I have done a lot.

The LBA flag is the logical block addressing flag.

[http://www.google.ca/search?q=what+does+this+lba+flag+mean+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=what+does+this+lba+flag+mean+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Don't know much more than that.

---

### Post by felinoel on 2009-07-17
> **hansdown said:**
> Hi felinoel.

Patitioning is not something I have done a lot.

The LBA flag is the logical block addressing flag.

[http://www.google.ca/search?q=what+does+this+lba+flag+mean+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=what+does+this+lba+flag+mean+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Don't know much more than that.I see, well thanks

---

### Post by felinoel on 2009-07-17
Should I resize the partition so it has only enough room for the data in it, and then install the Windows and Linux in the empty spaces, then later drag the data from the messed up partition (is that last part even possible?), or should I wait, to see if someone know how to help me?

---

### Post by felinoel on 2009-07-17
> **felinoel said:**
> Should I resize the partition so it has only enough room for the data in it, and then install the Windows and Linux in the empty spaces, then later drag the data from the messed up partition (is that last part even possible?), or should I wait, to see if someone know how to help me?

...

---

### Post by hansdown on 2009-07-17
As I said I'm not very good at this, so please excuse my noobish help.

- Install windows OS.

- Use the ubuntu install disk, and choose the "use available space".

This is assuming you have a newer machine with ( you didn't specify ram, etc) just as an example, 1GB of ram?

I've used this to install ubuntu on a few machines (for other people).

Once again, sorry for the noobish reply, but it saves some work.

---

### Post by hibliss on 2009-07-18
Seems like your drive may be failing. You should partition it as one sigle partition and test it. There are several ways to do this.

You can boot from LiveCD and run Gparted from there, partition your drive as one and check it with

```

sudo fsck /dev/hdxy
```

hdxy is the drive's ID, so it may be sda1, or whatever that drive registers as.

There are other disc checking utilities that you can boot from.

---

### Post by felinoel on 2009-07-18
> **hansdown said:**
> As I said I'm not very good at this, so please excuse my noobish help.

- Install windows OS.

- Use the ubuntu install disk, and choose the "use available space".

This is assuming you have a newer machine with ( you didn't specify ram, etc) just as an example, 1GB of ram?

I've used this to install ubuntu on a few machines (for other people).

Once again, sorry for the noobish reply, but it saves some work.My problem is that I was to know if I should give up completely on my old files and settings in Linux or if it is possible to revert this un-unallocated partition of my old files and Linux settings to a working version of Linux

---

### Post by felinoel on 2009-07-18
> **hibliss said:**
> Seems like your drive may be failing. You should partition it as one sigle partition and test it. There are several ways to do this.

You can boot from LiveCD and run Gparted from there, partition your drive as one and check it with

```

sudo fsck /dev/hdxy
```

hdxy is the drive's ID, so it may be sda1, or whatever that drive registers as.

There are other disc checking utilities that you can boot from.Whilst trying to install Windows alongside my Linux, I accidentally unallocated my Linux partition, using TestDisk and GParted I was able to un-unallocate it, but it won't run anymore, but the partition itself has the same memory usage, so it must all still be in there...?

---

### Post by felinoel on 2009-07-18
...

---

### Post by felinoel on 2009-07-18
...

---

### Post by felinoel on 2009-07-18
...

---

### Post by felinoel on 2009-07-18
...

---

### Post by merlinus on 2009-07-18
At this point, try to back up important data by using a live cd such as knoppix, and reinstall.  But be sure to look at dual-booting guides such as this one beforehand:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by felinoel on 2009-07-18
> **merlinus said:**
> At this point, try to back up important data by using a live cd such as knoppix, and reinstall.  But be sure to look at dual-booting guides such as this one beforehand:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)Well... I did make a copy of the GRUB boot menu, but that's in the messed up partition, what would that do anyways? And if I just squeeze all my data into one smaller partition, freeing up space, can I still do that data saving thing at a later time?

And actually I was following a guide for dual-booting...
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)
This one

---

### Post by merlinus on 2009-07-18
The problem is how you will know that all the data is squeezed into one partition.  If you resize, there is a risk of losing some of it.

And as you said, no sense making a backup of grub.

---

### Post by felinoel on 2009-07-18
> **merlinus said:**
> But be sure to look at dual-booting guides such as this one beforehand:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)I already had Linux installed, your site is for installing Linux after a different OS, I am told it is harder to install something else after Linux, which was what I was doing

---

### Post by felinoel on 2009-07-18
> **merlinus said:**
> The problem is how you will know that all the data is squeezed into one partition.  If you resize, there is a risk of losing some of it.

And as you said, no sense making a backup of grub.Darn, the guide told me to back it up, there seriously is no reason for it?

If I take off 15 gigs from a partition with 20 gigs used and 200 gigs free, there is a chance the gigs I take off is in my used space and not my free?

---

### Post by merlinus on 2009-07-18
Reinstalling grub is very easy.  As for resizing, make sure you take the space from the end of the partition and not the beginning, and you should be okay.

---

### Post by felinoel on 2009-07-18
> **merlinus said:**
> Reinstalling grub is very easy.  As for resizing, make sure you take the space from the end of the partition and not the beginning, and you should be okay.

k... so I can just save the data later? If I want to prep a partition for installation of an OS, should it be unallocated, or should I "Create New Partition"

---

### Post by merlinus on 2009-07-18
Either way should work, but it cannot hurt to create and format the partition for the os you are wanting to install.

Remember that you can only have 4 primary partitions, but many, many logicals within an extended.  Windows needs to go in a primary, however; linux does not care.

---

### Post by felinoel on 2009-07-18
> **merlinus said:**
> Either way should work, but it cannot hurt to create and format the partition for the os you are wanting to install.

Remember that you can only have 4 primary partitions, but many, many logicals within an extended.  Windows needs to go in a primary, however; linux does not care.

I see, ok then, thanks

---

### Post by merlinus on 2009-07-18
Good luck, and let us know how it goes.

---

### Post by Tman5293 on 2009-07-18
Linux and Windows can't be installed on the same partiton. Make an ext3 or ext4 partiton for linux and let windows make its own ntfs partion when its installed.

---

### Post by felinoel on 2009-07-19
> **merlinus said:**
> Good luck, and let us know how it goes.

Terribly, I deleted the data I wanted to save

> **Tman5293 said:**
> Linux and Windows can't be installed on the same partiton. Make an ext3 or ext4 partiton for linux and let windows make its own ntfs partion when its installed.

This was my problem, darn, oh well, now to just make it dual boot like I originally wanted

---

### Post by felinoel on 2009-07-19
After giving up on my data, the dual booting worked, but now it says there is no free space on disk '/' 
Why is it saying this? Where is disk '/' how do I move the free space found everywhere else to it?
Sigh

See [here](http://ubuntuforums.org/showthread.php?p=7642296#post7642296)

---

