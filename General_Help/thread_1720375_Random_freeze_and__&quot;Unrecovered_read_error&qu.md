---
title: "Random freeze and  &quot;Unrecovered read error&quot; in /var/log/messages"
date: 2011-04-03
forum: General Help
---

### Post by Naggobot on 2011-04-03
System is Acer 5020 laptop with 32 bit Ubuntu 10.04 Lucid. 

I have following "smallish" problem. System freezes suddenly for a few seconds and after the freeze if I run following command to prompt

```
tail -n 100 /var/log/messages
```I can find a following possibly related error

```

....
Apr  3 08:18:09 acer5020-laptop kernel: [ 1383.202090] ata1.00: configured for UDMA/100
Apr  3 08:18:09 acer5020-laptop kernel: [ 1383.202113] ata1: EH complete
Apr  3 08:18:13 acer5020-laptop kernel: [ 1387.568764] ata1.00: configured for UDMA/100
Apr  3 08:18:13 acer5020-laptop kernel: [ 1387.568786] ata1: EH complete
Apr  3 08:18:17 acer5020-laptop kernel: [ 1391.888898] ata1.00: configured for UDMA/100
Apr  3 08:18:17 acer5020-laptop kernel: [ 1391.888919] ata1: EH complete
Apr  3 08:18:22 acer5020-laptop kernel: [ 1396.232745] ata1.00: configured for UDMA/100
Apr  3 08:18:22 acer5020-laptop kernel: [ 1396.232768] ata1: EH complete
Apr  3 08:18:26 acer5020-laptop kernel: [ 1400.620733] ata1.00: configured for UDMA/100
Apr  3 08:18:31 acer5020-laptop kernel: [ 1400.620755] ata1: EH complete
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928748] ata1.00: configured for UDMA/100
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928770] sd 0:0:0:0: [sda] Unhandled sense code
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928773] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928778] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928784] Descriptor sense data with sense descriptors (in hex):
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928786]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928797]         02 3c 5e 1b 
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928801] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Apr  3 08:18:31 acer5020-laptop kernel: [ 1404.928808] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 02 3c 5e 17 00 00 08 00
...
```Any recommendations on if this is fixable or is it broken hardware and if so do I assume right that it is the hard drive or related controller(s)?

Any recommendation on how to fix? (New HDD or totally new computer?)

---

### Post by Naggobot on 2011-04-03
dmesg seems to report a faulty sector or am I wrong?

```
[  362.926160]          res 51/40:00:1b:5e:3c/00:00:00:00:00/e2 Emask 0x9 (media error)
[  362.926168] ata1.00: status: { DRDY ERR }
[  362.926174] ata1.00: error: { UNC }
[  362.948881] ata1.00: configured for UDMA/100
[  362.948910] sd 0:0:0:0: [sda] Unhandled sense code
[  362.948915] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  362.948924] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  362.948934] Descriptor sense data with sense descriptors (in hex):
[  362.948940]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  362.948960]         02 3c 5e 1b 
[  362.948969] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  362.948981] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 02 3c 5e 17 00 00 08 00
[  362.949000] end_request: I/O error, dev sda, sector 37510683
[  362.949036] ata1: EH complete

```

---

### Post by Naggobot on 2011-04-04
Booted from LiveCD and run

```
sudo e2fsck -c /dev/sda1
```Output

```

e2fsck 1.41.11 (14-Mar-2010)
Checking for bad blocks (read-only test): done                                
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 263829: 4688768 4688827 4688828 4688829 4688830 4688831 4688833
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

File /home/acer5020/.mozilla/firefox/byjwr43s.default/urlclassifier3.sqlite (inode #263829, mod time Sun Apr  3 15:46:47 2011) 
  has 7 multiply-claimed block(s), shared with 1 file(s):
    <The bad blocks inode> (inode #1, mod time Sun Apr  3 16:24:36 2011)
Clone multiply-claimed blocks<y>? yes

Error reading block 4688827 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 4688828 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 4688829 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 4688830 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 4688831 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 4688833 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #0 (22362, counted=22355).
Fix<y>? yes

Free blocks count wrong for group #143 (4343, counted=4350).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 247030/9535488 files (0.9% non-contiguous), 23772515/38132277 blocks


```I have no idea what are > multiply-claimed blocks and [I tried asking about it]("http://ubuntuforums.org/showthread.php?t=1720686") but it seems that the info is not extremely common or I did not ask in correct way. There are a lot of references in Google but explanations are hard to come by. 

After the above I ran 

> sudo e2fsck -c -c -p -v /dev/sda1Output

> /dev/sda1: Updating bad block inode.

  247030 inodes used (2.59%)
    1929 non-contiguous files (0.8%)
     367 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 215395/266/3
23772508 blocks used (62.34%)
       0 bad blocks
       1 large file

  184991 regular files
   23532 directories
      68 character device files
      26 block device files
       0 fifos
     526 links
   38399 symbolic links (31257 fast symbolic links)
       5 sockets
--------
  247547 files
Which I think seems to be OK? Any how now it remains to be seen if the problem still persists.

---

### Post by Naggobot on 2011-04-04
Seems to be OK at least for now. No more freezes and no more errors in either dmesg or /var/log/messages. 

Marking thread as solved. 

Short post script:
When running the e2fsck -c option makes read test and -c -c option makes read/write test. Also note that file system has to be unmounted when running the file system check. I had to use the e2fsck since plain fsck did nothing for the file system. I do not know if it was a user error or some other reason. 

Warning: running the

```
sudo e2fsck -c -c -p -v /dev/sda1                      
```took a huge amount of time and there was no progress indicator even though the option -v was selected. So wait wait wait, do not interrupt since the program is performing read-write cycles. 

Note that for you the /dev/sda1 may be something different. Mount the disk first and use command mount in the terminal to see what is your disk. Then unmount and use disk check after unmonting.

---

