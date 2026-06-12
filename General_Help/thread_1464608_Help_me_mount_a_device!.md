---
title: "Help me mount a device!"
date: 2010-04-28
forum: General Help
---

### Post by houshdaran on 2010-04-28
Hi.
I typed thus at the terminal:
> soheil@soheil-PC:/dev$ sudo mount /dev/sda5 /media/hand got such a message:> 
mount: /dev/sda5 is not a block deviceWhy is it?I "mkdired" /media/h previously.see:
> soheil@soheil-PC:~$ sudo mkdir /media/h
and, 
> soheil@soheil-PC:~$ cd /media
soheil@soheil-PC:/media$ ls
cdrom  cdrom0  cdrom1  floppy  floppy0  h  m  new  toshia  toshiba
So why do I get error?I'm running ubuntu 9.10

---

### Post by dino99 on 2010-04-28
install MountManager (search into synaptic) and tweak the rights settings as you need.

---

### Post by rukiaEnix on 2010-04-28
first make sure your device is /dev/sda5
you can know what devices are available by typing in terminal:
```

sudo fdisk -l

```there you can see wich is the real name of the device you want to mount

---

### Post by houshdaran on 2010-04-28
Hi.
> **rukiaEnix said:**
> first make sure your device is /dev/sda5
you can know what devices are available by typing in terminal:
```

sudo fdisk -l

```there you can see wich is the real name of the device you want to mount
Welll, I don't see /dev/sda5 when fdisk -l ;ut I saw it when ls'ed  in the /dev directory

Can you help me in ubuntu forensics?I had some ebooks on my computer and want to get them back, like by using "foremost" and/or "scalpel"

---

### Post by quadproc on 2010-04-28
> **houshdaran said:**
> Hi.
I typed thus at the terminal:
...
So why do I get error?I'm running ubuntu 9.10
You may need to set appropriate permissions and ownership for your new directory.  The owner and group should be root and the permissions should be appropriate for the intended usage.

I think that you will also need to specify the filesystem type in the mount command.  For example, mount -t ext3 /dev/sdXY /media/h; substitute your filesystem type instead of ext3.

quadproc

---

