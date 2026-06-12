---
title: "Issues trying to dual boot with windows XP"
date: 2009-12-31
forum: General Help
---

### Post by Amatocianmonk on 2009-12-31
I have been trying to play Half-Life 2 on Ubuntu using Steam through Wine. 
Steam installed just fine but half-life 2 won't play. Long story short, its an issue with the graphics card and wine, blah blah. 
As a simple solution I want to dual boot with windows XP simply for game playing reasons.

I was following this tutorial to dual boot with xp
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

However, when I boot off the ubuntu live CD and try to use the partition editor to resize the ubuntu partition to make space for the windows installation, GParted ends with an error

More specifically ```
Input/Output error during read on /dev/sda
```And more specifically 
```

GParted 0.4.3
 Libparted 1.8.8
    **Move /dev/sda1 to the right**  01:44:21    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 561616397
size: 561616335 (267.80 GiB)[/I]          calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )             [I]requested start: 46170810
requested end: 607787144
requested size: 561616335 (267.80 GiB)[/I]       [I]new start: 46170810
new end: 607787144
new size: 561616335 (267.80 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:04:41    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda1***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  190010 inodes used (1.08%)
    1916 non-contiguous files (1.0%)
     194 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 10631/1143/0
 5756129 blocks used (8.20%)
       0 bad blocks
       1 large file

  146366 regular files
   25051 directories
      69 character device files
      26 block device files
       4 fifos
     398 links
   18477 symbolic links (16917 fast symbolic links)
       8 sockets
--------
  190399 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             move file system to the right  01:39:40    ( ERROR )             perform read-only test  01:39:40    ( ERROR )             using internal algorithm       read 561616335 sectors       finding optimal blocksize             read 65536 sectors using a blocksize of 128 sectors  00:00:03    ( SUCCESS )             *65536 of 65536 read*       *2.78545 seconds*          read 65536 sectors using a blocksize of 256 sectors  00:00:02    ( SUCCESS )             *65536 of 65536 read*       *2.67603 seconds*          read 65536 sectors using a blocksize of 512 sectors  00:00:03    ( SUCCESS )             *65536 of 65536 read*       *2.53064 seconds*          read 65536 sectors using a blocksize of 1024 sectors  00:00:02    ( SUCCESS )             *65536 of 65536 read*       *1.96418 seconds*          read 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )             *65536 of 65536 read*       *1.71961 seconds*          read 65536 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )             *65536 of 65536 read*       *1.40022 seconds*          read 65536 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS )             *65536 of 65536 read*       *1.25703 seconds*          read 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )             *65536 of 65536 read*       *1.10539 seconds*          read 65536 sectors using a blocksize of 32768 sectors  00:00:02    ( SUCCESS )             *65536 of 65536 read*       *1.10226 seconds*          read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )             *65536 of 65536 read*       *1.2034 seconds*          optimal blocksize is 32768 sectors (16.00 MiB)          read 560960975 sectors using a blocksize of 32768 sectors  01:39:22    ( ERROR )             *555685327 of 560960975 read*       *Error while reading block at sector 5242943*          556340687 sectors read             libparted messages    ( INFO )             *Input/output error during read on /dev/sda*          ========================================
 
```

Any ideas?

---

### Post by gsmanners on 2009-12-31
I/O errors most likely mean hardware failure. Whether it's a bad drive, a bad cable, or the computer's interface to the drive going bad (or a combination thereof) is unknown.

If you take your computer to a hardware technician, they will more than likely look for the cause by simply swapping out the cable and the drive to see what works. If a new cable and a new drive don't work, then it's most likely the interface.

---

### Post by Amatocianmonk on 2010-01-01
That is odd because everything else works just fine on the computer and i was able to do other things to the partitions, its just resizing the ubuntu partition

---

### Post by gsmanners on 2010-01-01
Well, it doesn't have to be a bad drive per se to give you errors, I suppose. Some drives just can't handle problems with specific parts of the media. Resizing a drive is a bit like defragmenting a drive. That is, they assume that the space allocated by the drive controller is an error-free region.

The upshot of all this is: backup your data and reformat. Those type of errors aren't the kind you can afford to ignore, and you can't code your way around them (at least not that I know of).

---

