---
title: "Recover deleted file"
date: 2010-05-01
forum: General Help
---

### Post by mckinnon81 on 2010-05-01
Hi;

I am trying to recover a file that was deleted via fsck.

Running debugfs shows that the file is still possibly available:
```

5333037   40755 (2)   1000   1000    4096 16-Apr-2010 16:30 .
 5332995   40755 (2)   1000   1000    4096 12-Apr-2010 10:08 ..
      0       0 (1)      0      0       0                   Windows XP.vdi
```


But with out an indode I cannot undelete it via debugfs

Cab anyone give me any tips or help in recovering the missing file?

The filesystem is EXT2

Thanks
Matt

---

### Post by mckinnon81 on 2010-05-02
BUMP

Any help is really appreciated.

Thanks

---

### Post by dino99 on 2010-05-02
use cgsecurity.org tools

---

### Post by mckinnon81 on 2010-05-02
Thanks for the reply dino. I have tried both testdisk and photorec but no luck.

Using debugfs i did a dump of the directory the file was in.

```
 5332995   40755 (2)   1000   1000    4096 12-Apr-2010 10:08 .
 5332994   40755 (2)   1000   1000    4096 30-Apr-2010 09:44 ..
 5333037   40755 (2)   1000   1000    4096 16-Apr-2010 16:30 HardDisks
 5341201   40755 (2)   1000   1000    4096 16-Apr-2010 16:29 Machines
 5332998  100600 (1)   1000   1000    2743 30-Apr-2010 08:57 VirtualBox.xml
 5333039  100644 (1)   1000   1000    1236 12-Apr-2010 10:08 compreg.dat
 5333040  100644 (1)   1000   1000   14142 12-Apr-2010 10:08 xpti.dat

debugfs: dump <5333037> /tmp/dirdata


```


Now by using hexdump I can see the file exists but is not 'pointed' to.

```

#  hexdump -C dirdata

00000000  2d 60 51 00 0c 00 01 02  2e 00 00 00 03 60 51 00  |-`Q..........`Q.|
00000010  2c 00 02 02 2e 2e 00 00  00 00 00 00 20 00 16 01  |,........... ...|
00000020  2e 57 69 6e 64 6f 77 73  20 58 50 2e 76 64 69 2e  |.Windows XP.vdi.|
00000030  33 38 68 70 67 65 00 00  00 00 00 00 c8 0f 0e 01  |38hpge..........|
00000040  57 69 6e 64 6f 77 73 20  58 50 2e 76 64 69 00 00  |Windows XP.vdi..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00001000
```


By using this hex how can i find the previous inode to modify as mentioned here:

For example under Linux ext2fs it is quite easy (this
is documented in a mini-howto from linuxdoc):

1. Unmount the filesystem.
2. Start "debugfs".
3. Walk to the directory.
4. Dump the directory content data
   (debugfs: dump <inode of directory> /tmp/dirdata).
5. Exit debugfs.
[B]6. Load the data into a hexeditor.
7. Check the inode of my deleted file (it is still
there in the directory data, only the "pointer" to the
next entry in the directory has increased so it now
points after my deleted file's directory entry).[/B]
8. Start debugfs again.
9. Add the file to a directory under a certain name
with the old inode number (debugfs: modify_inode
<inode of my deleted file>)
10. Set deletion time to 0 and link count to 1.
11. Dump my deleted file
    (debugfs: dump <inode of my deleted file> /tmp/mydeletedfile)

---

### Post by mckinnon81 on 2010-05-02
BUMP again.

Anybody at all go any ideas?

---

### Post by Omar.Fayyad on 2011-08-06
I dont know if you finally solved your problem or not but i do have similar issue and i need urgent help :(!!

Look i have a similar problem, actually i mistakenly deleted a 'vdi' and a 'sav' and these where snapshots but i still have the vdi and i am not able to start the image again..

Can you help in this matter

QUOTE=mckinnon81;9210696]Hi;

I am trying to recover a file that was deleted via fsck.

Running debugfs shows that the file is still possibly available:
```

5333037   40755 (2)   1000   1000    4096 16-Apr-2010 16:30 .
 5332995   40755 (2)   1000   1000    4096 12-Apr-2010 10:08 ..
      0       0 (1)      0      0       0                   Windows XP.vdi
```
But with out an indode I cannot undelete it via debugfs

Cab anyone give me any tips or help in recovering the missing file?

The filesystem is EXT2

Thanks
Matt[/QUOTE]

---

