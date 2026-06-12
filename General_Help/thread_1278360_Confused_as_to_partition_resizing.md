---
title: "Confused as to partition resizing"
date: 2009-09-29
forum: General Help
---

### Post by boyracerr on 2009-09-29
I have an ubuntu installation which runs inside a VMWare virtual machine. Because I originally made the root partition too small, I am now unable to import a large MySQL DB that I need.

As such, I am looking to resize the partition, using the instructions found here:

[http://beerpla.net/2007/08/10/how-to-resizegrow-vmware-linux-disks-and-partitions/](http://beerpla.net/2007/08/10/how-to-resizegrow-vmware-linux-disks-and-partitions/)

I successfully allocated the extra space using VMManager (as far as I can tell). Step 4 however has me stumped. I booted into the GParted live CD; problem is that it apparently does not work with LVM, which is in use on my Ubuntu system. I also tried using the latest Ubuntu Live CD with similar results.

Is there any way that I can make use of the space, or is this impossible?

Thanks

---

### Post by unutbu on 2009-09-29
[list]
[*] The information you need is in this guide:
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

but you'll have to understand enough to separate the cryptsetup stuff (having to do with LUKS encryption) from the LVM resizing commands.
[*] Note that over the past few months I've encountered at least two threads where people ran into problems after trying to resize their LVMs. I think in both cases they lost all their data. So I'd recommend backing up your data before attempting this.
[*] There is a way to set up mysql to access databases in locations other than /var/lib/mysql. Perhaps if you have more space in another partition (even in Windows), you can put the database there, and just tell mysql to look for the database in the other partition.
For more info on how to do this, see [http://ubuntuforums.org/showthread.php?p=7775666](http://ubuntuforums.org/showthread.php?p=7775666)
[/list]

---

