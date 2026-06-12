---
title: "Stuck at Ubuntu 10.04 startup splash screen after disk checking / fix attempt"
date: 2011-01-06
forum: General Help
---

### Post by ehsanul_g3 on 2011-01-06
When starting up, my disks were being checked. After checking, it told me errors were found on '/', and gave me options "F" to attempt automatically fixing the errors, "S" to skip mounting and "M" to manually recover.

Naturally, I went with "F", which had the disk spinning for a very long time. During this time, there was a message saying something like "/tmp not mounted yet" and it said at the bottom to "wait to continue, or press "S" to skip mounting or "M" to manually recover". So I just skipped as it was taking too long. My theme had gone back to an older version, and video playback with any video player wasn't working.

So later on I restarted, and let the automatic fixing do its thing and went away. I came back and my computer was stuck on the Ubuntu loading screen, at fully loaded, but GDM would not come up with a prompt to log in.

When I restarted, I wasn't presented with my usual Grub menu, listing my other Ubuntu install, but rather it went straight to attempting to boot the system that just got messed up. This seems to indicate something wrong with the MBR? And it always gets stuck in the splash screen, as before. I manage to take a picture of what stage it was at when stuck by restarting and hitting backspace to show the text:

```

 * Starting Name Service Cache Daemon nscd
Segmentation fault
Not starting estmaster - edit /etc/default/hyperestraier and change NO_START to be 0.
 * Starting PostgreSQL 9.0 database server
acpid: exiting

```The segfault doesn't seem significant, since that's just a dns caching daemon. I don't know what estmaster is though, should I make the change suggested? 

What else can I do to recover this system? I'm currently running off an Ubuntu 10.10 live CD on the same computer, so I have access to the filesystem of the system having issues and can chroot in I suppose.

---

### Post by ehsanul_g3 on 2011-01-06
Bump (down to 4th page).

No ideas anyone??

---

### Post by ehsanul_g3 on 2011-01-06
Bump.

---

### Post by ehsanul_g3 on 2011-01-07
So I tried creating a new partition for a new Ubuntu install by resizing the current one (didn't want to get rid of it, hope I can fix it). However, it must be the same issue popping up again. Resizing fails, seemingly because of a corrupt filesystem (ext3 btw). However, e2fcsk doesn't seem to indicate issues or fix anything..

From gparted details:

```
e2fsck -f -y -v /dev/sda1
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

1113212 inodes used (24.84%)
   36897 non-contiguous files (3.3%)
   1266 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 44144/1745/1
15882140 blocks used (88.68%)
       0 bad blocks
      3 large files

  926206 regular files
  133751 directories
     113 character device files
      26 block device files
      4 fifos
     957 links
   53099 symbolic links (42655 fast symbolic links)
       4 sockets
--------
 1114160 files

e2fsck 1.41.12 (17-May-2010)

resize2fs /dev/sda1 66529248K
Resizing the filesystem on /dev/sda1 to 16632312 (4k) blocks

resize2fs 1.41.12 (17-May-2010)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
Please run *e2fsck -fy /dev/sda1* to fix the filesystem after the aborted resize operation.

```

---

### Post by Zaytoven on 2011-02-15
i'm having the same freaking problem!!!! When i pressed ignore it just takes me to that freaking splash screen all the bars fill up then it does nothing! It was working perfectly last night but after i downloaded the newest patch of updates then shut down my computer to go eat lunch then I came back and turned it on it started freaking doing this crap! I HATE COMPUTERS AND UBUNTU LOL...

---

