---
title: "I don't want Ubuntu to see an internal drive"
date: 2010-08-08
forum: General Help
---

### Post by Airais on 2010-08-08
I use ubuntu on a usb drive and Windows 7 as my main.  The problem I have is that because I have a 1tb hard drive and a 1gb mem stick its really easy to chose the wrong on in the places menu as they are both 968 then either gb or tb which at a glance is hard to tell. Anyway I know the tb hard drive isn't mounted but I would like to know how to stop Ubuntu from even seeing the tb hard drive.  Is this possible?? If So How?

---

### Post by dino99 on 2010-08-08
install mountmanager to deal with partitions and devices rights, set your prefs into "system admin mountmanager"

---

### Post by Airais on 2010-08-08
Thanks for the reply I'll try that out when I get home!

---

### Post by Airais on 2010-08-10
kk I have it installed but I have no idea what I am doing here I simply don't want Ubuntu to even see the internal drive can some one help me set that up using mountmanager. Thanks

---

### Post by dcstar on 2010-08-11
> **Airais said:**
> I use ubuntu on a usb drive and Windows 7 as my main.  The problem I have is that because I have a 1tb hard drive and a 1gb mem stick its really easy to chose the wrong on in the places menu as they are both 968 then either gb or tb which at a glance is hard to tell. Anyway I know the tb hard drive isn't mounted but I would like to know how to stop Ubuntu from even seeing the tb hard drive.  Is this possible?? If So How?

Use the "noauto" option in the /etc/fstab line, for example this is what I use to keep my external eSATA drive from being mounted unless I actually have it switched on and then do a "sudo mount -a":

```
#/dev/sdh5
UUID=whatever	/BackupDrive/home ext4	noatime,nodiratime,noauto 0  2
```

---

### Post by Morbius1 on 2010-08-11
> **Airais said:**
> I use ubuntu on a usb drive and Windows 7 as my main.  The problem I have is that because I have a 1tb hard drive and a 1gb mem stick its really easy to chose the wrong on in the places menu as they are both 968 then either gb or tb which at a glance is hard to tell. Anyway I know the tb hard drive isn't mounted but I would like to know how to stop Ubuntu from even seeing the tb hard drive.  Is this possible?? If So How?

OK, I'm mildly confused by your post. Do I have this right? :
The 1TB hard drive is the internal drive with Win7 installed on it and most likely formatted in NTFS.

One way to make the drive disappear from places is to actually mount it at boot with the right parameters. For example, Let's say that the 1TB partition is located at /dev/sda1. You could create a line in /etc/fstab that will mount it automatically:
```
/dev/sda1 /mnt/Win7 ntfs defaults,nls=utf8,umask=000 0 0
```This will mount the partition with access to everyone but in a location (/mnt/Win7) that will not show up under Places.

If you don't want anyone to access the partition at all then you could modify the "umask option":
```
/dev/sda1 /mnt/Win7 ntfs defaults,nls=utf8,umask=777 0 0
```This will put Win7 in a location that doesn't show up under Places and is not accessible to anyone.

So if you wanted to implement any of these recommendations specific to your hardware you need to follow these steps:

*Create the /mnt/Win7 mount point:*
```
sudo mkdir /mnt/Win7
```*Determine the partition identifier of the 1TB drive ( to make sure it's really at /dev/sda1 ):*
```
sudo blkid -c /dev/null
```*Edit /etc/fstab as root:*
```
gksu gedit /etc/fstab
```Add the new fstab line.

After you save the fstab run the following command to run the new fstab and check for errors:
```
sudo mount -a
```

---

