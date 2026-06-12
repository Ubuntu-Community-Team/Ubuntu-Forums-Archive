---
title: "Having trouble with swap partition, always listed as unknown"
date: 2010-04-14
forum: General Help
---

### Post by Falc7 on 2010-04-14
KDE partition manager reports /dev/sda3 is currently type "unknown".
I have tried reformatting this partition as linux swap, it says successfully done, but both Kde partition manager and gparted still immedietly report this partition as "unknown" again.

---

### Post by tuxulin on 2010-04-14
have you tried to delete and recreate the partition. try giving it a different size on creation to see what happens

Tux

---

### Post by rnerwein on 2010-04-14
hi
post: fdisk -l 
please
ciao

---

### Post by Falc7 on 2010-04-14
@tuxulin
Yep tried all that, still unknown

@rnerwein
Nothing happens when i put that in
```
jamie@jamie-kubuntu:~$ fdisk -l 
jamie@jamie-kubuntu:~$ 


```

---

### Post by john newbuntu on 2010-04-14
Run the command:
```
sudo swapon -a
```

Then check if swap is being enabled using:
```
sudo swapon -s
or
sudo fdisk -l
```

If it is still not, post the outputs of:
```
sudo fdisk -l
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by Falc7 on 2010-04-14
> **john newbuntu said:**
> Run the command:
```
sudo swapon -a
```

Then check if swap is being enabled using:
```
sudo swapon -s
or
sudo fdisk -l
```

If it is still not, post the outputs of:
```
sudo fdisk -l
sudo blkid -c /dev/null
cat /etc/fstab
```

```
jamie@jamie-kubuntu:~$ sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/mapper/cryptswap1                  partition       6056496 247528  -1

```

```
jamie@jamie-kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa88cb8cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28924   232331998+   5  Extended
/dev/sda2   *       28925       38159    74180137+   7  HPFS/NTFS
/dev/sda3           38160       38913     6056505   82  Linux swap / Solaris
/dev/sda5               1       28924   232331967   83  Linux
jamie@jamie-kubuntu:~$ 


```

This seems to suggest that the swap file is working yes?

```
jamie@jamie-kubuntu:~$ sudo blkid -c /dev/null
/dev/sda2: UUID="0A9C61789C615EE7" TYPE="ntfs" 
/dev/sda5: UUID="97da6210-9927-4fb9-9697-8227b4fe0221" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="ba16eb07-6a72-48cf-b58d-dc352ada1a35" TYPE="swap" 
jamie@jamie-kubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=97da6210-9927-4fb9-9697-8227b4fe0221 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=31d3a103-8f4a-43a5-8c15-b98c5d555b9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
jamie@jamie-kubuntu:~$ 

```

---

### Post by john newbuntu on 2010-04-14
From the output of "sudo fdisk -l", it is clear that /dev/sda3 is indeed a swap partition.

But this is not being identified or used by your system since your /etc/fstab and "swapon -s" points to /dev/mapper/cryptswap1, which means your system has been set up to use encrypted swap partition (or changed at some point to use it)

Now, if you decide to use /dev/sda3 as your swap partition, here's what you need to do:
First run:
```
sudo swapoff -a
```
You then need to remove the entry from /etc/crypttab.  
You also need to edit the last line of /etc/fstab and replace /dev/mapper/cryptswap1 with /dev/sda3.  _PLEASE_ make backup copies of these files before editing them.
Finally run:
```
sudo swapon -a
```
Now check with your kde tool on where the swap is.

If it does not work, rerun the commands you ran previously in post#6 and post your results.

---

### Post by Falc7 on 2010-04-14
```
jamie@jamie-kubuntu:~$ sudo swapon -a
swapon: /dev/sda3: read swap header failed: Invalid argument

```

Here is what my files look like:
```
jamie@jamie-kubuntu:~$ sudo kate /etc/crypttab

```
Looks like this:
```
# <target name>	<source device>		<key file>	<options>

```

```
jamie@jamie-kubuntu:~$ sudo kate /etc/fstab
```
Looks like:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=97da6210-9927-4fb9-9697-8227b4fe0221 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=31d3a103-8f4a-43a5-8c15-b98c5d555b9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 none swap sw 0 0

```

I have made backups; results from the commands from post6:
```
jamie@jamie-kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa88cb8cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28924   232331998+   5  Extended
/dev/sda2   *       28925       38159    74180137+   7  HPFS/NTFS
/dev/sda3           38160       38913     6056505   82  Linux swap / Solaris
/dev/sda5               1       28924   232331967   83  Linux

```

```
jamie@jamie-kubuntu:~$ sudo blkid -c /dev/null
/dev/sda2: UUID="0A9C61789C615EE7" TYPE="ntfs" 
/dev/sda5: UUID="97da6210-9927-4fb9-9697-8227b4fe0221" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="0ed11f8c-620f-4b9a-979c-d34667aa83a3" TYPE="swap"
```

```
jamie@jamie-kubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=97da6210-9927-4fb9-9697-8227b4fe0221 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=31d3a103-8f4a-43a5-8c15-b98c5d555b9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 none swap sw 0 0

```

---

### Post by john newbuntu on 2010-04-14
For some reason, swap is not being recognized by the block device command.  Create it as follows:

```
sudo /sbin/mkswap /dev/sda3
```Hopefully, this command should give you a UUID.  Once you get this, you can again try:
```
sudo swapon -a
```or if that does not work, replace the last line of your /etc/fstab with something like the following:

```
UUID=2ad3b11a-189d-434f-b546-f45dd844689f   none    swap    sw  0  0
```where the number following UUID= is the same number you got when you ran the mkswap command.  Finally run "sudo swapon -a"

---

### Post by Falc7 on 2010-04-15
Ah yes that did it, thanks :)

---

### Post by yourself65 on 2011-11-24
> **john newbuntu said:**
> For some reason, swap is not being recognized by the block device command.  Create it as follows:

```
sudo /sbin/mkswap /dev/sda3
```Hopefully, this command should give you a UUID.  Once you get this, you can again try:
```
sudo swapon -a
```or if that does not work, replace the last line of your /etc/fstab with something like the following:

```
UUID=2ad3b11a-189d-434f-b546-f45dd844689f   none    swap    sw  0  0
```where the number following UUID= is the same number you got when you ran the mkswap command.  Finally run "sudo swapon -a"

Dude!!

i have got to admit that you made my day really
i spend like 4 fokin hours looking for solution till i found this thread 
i registered specially to thank you ;)

---

### Post by yourself65 on 2011-11-24
hibernate did appear
but once i press it 
laptop freezes for a while then it's back again like a log-out or something

i though it might be the swap partition size

so i extend it..
here is the new size 

 total       used       free     shared    buffers     cached
Mem:          3924       1413       2511          0         53        705
-/+ buffers/cache:        654       3270
Swap:         4614          0       4614

i still couldn't find the problem..
any help would be appreciated :)

---

### Post by yourself65 on 2011-11-24
i think it might be a problem with vga
so here is mine if u 'll ask for it:
Intel Corporation Mobile 4 Series Chipset Integrated
 Graphics Controller

---

