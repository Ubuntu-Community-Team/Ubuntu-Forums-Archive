---
title: "Unallocated Partition help"
date: 2011-01-16
forum: General Help
---

### Post by natpat on 2011-01-16
Hey, 

I've got a computer set up that dual-boots Linux and Vista, which means that all four of my primary partitions are filled. However, I have a 45GB unallocated partition sitting there doing nothing.

My drive looks like this:

[-Vista Recovery-][-Vista Boot & data-][-Linux Swap-][-Ubuntu Boot & data-][-Unused-]
[----- 10GB -----][------111 GB-------][----8 GB----][-------57 GB--------][--46 GB-]

What I want to do is either expand the Vista partition to fill that 46GB, but any alternative that lets me use it I'm open to.

The problem is that I can't do this is Ubuntu, because I can't move the partitions whilst they're in use, and I can't do it using Vista because Partition Magic doesn't work, and Vista's built in Disk Management doesn't like the Ubuntu partitions, so I can't move it from there either.

Any help?

---

### Post by TeoBigusGeekus on 2011-01-16
Boot up with a live cd and run gparted from there.

---

### Post by Zimmer on 2011-01-16
You have 8gb of swap on a primary partition...
That is 8GB that might possibly be recoverable by your Win partition but you need to read more to find out how.. in the meantime there is 46GB lying unused at the end.

OK. IF you use Gparted from a Live CD you could delete the swap partition, making it free space.

Then, with the 46GB at the end of the disk you could make an EXTENEDED partition.

Into the extended partition you can then create a logical 8GB SWAP  and then another  partition with the remainder for DATA  in whatever filesystem suits your fancy.(you can create more than one or two LOGICAL partitions inside an EXTENDED partition, have a read.)

Even NTFS if you want Windows to see it primarily, else EXT3 or 4 if Linux primarily.

Use this partition to save your important files or as a space to copy them for backup . 
How much of the 57 GB Ubuntu install is being used ? Not that much (around 5-8 GB for the install + some DATA I would guess.)

You might also consider shrinking the Ubuntu partition before creating the EXTENDED to release more for the extended partition..
Loads of info
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Nice diagrams of partition themes here
[http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_](http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
read the additional notes at the end of this article for certain caveats.

Make a plan. Check it will work and in what order to do it.

AND BACKUP your important DATA before doing it...

---

### Post by ajgreeny on 2011-01-16
It would probably take for ever and a day to move the partitions which are between Vista and the unallocated area, depending on how much data there is in the ubuntu 57GB partition, and this would be needed if you really want to add the space to the vista partition.  The easiest thing to do would be to add the space to your ubuntu OS & Data partition, which is right next door to it.

Alternatively if you are prepared to re-install ubuntu from scratch it could be worth backing up all your ubuntu home data files, including the hidden files and folders, then deleting the two ubuntu partitions, and then enlarging the vista OS & Data partition, with its own disk management utility, not gparted.

You can then in the unallocated space make a new extended partition, and within that, three new logical partitions, swap, /home and /.  This will make a great partition layout for your ubuntu, and next time you need to install an updated version of the ubuntu OS you can do it with a clean install and keep retain /home much more easily than you can at present.

PS:  I've just seen Zimmer's post and I also like that idea as it means no re-installation.  I don't know why I didn't see that way of doing it as well.

---

### Post by natpat on 2011-01-16
Thanks for all your quick replies :)

I think I'll go with Zimmer's idea, along with shrinking the Ubuntu partition. I'll report back if I have any problems :)

---

### Post by oldfred on 2011-01-16
While it should let you boot without swap, when you delete & recreate the swap its UUID will change and you will have to manually update it in fstab.

To see new swap:
sudo blkid

gksudo gedit /etc/fstab

---

