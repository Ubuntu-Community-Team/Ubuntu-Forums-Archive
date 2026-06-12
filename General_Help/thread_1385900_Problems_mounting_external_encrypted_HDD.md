---
title: "Problems mounting external encrypted HDD"
date: 2010-01-20
forum: General Help
---

### Post by Micha_R on 2010-01-20
Hey guys,

I'm still quite new to ubuntu, so I need to seek for advice here. Unfortunately, I couldn't find anything about my specific Problem in the Forum, therefore I have to open a new thread.

I have a external HDD with eSATA and USB connectors available. I want to use this HDD to store my backups. The HDD should be encrypted (my main system is as well).

So here is what I did so far:

1) I used the following code to create the encrypted LUKS partition with EXT3 Filesystem:
```
cryptsetup -c aes-xts-plain -s 512 luksFormat /dev/sdb1
cryptsetup luksOpen /dev/sdb1 luks
mkfs.ext3 /dev/mapper/luks 
```The system always hang when I executed the "mkfs.ext3..." command, so I switched the HDD from eSATA to USB and then it worked fine.

2) When I switched on the ext. HDD the first time, the drive was recognized automatically and Nautilus asked for the password. I typed it in as checked the checkbox to remember the password in the future.

For the backup I use a nice script that I found in another forum, where I can define a mountpoint and then the script will check for previous backups and only make a incremental backup based of the latest version. The script also mounts the drive automatically. In order to always have the same mountpoint, I want to make an entry in the /etc/fstab using the UUID of the ext. HDD.

Whatever I tried, it doesn't work. What am I doing wrong? Here is my current /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/ubuntu-root during installation
UUID=2ea47421-73ce-4c66-9606-8a1db81ae640 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dbdeb793-1d4e-43ea-8986-7b37fdbc9674 /boot           ext3    relatime        0       2
# /home was on /dev/mapper/ubuntu-home during installation
UUID=42702091-83e6-43eb-aad1-108f43eedf9d /home           ext3    relatime        0       2
# swap was on /dev/mapper/ubuntu-swap during installation
UUID=e225bcf9-908b-4226-a963-6b02ee658df1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Eintrag wegen iPhone
none        /proc/bus/usb     usbfs    devgid=125,devmode=666,nodev,nosuid,noexec    0    0
# external HDD
UUID=913977f7-8fa6-416f-af79-b5f913b68f53 /media/backup-hdd   ext3      noauto,users   0       0


```I made the "none /proc/bus/usb..." entry because it was recommended to ensure correct behaviour of the iPhone. Not sure if I need it though.

I created the mountpoint with this command:
```
sudo mkdir /media/backup-hdd
```
Now it seems the mountpoints owner is not root - strange right?```
2 4 drwxr-xr-x  3 michael michael 4096 2010-01-15 02:45 backup-hdd
```

How should I mount this drive correctly? It will be automounted as every USB device, but that should not be the case. I want the script to mount and unmount the drive.

Can anyone help me with that?

Thanks,
Mike

---

### Post by delcypher on 2010-01-20
If you want your luks encrypted hard drive to be mounted at boot you need to add that entry to /etc/crypttab and add the mapper device in /etc/fstab not the drive itself.

For you I think the following would be appropriate:

/etc/crypttab:
```

mappername   /dev/sdb1  none   luks

```
This assumes you want your mapper name to be mappername and that you use a passphrase rather than a key file (look at man crypttab for more help)


/etc/fstab:
```

# external HDD
/dev/mapper/mappername /media/backup-hdd   ext3      noauto,users   0  0
```

Assuming your mapper device is at /dev/mapper/mappername

I hope this helps you. Hopefully using crypttab will work better for you than it does for me at the momement. I found your post because I was looking to see if my problem was mentioned on the forums before I went on the bug tracker.

Oh as a useful note a few options are available in the file /etc/default/cryptdisks , the options are explained more thoroughly in man crypttab

---

### Post by Micha_R on 2010-01-21
@delcypher:

Thanks for your suggestions. Actually I don't want to mount the ext. drive at boot. I just want to switch it on when I want to make or restore a backup. If I switch it on, it should still not be automounted. The mountig process should be done by the backupscript.

Is that possible?

Also will I get prompted to enter the passphrase as soon as the drive will be mounted by the backup script?

Any ideas?

Mike

---

