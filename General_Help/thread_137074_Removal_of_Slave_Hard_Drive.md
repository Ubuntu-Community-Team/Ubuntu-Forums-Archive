---
title: "Removal of Slave Hard Drive"
date: 2006-02-27
forum: General Help
---

### Post by ironmaiden6669 on 2006-02-27
I have a slave hard drive that I need to take out of my system to use elsewhere.
It is a ~3Gb drive that I partitioned for swap-file when I installed ubuntu.
This is the only allocated swap area.
Will ubuntu care if I start it up without this drive in there ?
Will I have to organize another swap-file space on my master drive for ubuntu to run correctly ?
Does my computer even need swap-file space ? I have 768Mb of RAM in a P667.
I mainly use kde.
What is the best way to go about ensuring that ubuntu will work properly after the slave drive is gone ?

---

### Post by Ramses de Norre on 2006-02-27
I think you might need to delete the line for the swap partition from fstab.
Ubuntu will run without the swap but it might be a bit slower (mostly when running a lot of apps).
You can make a swap file or a new swap partition if it's too slow.

---

### Post by ironmaiden6669 on 2006-02-27
Thanks.
To make a new a swap area, would I just use the 'Disk & Filesystems' applet in Control Centre ?

---

### Post by Ramses de Norre on 2006-02-27
Where do you find that control center? I haven't seen that yet.
But you can do this: (didn't tried myself yet)
```
 To add a swap file:
1. Determine the size of the new swap file and multiple by 1024 to determine the block size. For example, the block size of a 64 MB swap file is 65536.
2. At a shell prompt as root, type the following command with count being equal to the desired block size: dd if=/dev/zero of=/swapfile bs=1024 count=65536
3. Setup the swap file with the command: mkswap /swapfile
4. To enable the swap file immediately but not automatically at boot time: swapon /swapfile
5. To enable it at boot time, edit /etc/fstab to include:
/swapfile swap swap defaults 0 0

The next time the system boots, it will enable the new swap file.
6. After adding the new swap file and enabling it, make sure it is enabled by viewing the output of the command cat /proc/swaps or free.
```

Or even better: make a new swap partition, to do so you'll need to resize your existing ext3 partition and format the free space as linux swap (that's how it's cald in gparted).
Then add a line to fstab like this ```
/dev/sda5       none            swap    sw              0       0

```
And turn the swap on with swapon /dev/xxx (xxx=partitions logical name)

---

### Post by ironmaiden6669 on 2006-02-27
Thanks for that.
Control Center is in KDE.
I've been giving the kubuntu-desktop a go.
Thanks again for the help.

---

