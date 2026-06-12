---
title: "Dang!Crazy HD mounting"
date: 2006-04-15
forum: General Help
---

### Post by ububaba on 2006-04-15
I was so happy I could mount an additional HD, a SATA to be used just for the storage
of files. I did not cry out for help at all. I could access the new HD through 
System>Administration>Disks. 
Apparently I un-corked the champagne too early. Everytime when I visit "Disks" it is 
no longer possible for me to click any of the Gnome icons. I have to reboot first, only
then can I do that. 

Thanks to all wisemen on the forum. I know you are going to laugh at such a simple 
thing. Just an ownership problem? How can I lessen this bother?:-k

---

### Post by taurus on 2006-04-15
Assuming it's /dev/sda1 (check the output of "dmesg | tail" for the exact name of the device) and it has a fat32 filesystem on it.  Open a terminal and type
```

sudo mkdir /backup <-- create a mount point
sudo gedit /etc/fstab <-- edit your /etc/fstab so it would be mounted automatically at boot

```
Now, add the following line to the end of it and save it...
```

/dev/sda1  /backup  vfat  defaults,umask=0000  0  0

```
No need to reboot.  Mount it with
```

sudo mount -a

```

---

### Post by ububaba on 2006-04-16
[QUOTE=taurus]Assuming it's /dev/sda1 (check the output of "dmesg | tail" for the exact name of the device) and it has a fat32 filesystem on it.  Open a terminal and type
```

sudo mkdir /backup <-- create a mount point
sudo gedit /etc/fstab <-- edit your /etc/fstab so it would be mounted automatically at boot

```
Now, add the following line to the end of it and save it...
```

/dev/sda1  /backup  vfat  defaults,umask=0000  0  0

```
No need to reboot.  Mount it with
```

sudo mount -a

```[/QUOTE]

Thanks for the quick response. I am afraid to say that even though I did everything
as per instruction but it was to no avail. I have to do two reboots before I can send
this mail. This is the message I get when I run $ cat /etc/fstab

[COLOR="RoyalBlue"]mount: /dev/sdb already mounted or /backup busy[/COLOR]

 ](*,)

---

### Post by ubernoob on 2006-04-16
post the /etc/fstab file here, 

and also the fdisk from the disk you are trying to mount: 
fdisk /dev/hdb
then press p (and enter) then q (and enter)

---

### Post by ububaba on 2006-04-16
[QUOTE=ubernoob]post the /etc/fstab file here, 

and also the fdisk from the disk you are trying to mount: 
fdisk /dev/hdb
then press p (and enter) then q (and enter)[/QUOTE]
[COLOR="RoyalBlue"]# /etc/fstab: static file system information.[/COLOR]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb      /media/drive2     ext3   defaults   0 0
/dev/sdb  /backup  vfat  defaults,umask=0000  0  0


[COLOR="RoyalBlue"]# fdisk /dev/hdb[/COLOR]

The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

[COLOR="RoyalBlue"]after pressing p/ente[/COLOR]r:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   82  Linux swap / Solaris

[COLOR="RoyalBlue"]after pressing q/enter:[/COLOR]

bash: q: command not found

---

### Post by ubernoob on 2006-04-16
There are two reasons you cant mount it:

1. There are two lines in /etc/fstab. There should be only one.
/dev/sdb /media/drive2 ext3 defaults 0 0
/dev/sdb /backup vfat defaults,umask=0000 0 0

the second error is that it should have a number after "/dev/sdb". E.g /dev/sdb1

you can send the output of fdisk /dev/sdb if you need help to set fstab correct.

> after pressing q/enter:

bash: q: command not found
Thats ok. "q" was just to quit fdisk

---

### Post by ububaba on 2006-04-16
[QUOTE=ubernoob]There are two reasons you cant mount it:

1. There are two lines in /etc/fstab. There should be only one.
/dev/sdb /media/drive2 ext3 defaults 0 0
/dev/sdb /backup vfat defaults,umask=0000 0 0

