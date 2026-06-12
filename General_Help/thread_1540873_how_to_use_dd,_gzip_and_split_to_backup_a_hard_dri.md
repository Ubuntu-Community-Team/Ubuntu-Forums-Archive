---
title: "how to use dd, gzip and split to backup a hard drive to a usb stick"
date: 2010-07-28
forum: General Help
---

### Post by art2003 on 2010-07-28
First Boot any linux live cd
```

(Optional: but highly recommended as it will help creating a much smaller image)

```

Otherwise the dd command will dump the bits of even the files that where previously deleted.

Empty out the unused blocks of your hard disk with zeros, using command:

```

sudo dd if=/dev/zero of=/tmp/bigfilefullofzeros && rm /tmp/bigfilefullofzeros

```

Unmount the source file system

```

If you don't know how to to this step, stop immediately and go no further

```


Create the compressed image:

From a terminal change directory to the folder in your external usb drive or NFS volume where you want to dump the backup

```

su -
dd if=/dev/sda conv=sync,noerror bs=64K | gzip -c | split -b 2000m - ./system_drive_backup.img.gz

```

It will create 2GB files in this fashion:

system_drive_backup.img.gz.aa
system_drive_backup.img.gz.ab
system_drive_backup.img.gz.ac
...
etc, etc
 

"dd" is the command to make a bit-by-bit copy of "if=/dev/sda" as the "Input File" to "of=/mnt/sda1/sda.img.gz" as the "Output File". Everything from the partition will go into an "Output File" named "sda.img.gz". "conv=sync,noerror" tells dd that if it can't read a block due to a read error, then it should at least write something to its output of the correct length. Even if your hard disk exhibits no errors, remember that dd will read every single block, including any blocks which the OS avoids using because it has marked them as bad. "bs=64K" is the block size of 64x1024 Bytes. Using this large of block size speeds up the copying process. The output of dd is then piped through gzip to compress it and in turn piped to split in order to split it in 2gb chunks which fit nicely on FAT32 drives



To restore the image:
```

su -
cat system_drive_backup.img.gz.* | gzip -dc | dd of=/dev/sda conv=sync,noerror bs=64K

```

[edit]
Storing extra information about the drive geometry necessary in order to interpret the partition table stored within the image
```

fdisk -l /dev/sda > /mnt/sda1/hda_fdisk.info

```

NOTE: I do not claim credit for this, I have just put together this stuff from info on the web

---

