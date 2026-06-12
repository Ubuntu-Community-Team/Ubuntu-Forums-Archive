---
title: "Ubuntu Linux 10.04.4"
date: 2012-05-28
forum: General Help
---

### Post by dabonz on 2012-05-28
Hello,

Question I have 4 Additional HDD on my Linux Server  That I haven't been mounted 
I have installed Apache and Webmin and Samba .

Question How can I mount my 4 Drives so I can see them so I can share to my windows pc

I connect to my Linux Server via putty I have no Geographical interface 

Feedback much Appreciated

Dabonz

---

### Post by maverickaddicted on 2012-05-28
> **dabonz said:**
> Hello,

Question I have 4 Additional HDD on my Linux Server  That I haven't been mounted 
I have installed Apache and Webmin and Samba .

Question How can I mount my 4 Drives so I can see them so I can share to my windows pc

I connect to my Linux Server via putty I have no Geographical interface 

Feedback much Appreciated

Dabonz

Identify the connected hdd to your server use this command -
```
sudo fdisk -l
```
After that use mount command to mount them. If you have any problem, post the output of fdisk -l command, to get more help.

---

### Post by dabonz on 2012-05-28
Hi thanks for your reply

when I do that sudo fdisk -l  >>>>>> Unable to seek on /dev/sda

---

### Post by zero2xiii on 2012-05-28
Hay,

A quick how to will be:

```
sudo fdisk -l
```
To get the drives list.
Note the location such as /dev/sda etc... for the unmounted drives
```
sudo blkid
```
To get the UUIDs acociated by with the unmounted drives.

Now add these devices into fstab:

```
gksudo gedit /etc/fstab
```

An example entry will look like this:
> UUID=208a62f6-ddc9-4108-9c30-ac98e839c704 /home/Music     ext2    defaults        0       2

Check the man page for fstab
```
man fstab
```
for details on the syntax. But basicly that is self explanitory. Just leave the 0 and 2, and change the UUID, mount location, and format to what ever your drives are and it should mount without any issues.

Cherz

EDIT: Snap hahaha typed a bit to slowly it seemed :D

---

### Post by dabonz on 2012-05-28
Hi, Thanks For your reply

Yeah I don't want to format these drive there is data containing on them I just want to be able to share them to my windows pc from the linux sever




the list hdd I would like to mount and share them drive to my windows pc

/dev/sdb1: LABEL="WDC_RAPTOR" UUID="A0D42D0CD42CE66E" TYPE="ntfs"
/dev/sdc1: LABEL="WDC_640GB" UUID="F8D057C8D0578BAE" TYPE="ntfs"
/dev/sdd1: LABEL="WDC_1TB" UUID="EA44FA3E44FA0CD7" TYPE="ntfs"

gksudo gedit /etc/fstab  >>>>>>>>>>>> (gksudo:9549): Gtk-WARNING **: cannot open display:

---

### Post by steeldriver on 2012-05-28
if you are using a simple puTTY session then 'gksudo gedit' isn't going to work for you since it is trying to invoke a graphical editor

you will need to use a command line editor e.g. 

```
sudo vi
``````
sudo nano
```iirc the default install only includes the samba **client** portions so once the drives are mounted, if you want to share **from** the ubuntu box **to** windows you will need to install and setup samba server

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by dabonz on 2012-05-28
Thanks a lot for your reply's 

I have samba installed already

 [SIZE=+2]Samba Windows File Sharing[/SIZE]
Samba version 3.4.7

I just need to mount those 3 drives

---

### Post by dabonz on 2012-05-28
sorry did not mean to double post

---

### Post by maverickaddicted on 2012-05-29
> **dabonz said:**
> Hi, Thanks For your reply

Yeah I don't want to format these drive there is data containing on them I just want to be able to share them to my windows pc from the linux sever
the list hdd I would like to mount and share them drive to my windows pc

/dev/sdb1: LABEL="WDC_RAPTOR" UUID="A0D42D0CD42CE66E" TYPE="ntfs"
/dev/sdc1: LABEL="WDC_640GB" UUID="F8D057C8D0578BAE" TYPE="ntfs"
/dev/sdd1: LABEL="WDC_1TB" UUID="EA44FA3E44FA0CD7" TYPE="ntfs"

gksudo gedit /etc/fstab  >>>>>>>>>>>> (gksudo:9549): Gtk-WARNING **: cannot open display:

Have you tried mount command?
1) ```
sudo mkdir /mnt/wdcraptor/
```

2) a) Install fuse and ntfs-3g in your server.
   b) Then use this command to mount it -
```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/wdcraptor/
```

If you are able to mount all your drive, then you can edit /etc/fstab using this command -

```
sudo nano /etc/fstab/
```

**Do not use gedit; read steeldriver post.**

You can get more details about mounting partition here -

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by zero2xiii on 2012-05-29
> **steeldriver said:**
> if you are using a simple puTTY session then 'gksudo gedit' isn't going to work for you since it is trying to invoke a graphical editor



Snap sorry. I missed the no GUI part... You need to then use a terminal editor that is correct.


> Yeah I don't want to format these drive there is data containing on them I just want to be able to share them to my windows pc from the linux sever

I did not mean you should format it. The current format of the drive, or filesystem of the drive, has to be listed inside fstab.

Adding the entries to fstab will also mount them everytime the computer boots. If you want to share the drives for a limited time or only a once off, use a mount command, or script.

Cherz

---

