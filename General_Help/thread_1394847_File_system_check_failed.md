---
title: "File system check failed"
date: 2010-01-31
forum: General Help
---

### Post by Macamba on 2010-01-31
Hi,

The other day I was browsing around on my file system. Then disaster struck. I tried to open a directory, and instead of listing its contents nothing was showed. I rebooted, and got:
```

Grub loading stage 1.5

Grub loading please wait ...
Error 17

```

I solved this by reinstalling Linux, and mounting my home directory (which resided on a different partition). When I rebooted again I got a
```

File system check failed

```

I have been playing around with fsck. At one moment I got:
```

fsck /media/disk/macamba
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /media/disk/macamba

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I kept on searching, and tried:
```

sudo e2fsck -C0 -p -f -v /dev/sda9
/dev/sda9 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

```

Now I think I run out of options. Does anyone know:
[LIST=1]
[*]What happened that caused this (file system corruption)
[*]If I really have a corrupt file system
[*]What other checks I might use to pinpoint the problem
[*]What steps I need to do to get my (file) system up and running again
[/LIST]

TIA
Macamba

---

### Post by Macamba on 2010-01-31
F.W.I.W, when I reboot I get the following message on screen:
```

Runtime check on drives ...

8 % Stage 1/5, 80/668

```

Next the check fails and I get the change to correct it. I then perform the actions described before. ](*,)

---

### Post by rnerwein on 2010-01-31
hi
1. i think you haven't to reinstall your system - read this:  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
2. your problem now is - you try to run fsck on a mounted file system. just unmount it                        
    unmount /dev/sda9
3. run fsck again: fsck /dev/sda9
ciao
oh you are back - if fsck ask you to correct it type: yes 
good luck

---

### Post by Macamba on 2010-02-01
Thanks

---

