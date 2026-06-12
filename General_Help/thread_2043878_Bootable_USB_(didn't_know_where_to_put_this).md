---
title: "Bootable USB (didn't know where to put this)"
date: 2012-08-17
forum: General Help
---

### Post by BrianBlaze on 2012-08-17
Good morning fellow helpers!

I have a question... I am sure this is an odd one but I am looking and will continue to look for my solution but maybe someone can help. I have a bootable USB I created from windows. It works perfectly and I have installed ubuntu onto my PC. My question is I would like to mount the linux system that is on the bootable USB but I can't find it on the USB. When I do fdisk I see my USB and see the one partition for it but when I mount it I don't see the root folders just the files directly on the USB. I am curious if there is a way to chroot to my bootable USB. This is really just me wanting to know if it's possible so far no luck!

Thanks in advance!

---

### Post by CrusaderAD on 2012-08-17
I don't think Windows can mount and browse Linux partitions such as ext4 or ext3, can it?

---

### Post by Cheesehead on 2012-08-17
It depends on how you created the USB.

If you did the normal route of downloading an install .iso and converting it into a bootable USB, then mounting the image generally won't be helpful becasue you cannot save your changes. It's in the initrd file, a big squashfs blob.

If you did the uncommon route of installing an Ubuntu system onto the USB stick, then you can mount it because it's a real filesystem, and editable. The three disadvantages of this approach is that it's very slow compared to an HDD, mistakes are also persistent, and the frequent I/O may wear out a USB stick prematurely.

---

### Post by oldfred on 2012-08-17
The installer is usually a FAT formatted partition.

Why do you want to chroot into it? As an installer it is not meant to be modified. I have seen procedures on modifying an ISO before creating the installer. It does not have the same file structure as a normal install.

---

### Post by BrianBlaze on 2012-08-17
1. Create the mount points:
```

mkdir /mnt/liveusb
mkdir /mnt/squashfs
mkdir /mnt/rootfs 
```
2. Mount.
2a. The usb stick first (this can also be done in another way):
```

mount /dev/sdb1 /mnt/liveusb
```
2b. You must have a squashfs filesystem, mount it:
```

mount -t squashfs  /mnt/liveusb/LiveOS/squashfs.img  /mnt/squashfs 
```
2c. Mount the root image:
```

 mount -o loop /mnt/squashfs/LiveOS/rootfs.img /mnt/rootfs
The root filesystem is now mounted in /mnt/rootfs. 
```

To unmount:
```

umount  /mnt/rootfs
umount  /mnt/squashfs
umount  /mnt/liveusb
rmdir  /mnt/rootfs
rmdir  /mnt/squashfs
rmdir  /mnt/liveusb

```

So on my bootable USB is a squashfs file which is actually the whole linux filesystem... problem is when I mount it (2b) I get a message 
```

mount: warning: squashfs/ seems to be mounted read-only

```

So now it seems my problem is using sqashfs because the file system is coompressed so I need to decompress and then modify and then compress again :) Thanks for the responses

also I am doing this in Linux!

---

### Post by C.S.Cameron on 2012-08-17
The files that are saved on a persistent USB are stored in casper-rw.
To access these files:



```

sudo mkdir /media/casper
```


and then mount it:


```
sudo mount -o loop casper-rw /media/casper/

```

---

### Post by BrianBlaze on 2012-08-17
> **C.S.Cameron said:**
> The files that are saved on a persistent USB are stored in casper-rw.
To access these files:



```

sudo mkdir /media/casper
```


and then mount it:


```
sudo mount -o loop casper-rw /media/casper/

```

Exactly but I want to mount it and be able to make changes :)

---

### Post by Khal1d on 2012-08-17
Hmmm...

It may help if you actually state what you want to do with the USB. Just mount it and browse around?

We got a proverbial point "A" (so to speak) but no point "B" :P

---

### Post by BrianBlaze on 2012-08-17
I want to chroot on my linux box to the USB linux filesystem and have full access to my linux USB root (be able to modify and pretty much use it like it is a real linux without actually booting the USB lol sorry to be so vague but if you want to know why it's because I am crazy haha

---

### Post by Zukaro on 2012-08-17
*isn't exactly sure what you want to do*

If you need to be able to see whats on a Linux partition in Windows there's programs which can read stuff like ext4 etc (I think the program is called "ext2 explore").

If you're trying to actually use what's on the USB (run Linux) you can use a virtual machine (VirtualBox is free).

---

### Post by C.S.Cameron on 2012-08-17
> **BrianBlaze said:**
> Exactly but I want to mount it and be able to make changes :)

Once casper-rw is mounted you can make changes.
Like add files to home, etc.

Give it a try.

---

### Post by BrianBlaze on 2012-08-30
Thanks for all your help guys!

---

