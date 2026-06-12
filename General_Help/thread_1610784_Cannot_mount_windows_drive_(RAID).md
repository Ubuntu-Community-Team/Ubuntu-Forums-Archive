---
title: "Cannot mount windows drive (RAID)"
date: 2010-11-01
forum: General Help
---

### Post by Milk Rulz on 2010-11-01
Hey I've just installed ubuntu 10.10 (64bit) on my 1TB drive where as I have my windows drives on a seperate 2x 1TB drives in RAID and am not exactly sure how to mount it.

I am not finding it under computer or under NTFS configuration tool and when I click mount under storage device manager it does nothing, although does detect the RAID array as /dev/sda2


All help is appreciated, thanks.

---

### Post by cbraxton on 2010-11-01
> **Milk Rulz said:**
> Hey I've just installed ubuntu 10.10 (64bit) on my 1TB drive where as I have my windows drives on a seperate 2x 1TB drives in RAID and am not exactly sure how to mount it.

I am not finding it under computer or under NTFS configuration tool and when I click mount under storage device manager it does nothing, although does detect the RAID array as /dev/sda2

All help is appreciated, thanks.

What you probably have is motherboard-based fake RAID. It is possible to mount fake RAID under Linux but you need to use the command line. If you don't have the "dmraid" program installed, execute "apt-get install dmraid" as root, then run the following (also as root):

1. Find the RAID devices:

```

  dmraid -r
      /dev/sdb: isw, "isw_jbifjjgg", GROUP, ok, 488397166 sectors, data@ 0
      /dev/sdc: isw, "isw_jbifjjgg", GROUP, ok, 488397166 sectors, data@ 0

```

2. Activate the RAID device in /dev/mapper:
```

dmraid -ay -v
     INFO: Activating group RAID set "isw_jbifjjgg"
     INFO: Activating partition RAID set "isw_jbifjjgg_RAID_Volume01"

```

3. Mount the RAID device:
```

mount /dev/mapper/isw_jbifjjgg_RAID_Volume01 /mnt/mountpoint

```

This is from a guide I found and saved some time ago, the output shown is of course a sample and your RAID device names will vary.

---

### Post by Swiftjay on 2010-11-01
> **Milk Rulz said:**
> Hey I've just installed ubuntu 10.10 (64bit) on my 1TB drive where as I have my windows drives on a seperate 2x 1TB drives in RAID and am not exactly sure how to mount it.

I am not finding it under computer or under NTFS configuration tool and when I click mount under storage device manager it does nothing, although does detect the RAID array as /dev/sda2


All help is appreciated, thanks.


do it in the terminal, some of those gui applications to mount are really bad and unreliable.

In terminal you should first make a directory so it know's where to mount too.

so: mkdir /mnt/Windows

You might need to do sudo mkdir /mnt/Windows if it doesn't allow you to.

Now, you need to mount the drive. type sudo /dev/sda2 /mnt/Windows

If it has problems mounting the drive it will let you know, post any errors you have.

If it works then you can set up the fstab to mount it every time you load up windows to do this do sudo vim /etc/fstab  (you'll need to install vim, I don't suggest using VI as it's a bit weird you can do this by sudo apt-get install vim, you could alternatively use sudo gedit /etc/fstab  But i use vim because it colour co-ordinates everything letting you know if it's in the right area or not)

go to where there's a blank space in the bottom and type:


/dev/sda2       /mnt/Windows ntfs

make sure you press tab after doing /dev/sda2 and a tab after /mnt/Windows to give them an optimal space that fstab can read it.

After doing that it will auto mount the hard drive on startup.

*edit* just saw the guy post before me haha.  That raid guide is quite useful.. I will add that to my documents for the future with any raid mounting.  His option is probably the best to choose out of both of us.

---

### Post by ronparent on 2010-11-01
Just a note: In 10.10 it is no longer necessary to separately mount the raid partitions. They will be immediately seen after activated under Places>Computer and will be automatically mounted when selected.

---

