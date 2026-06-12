---
title: "Trouble mounting a floppy"
date: 2011-11-23
forum: General Help
---

### Post by /bin/sh on 2011-11-23
I am making an os in assembly and have made the basic parts of the bootloader and the kernel. I have made a floppy with:
```

mkdosfs -C /path/to/my/floppy.flp 1440

```
and then copyed the bootloader:
```

dd status=noxfer conv=notrunc if=/path/to/bootloader.bin of=/path/to/floppy.flp

```
but now I want to copy the kernel and other stuff to the floppy by mounting it on a directory. I tried:
```

mount -t vfat /path/to/floppy.flp /path/to/mountpoint

```
but it shows this error message:
```

mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Can anyone help!
Thanks in advance.

---

### Post by dino99 on 2011-11-23
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by /bin/sh on 2011-11-23
Tried all of that, same error.

---