the second error is that it should have a number after "/dev/sdb". E.g /dev/sdb1

you can send the output of fdisk /dev/sdb if you need help to set fstab correct.


Thats ok. "q" was just to quit fdisk[/QUOTE]
Thanks ubernoob. I removed /dev/sdb /backup vfat defaults,umask=0000 0 0 
and changed /dev/sdb to [COLOR="RoyalBlue"]/dev/sdb1[/COLOR] as you suggested.

So this is what I get as [COLOR="RoyalBlue"]fdisk /dev/sdb [/COLOR]output.
The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK.

Feel like being with a doctor,  will take any medicine you suggest, Sir!

---

### Post by ubernoob on 2006-04-16
that is a normal message. You have to press "p" after that to get the same information as you wrote above. (Then "q" to quit fdisk)

---

### Post by ububaba on 2006-04-16
[QUOTE=ubernoob]that is a normal message. You have to press "p" after that to get the same information as you wrote above. (Then "q" to quit fdisk)[/QUOTE]

Terribly sorry for the stupidity due to over-anxiousness.:oops:

This is what I got now from [COLOR="RoyalBlue"]/dev/sdb:  [/COLOR]

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb2               1           1        8001   83  Linux
/dev/sdb5               2        6471    51970243+  83  Linux
/dev/sdb6            6472       19457   104310013+  83  Linux

What say you?

---

### Post by ubernoob on 2006-04-16
No worries at all. Better to be safe than sorry! ;)

I'm not sure which of the partitions you want to mount, but i guess it is either sdb5 or sdb6.

So you should have a line in /etc/fstab like:
/dev/sdb5 /media/drive2 ext3 defaults 0 2

the you can change the path /media/drive2 to where you want to mount the partition. Just remember to make the directory first.

to remount fstab use:
sudo mount -a

if you want to mount the other partitions to find out whats on them you can do:
sudo mount /dev/sdb6 /media/newdisk

---

### Post by ububaba on 2006-04-16
[QUOTE=ubernoob]No worries at all. Better to be safe than sorry! ;)

I'm not sure which of the partitions you want to mount, but i guess it is either sdb5 or sdb6.

So you should have a line in /etc/fstab like:
/dev/sdb5 /media/drive2 ext3 defaults 0 2

the you can change the path /media/drive2 to where you want to mount the partition. Just remember to make the directory first.

to remount fstab use:
sudo mount -a

if you want to mount the other partitions to find out whats on them you can do:
sudo mount /dev/sdb6 /media/newdisk[/QUOTE]

Now this is once again getting above my head. I would like to use whole of the new
HD. I have divided it in 2 partitions. On /dev/sdb6 would like to have music files
while on /dev/sdb5 movies. I want to mount the partition where it is suitable, 
bearing these needs in mind. 

Does that sound extremely silly? Is it the height of me having totally missed the 
very abc of Linux?

---

### Post by ubernoob on 2006-04-16
Its not silly. Just make two lines in fstab:
dev/sdb5 /media/drive2 ext3 defaults 0 2
dev/sdb6 /media/drive3 ext3 defaults 0 2

I don't know what you mean with "suitable" :) That can be wherever you want. Mine datadisk is in a folder called /data

You can choose whatever you want and make that partition with e.g:
sudo mkdir /data

and then change 
/media/driver2
to
/data
in fstab

---

### Post by ububaba on 2006-04-16
[QUOTE=ubernoob]Its not silly. Just make two lines in fstab:
dev/sdb5 /media/drive2 ext3 defaults 0 2
dev/sdb6 /media/drive3 ext3 defaults 0 2

I don't know what you mean with "suitable" :) That can be wherever you want. Mine datadisk is in a folder called /data

You can choose whatever you want and make that partition with e.g:
sudo mkdir /data

and then change 
/media/driver2
to
/data
in fstab[/QUOTE]


Thanks for all the help. By suitable I meant I did not want to get stuck with an
un-reversible situation and have the options open. Me chicken.:( 

I still keep logging-in at root level instead of user. That is the next headache.

---

