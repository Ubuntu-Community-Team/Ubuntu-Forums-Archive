---
title: "Shrink /home in LVM"
date: 2011-05-16
forum: General Help
---

### Post by diamond_D on 2011-05-16
What is my best way of shrinking /home contained in an LVM? It is it's own partition and is contained completely on a logical volume contained on a single physical disk. I have other regular partitions (non-LVM) such as /root /boot /usr/local and a few other custom partitions on this disk as well. I simply want to shrink /home by 10GB so I can create another partition for /var/log
 
I am not too familiar with LVM tools but I figure there must be an option. I obviously can't be in X since /home can't be mounted. I was thinking about using a LiveCD but not sure if the Natty 11.04 LiveCD supports LVM tools. If anybody can help guide me to the commands and safest way to accomplish this it would be greatly appreciated.

---

### Post by srs5694 on 2011-05-16
The easiest way to do this is to use a GUI tool, such as kvpm or system-config-lvm. Both of these are available in Ubuntu (at least, they're both installed in my Ubuntu 9.10 system), but you'd need to do one of two things to use them:


[list]
[*]Activate your root account (which the Ubuntu developers discourage, but sometimes it's necessary), log out of your regular account, log into the root account, unmount /home, and do the work.
[*]Boot from a live CD, install kvpm or system-config-lvm, and do the work from there.
[/list]


Alternatively, you can do it in text mode. This will require working in the same way (directly as root or from a separate boot disc) and for the same reasons, although you can use a text-mode login. The procedure I recommend is:


[list=1]
[*]Use resize2fs (or whatever tool is appropriate for your filesystem) to shrink the filesystem to something significantly smaller than you require. For instance, if you've got a 100 GiB logical volume that you want to shrink to 90 GiB, shrink it to 80 GiB with "resize2fs /dev/mapper/{whatever} 80G".
[*]Use lvresize to resize your logical volume to the desired size, as in "lvresize -L 90G /dev/mapper/{whatever}"
[*]Use resize2fs to resize the filesystem to the exact size of the logical volume, as in "resize2fs /dev/mapper/{whatever}". Note that there's no size specified; with no size specified, resize2fs sizes to precisely the size of the volume.
[/list]


I recommend doing it this way so as to minimize the risk of ending up with a filesystem that's too small or (much worse) too large for the containing logical volume.

---

### Post by diamond_D on 2011-05-17
I did this series of commands along with "pvresize" and things look ok when I look at the physical extent (PE) values when I do pvdisplay, vgdisplay and lvdisplay. However when I use parted or fdisk to view my disk I expected to see "Unallocated space" available. Instead my LVM partition is the same size as it was originally. 
 
BTW, I originally started using the LVM tools available on the alternate install CD. It seemed to hang when running lvreduce. I let it run over an hour and it did not reduce by the 10G that I specified. I rebooted and ran the tools from the systemrescueCD that appeared to work quickly and smoothly however I still do not know how to get the 10G "unallocated space" that I want. Not sure if hanging on lvreduce did any damage but running e2fsck on the volume seems to be ok.

---

### Post by srs5694 on 2011-05-17
Think of LVM as a filesystem for filesystems. That is, your logical volumes (which contain your filesystems) are stored *inside* the partitions in which the LVM itself resides. Thus, you can change your logical volumes all you want and you'll see no difference at the partition level (as viewed by fdisk), any more than you'd see a difference in the fdisk output when you create files in a partition that contains a filesystem more directly. Thus, the results you report are as designed.

Instead of creating a partition for /var/log, you should create a new logical volume for it. (I thought you'd simply mistyped what you meant in your original post.) You can do this with a GUI tool or with lvcreate, as you see fit.

BTW, if you're creating a separate volume for /var/log because your log files are growing too large and causing problems elsewhere, you may need to look into log rotation tools instead of or in addition to splitting /var/log off into its own filesystem. Perhaps you've got a log file that's not included in your log rotation schedule, or maybe your log rotation settings are inappropriate for the log files you are rotating. I don't have any URLs handy for references on this topic, but you can try doing a Web search on "Linux log rotation" or something similar. If necessary, start a new thread on the topic.

If you shut down your computer regularly, log rotation might not occur at all. If so, you can work around that issue with a tool called anacron; see [this article](http://www.ibm.com/developerworks/linux/library/l-anacron/index.html) I wrote on it a while ago. (Some distributions either install anacron by default or use similar functionality in other programs. I don't know offhand if Ubuntu does anything like this.)

---

