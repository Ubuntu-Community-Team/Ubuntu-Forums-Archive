---
title: "DD image restores larger than image"
date: 2011-02-13
forum: General Help
---

### Post by tamas413 on 2011-02-13
I've been working on getting another OS installed on my computer for one of my classes (OS specific assembly instructions).
To get this OS running, I had to start using a GPT rather than a MBR table. I backed up my Ubuntu partition (ext4) using the old-fashioned dd command. I've since been able to get everything working again after a dd restore. 
The problem is that my original Ubuntu partition was only about 50GB and the dd image only takes up 40 GB. After I restored the image to the new drive (146BG), gparted is reporting 119GB used and only 26GB free.
What can I do to reduce the size of my install to 40GB again?

UPDATE:
When looking at the disk in baobab, it says the the filesystem is only 47.2 GB and that only 20.9 GB has been used. This is likely what the old partition's breakdown was. So my new question is: How can I make the filesystem capacity (47.2 GB) equal that of the partition that it is on (146 GB)?
Thanks

---

### Post by srs5694 on 2011-02-13
If I understand correctly, you've done a dd copy of a filesystem of a certain size to a device with a larger capacity, and you want to be able to use the entire capacity of the new device. If so, the solution is to use the resize2fs command, as in:

```

sudo resize2fs /dev/sda5

```

Change the device filename (/dev/sda5) as appropriate, of course. Also, this works for ext2/3/4 filesystems; for other filesystem types, you'll need to use other filesystem-specific commands.

---

### Post by tamas413 on 2011-02-13
Sorry. I'm an idiot. I probably should have known that.

Thanks for the help.

---

