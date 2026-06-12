---
title: "Need help changing \home"
date: 2009-07-18
forum: General Help
---

### Post by twistedrabbit on 2009-07-18
I messed up my Ubuntu 9.04 while installing Zone Minder i got tired of trying to fix it and decided to just reinstall all of ubuntu. When i first installed Ubuntu, i had 2 partitions, one for /home and one for the rest. When i put the live CD in today, i reinstalled the rest but not the home. then when i started it back up, there was a new home folder and my old one is a mountable partition.
How do i get it back to the default home folder and remove the otherone?

I tried editing the fstab, but i cant find the /home to change it... i get this

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=373adf9e-71fa-4310-b954-1827180dedad /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=913c6b64-4c9e-4efb-86f1-0294fec11794 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

EDIT:
Gave up, reformated home partition and \ at the same time.

---

### Post by michy99 on 2009-07-18
First, what is the output of these commands?```
ls -l /home
sudo fdisk -l
cat /etc/fstab
```

---

### Post by twistedrabbit on 2009-07-18
> **michy99 said:**
> First, what is the output of these commands?```
ls -l /home
sudo fdisk -l
cat /etc/fstab
```


~$ ls -l /home
total 4
drwxr-xr-x 28 twisted twisted 4096 2009-07-18 14:06 twisted

and

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1867    14996646    7  HPFS/NTFS
/dev/sda2            1868        3161    10394055   83  Linux
/dev/sda3            3162       14589    91795410    5  Extended
/dev/sda5            3162       13495    83007823+  83  Linux
/dev/sda6           13496       14589     8787523+  82  Linux swap / Solaris

and 

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=373adf9e-71fa-4310-b954-1827180dedad /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=913c6b64-4c9e-4efb-86f1-0294fec11794 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-07-18
Ok, it looks like your old /home is on dev/sda5. Boot up from a Live CD. First backup the new home.```
sudo mv /home /home.backup
```Now make a new /home to mount to.```
sudo mkdir /home
```Now add a line to fstab to mount your old /home partition.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sda5 /home           ext3    relatime        0       2
```Now reboot your system and see if your /home partiton is mounted as it should be. If it works, you can delete the backup.

---

### Post by merlinus on 2009-07-18
Use this

```
gksudo gedit /etc/fstab
```These keyboards often have a mind of their own, when it comes to typing...

:)

---

### Post by michy99 on 2009-07-18
> **merlinus said:**
> Use this

```
gksudo gedit /etc/fstab
```These keyboards often have a mind of their own, when it comes to typing...

:)

Good catch. I've corrected it in my post.

---

### Post by twistedrabbit on 2009-07-18
What i get is: ubuntu@ubuntu:~$ sudo mv /home /home.backup ubuntu@ubuntu:~$ sudo mkdir /home ubuntu@ubuntu:~$ gksudo gedit /ect/fstab Error copying '/home/ubuntu/.Xauthority' to '/tmp/libgksu-ir21Gw': No such file or directoryubuntu@ubuntu:~$   do i need to change to my account or something? using terminal threw the live CD.

---

### Post by merlinus on 2009-07-18
You are running from the live cd, so you will have to mount your linux partitions before running the commands.

Usually you can do this by clicking on Computer in Places.

---

### Post by twistedrabbit on 2009-07-18
> **merlinus said:**
> You are running from the live cd, so you will have to mount your linux partitions before running the commands.

Usually you can do this by clicking on Computer in Places.

 It says   Nautilus could not create the following required folders: /home/ubuntu/Desktop, /home/ubuntu/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

---

### Post by michy99 on 2009-07-18
Sorry, I forgot that you need to mount the harddrive. Let's try this again. First mount the / partition.```
sudo mkdir /media/drive
sudo mount -t ext3 /dev/sda2 /media/disk
sudo mv /media/disk/home /media/disk/home.backup
sudo mkdir /media/disk/home
gksudo gedit /media/disk/etc/fstab
```
Now add the line.```
/dev/sda5 /home           ext3    relatime        0       2
```

---

### Post by twistedrabbit on 2009-07-18
Ok, well i fu%$#d something up, it was saying my /home was MIA when i tried to boot back into nonLiveCD. 
Its not worth the trouble at this point, i just threw some stuff on my external HD and im gonna reformat it all.
Im not very good at this Linux folder system... o well, 
if i stick with it i will probably learn.

---

