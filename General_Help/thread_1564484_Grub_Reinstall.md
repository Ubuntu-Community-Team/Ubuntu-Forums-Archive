---
title: "Grub Reinstall"
date: 2010-08-30
forum: General Help
---

### Post by dany8907 on 2010-08-30
I need help reinstalling grub. I took a look at this page [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and I followd the simplest procedure. Here is my hard drive set-up

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        9287    43142557+   5  Extended
/dev/sda3            9288        9725     3518235    c  W95 FAT32 (LBA)
/dev/sda5            3917        4038      979933+  82  Linux swap / Solaris
/dev/sda6            4039        5254     9767488+  83  Linux
/dev/sda7            5255        9287    32395041   83  Linux
        
```When I ran the steps I got this back from it.
```

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda7
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```Did I use the wrong sd?

---

### Post by cj.surrusco on 2010-08-30
You would want to install Grub to the whole hard drive and not just /dev/sda7.

So,
```
sudo grub-install --root-directory=/mnt/ /dev/sda7
```

would be changed to:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by dany8907 on 2010-08-30
I did this and I got a black screen on the next reboot. It was GNU Grub version 1.97~beta 4. It says

```

sh:grub>

```I use to have grub that displayed all my OSes. How do I get that one?

When I run 
 
```

sudo update-grub

```

I get

```

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```

---

