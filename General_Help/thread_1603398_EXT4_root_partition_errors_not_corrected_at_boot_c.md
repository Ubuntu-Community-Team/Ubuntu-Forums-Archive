---
title: "EXT4 root partition errors not corrected at boot check"
date: 2010-10-22
forum: General Help
---

### Post by Xylian on 2010-10-22
Hi,
I'm having some problems with errors reported by fsck on my EXT4 root partition on my Ubuntu 10.10 installation...
If I run fsck I get the following output:
```

# fsck -n /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Attenzione! /dev/sda1 è montato.
Attenzione: essendo un controllo a sola lettura, il journal non verrà ripristinato.
/dev/sda1 contiene un filesystem con errori, controllo forzato.
Passo 1: Controllo di inode, blocco(i) e dimensioni
Passo 2: Analisi della struttura delle directory
Passo 3: Controllo della connettività di directory
Pass 4: Controllo del numero dei riferimenti
Pass 5: Checking gruppo summary information
Numero dei blocco(i) liberi errato (12964316, contati=12961585).
Sistema? no

Numero degli inode liberi errato (4735644, contati=4735714).
Sistema? no


/dev/sda1: ********** ATTENZIONE: Il filesystem contiene ancora errori ************

/dev/sda1: 114020/4849664 files (0.3% non-contiguous), 6404132/19368448 blocks

```

Running it more than once, it shows different problems about the free inode/free blocks counters and it continuously says ATTENTION: filesystem still contain errors... I've tried to force an fsck at boot time with *touch /forcefsck*, I rebooted, it checked the filesystem and then if I execute thi fsck command I get the same errors as above... I've tried also to fsck the root partition from the Ubuntu 10.4 installation CD and it told me that there were no errors.... 

Is it normal that it finds such problems when FSCKing a mounted partition? If it is not normal, why aren't they corrected at boot fsck? Any idea?

Thanks for any help

---

### Post by dcstar on 2010-10-22
> **Xylian said:**
> 
...........
Is it normal that it finds such problems when FSCKing a mounted partition? If it is not normal, why aren't they corrected at boot fsck? Any idea?

Thanks for any help

[http://ubuntuforums.org/showpost.php?p=9922867&postcount=2](http://ubuntuforums.org/showpost.php?p=9922867&postcount=2)

---

### Post by Xylian on 2010-10-23
> **dcstar said:**
> [http://ubuntuforums.org/showpost.php?p=9922867&postcount=2](http://ubuntuforums.org/showpost.php?p=9922867&postcount=2)

That is not my problem.... My question was: if fsck does not find any error at boot and it does not find any error even if I fsck the /dev/sda1 partition from a live CD, why does it find so many errors if I run the fsck on /dev/sda1 when it is mounted? Maybe it is absolutely correct since if you run fsck on a rw-mounted partition it does not takes the journal into account and so it may find some inconsitencies that are not found at boot time since journal changes have been committed to the filesystem. So, I just wanted to know if my thesis is correct :)

---

### Post by dcstar on 2010-10-23
> **Xylian said:**
> That is not my problem.... My question was: if fsck does not find any error at boot and it does not find any error even if I fsck the /dev/sda1 partition from a live CD,** why does it find so many errors if I run the fsck on /dev/sda1 when it is mounted?**
.........

You must not ever run fsck on mounted filesystems, the message warning you about that is very clear.

---

### Post by Xylian on 2010-10-24
> **dcstar said:**
> You must not ever run fsck on mounted filesystems, the message warning you about that is very clear.

I know that, in fact I've never run it in repair mode on a mounted FS... I've run it just to check for errors... So, I think I can mark this thread as solved since errors are reported because of inconsistencies related to uncommitted journal changes..

Thanks for the info

---

