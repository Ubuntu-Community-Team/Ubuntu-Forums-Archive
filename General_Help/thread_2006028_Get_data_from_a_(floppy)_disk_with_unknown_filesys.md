---
title: "Get data from a (floppy) disk with unknown filesystem"
date: 2012-06-18
forum: General Help
---

### Post by DeShark on 2012-06-18
Hi all,

I've got a floppy disk with an unknown filesystem. It's from a computer which controls and old bit of industrial factory equipment.

Basically, there are some recipes on the floppy that I'd like to extract, but the filesystem is possibly custom-made for this application.

Is there any way of extracting any useful information from the disk? Maybe using dd or strings or something similar?

I'm using a usb floppy drive (which I think is at /dev/sdc) and I've tried dd:

```
# dd if=/dev/sdc
0+0 records in
0+0 records out
0 bytes (0 B) copied, 6.7061e-05 s, 0.0 kB/s
```

but it doesn't seem to work. I've also tried:

```
# strings /dev/sdc
```

but again... no luck.

Any ideas?

---

### Post by HermanAB on 2012-06-18
Plug it in, then run dmesg to see what device it is.  After that, use dd to write it to a file and read the file with hexedit.

---

### Post by DeShark on 2012-06-18
I ran dmesg and got:

```
[ 2525.036644] sd 6:0:0:0: [sdc] Write Protect is on
[ 2525.036649] sd 6:0:0:0: [sdc] Mode Sense: 00 46 1e 80
[ 2525.100561] sd 6:0:0:0: [sdc] No Caching mode page present
[ 2525.100566] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2525.356401] sd 6:0:0:0: [sdc] READ CAPACITY failed
[ 2525.356406] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2525.356409] sd 6:0:0:0: [sdc]  Sense Key : Medium Error [current] 
[ 2525.356413] sd 6:0:0:0: [sdc]  Add. Sense: Cannot read medium - unknown format
[ 2525.484323] sd 6:0:0:0: [sdc] No Caching mode page present
[ 2525.484328] sd 6:0:0:0: [sdc] Assuming drive cache: write through
```

Running dd if=/dev/sdc gave me the output posted above... :confused:

---

