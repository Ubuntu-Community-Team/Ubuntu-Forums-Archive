---
title: "How to access local drives in terminal?"
date: 2010-06-06
forum: General Help
---

### Post by 2603Munna on 2010-06-06
Hello I am having a windows 7 64 bit OS in my laptop....,and recently i have installed ubuntu 10.04 in one of the primary partitions.......,and totally there are 3 drives in my laptop now(excluding the one in  which ubuntu is installed)

I am interested in accessing the local drives(i.e.,any of the local drives except the "C" drive)in the terminal of the ubuntu......



Can any one suggest me how can i do it?:)

---

### Post by Ozymandias_117 on 2010-06-06
Did you mount it through nautilus? Or are you asking how do you mount it?

If you're trying to access a drive you've mounted through nautilus, it will be in /media

---

### Post by BoneKracker on 2010-06-06
You can see what's been mounted by using the 'mount' command with no options:
```
mount
```

Another way is to look at the file /etc/mtab:
```
cat /etc/mtab
```

Ubuntu supposedly mounts the drives used by Windows automatically and mounts them for you in /media.  So in the output of those commands, look for an NTFS filesystem mounted somewhere in /media.

Once you know what it's been mounted as (i.e., the directory name of the mountpoint in /media), you should be able to use that in your terminal:
```
cd /media/whatever
```

---

### Post by stderr on 2010-06-06
By the sounds of things you have a laptop drive partitioned into 4 partitions, with Ubuntu and Windows 7 installed in separate partitions. I don't know if they'll be mounted by default or not. There are many ways to do this though - perhaps the easiest is just to use nautilus.

Click on the "Places" menu, and then "Computer". If you can't see a side panel on the left of the window, press F9 to open it. On the side panel, you should see a list of partitions and folders, and "Places" at the top - if your view is different, change it at the top. You can mount an unmounted partition in the list by clicking on it, and an authentication window may pop up requesting your password to continue. After it's mounted, click on it again to view the contents. Partitions can be unmounted by clicking on the little eject icon to the right of them. 

You can also mount partitions from the command line using the mount command. Read the man page with

```
man mount
```

but basically you'd type

```
sudo mount /dev/sd
```

and then press TAB twice to get an autocomplete list, something like:

```
sudo mount /dev/sd
sda   sda2  sda4  sdb   sdc   sdd   sdd2  sde1  
sda1  sda3  sda5  sdb1  sdc1  sdd1  sde   sde2  

```

(Note that if your drives are old PATA style, you *may* need to use /dev/hd instead.)

Finish the command by giving a mountpoint - a directory to mount to. I typically create a /mntpt directory under root and use that.

```
sudo mount /dev/sdc1 /mntpt
sudo ls -l /mntpt
```

---

