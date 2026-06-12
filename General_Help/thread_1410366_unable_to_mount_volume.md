---
title: "unable to mount volume"
date: 2010-02-18
forum: General Help
---

### Post by hannounest on 2010-02-18
[SIZE=3]
Relative newbie here so please accept apology if I am not well versed in using Ubuntu.

I was using Win XP Pro SP3 on my old machine.

I decided to make the move to Ubuntu. No problem since all files on the primary drive of the old machine were just OS related. I kept all of the important stuff (music, documents, reg codes, etc.) The computer had no problem importing the songs on the external drive to the music library. I am playing songs and loving it. 
Now the problem... when im starting with ubuntu i don't find the drive and i can't mount it. 

I get a box stating:
                [COLOR=Red]You are not privileged to mount this volume
                DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[COLOR=Black] 

[/COLOR]
[/COLOR][/SIZE]

---

### Post by cariboo on 2010-02-19
Please use the default font settings when creating a post. 

You didn't say what version you are using, so these are generic instructions. You need to be root to mount a partition that you aren't the owner of, for example if your Windows system is on the first partition of the first hard drive, the first thing you would need to do is to create a mount point for the partition. Open an Applications->Accessories->Terminal and type:

```
sudo mkdir /media/Windows
```

the above command will create a sub-directory in the /media directory called Windows. Now assuming again that Windows is on the first partition of the first hard drive you would mount it with the following command, in the same terminal type:

```
sudo mount /dev/sda1 /media/Windows
```

If you don't know what partition your Windows system is on, while you are still in the terminal type:

```
sudo fdisk -l
```

this command will list all the hard drives in your system as well as their partitions. I don't have a Windows partition on this computer, so I can't show you an example, but look for a partition where there is HPFS/NTFS at the end of the line, that would be your Windows partition.

---

### Post by zbirdman777 on 2010-02-19
zburditt@DexterIII:~$ sudo fdisk -l
[sudo] password for zburditt: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e9886c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13514   108550144    7  HPFS/NTFS
/dev/sda2           13515       26264   102414375   83  Linux
/dev/sda3           26265       26672     3277260   82  Linux swap / Solaris
/dev/sda4           26673       38913    98325832+   b  W95 FAT32


That's what it looks like when you run fdisk. You can see on mine its /dev/sda1 yours may be different.

---

### Post by Cilionelle on 2010-02-19
Hi, I'm having a similar problem with a partition already in ext3.

This is the error:
```
Error opening file '/media/extra/ADAM-variant-B-touch-screen-only.pdf': Permission denied
```

And this is the results of **fdisk -l**
```
tom@satris:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        6514    52291575   83  Linux
/dev/sda3            6515        9587    24683872+  83  Linux
/dev/sda4            9588        9726     1116517+   5  Extended
/dev/sda5            9588        9726     1116486   82  Linux swap / Solaris
```

Basically I'm trying to assign myself permission to use the mounted partition, right?  Is there a from-the-System-menu way to do this?

---

### Post by hannounest on 2010-02-19
thanks for you

im trying this command

mount -t ntfs-3g /dev/sda5 /media/Documents/ -o ro,force

it work

---

### Post by Cilionelle on 2010-02-19
Glad that worked for you!  That's great!

Unfortunately, it didn't for me.  I got a couple of errors, the first being that I've already shifted from an NTFS structure to ext3... should've seen that coming!

I still get the "permission denied" message when trying to put files in the partition though.  Anyone got any thoughts?

---

