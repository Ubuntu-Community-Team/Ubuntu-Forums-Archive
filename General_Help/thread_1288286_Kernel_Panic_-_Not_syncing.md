---
title: "Kernel Panic - Not syncing"
date: 2009-10-11
forum: General Help
---

### Post by mac666 on 2009-10-11
Hey
Yesterday, i removed a faulty HDD.
After this i couldnt boot my ubuntu - 
At start screen, it freezes

In recovery mode it says:
```
Stale NFS file handle
Kernel Panic - Not Syncing ( Or something )
```

I can explorer the filesystem from livecd / another installation....

I have tried to switch the RAM modules, but same thing...
Windows Vista x64 and ubuntu x32 works great on same computer, but the ubuntu x64 wont boot (My regular OS) :(


Any ideas?

---

### Post by NoaHall on 2009-10-11
It's because you've removed the drive with important files on. Did you set it up so your / and /home where on different partitions?

---

### Post by hantechbl on 2009-10-11
Your old hdd had a very important folder.  Reinsert that drive on the same cable it was and make sure your bios settings are the same as they were before you removed your old drive.  Then you should boot into recovery mode and run the check disk option.  Make a image of the bad drive and store it on your main hdd. Remove your bad drive and insert a new drive.  Boot with a live cd and put  the image onto the new hdd.  
If you have the unlikely event where you can't do anything with the old drive you're out of luck.
P.S. Most of the step I just showed you is what date recovery employees do.  In simple words, They get the image and extract the image to a new drive.

---

### Post by mac666 on 2009-10-11
The HDD was a new hdd which i didnt use, and it didnt have any folders or anything...
After installing it again it works with other ubuntu installations, but still cant boot the other...
I have no idea on how to make images et c?
I cant boot into recovery mode, i get "stale NFS file handle" error
And its not the RAM that is bad...

---

### Post by hantechbl on 2009-10-11
> **mac666 said:**
> The HDD was a new hdd which i didnt use, and it didnt have any folders or anything...
After installing it again it works with other ubuntu installations, but still cant boot the other...
I have no idea on how to make images et c?
I cant boot into recovery mode, i get "stale NFS file handle" error
And its not the RAM that is bad...
Nevermind make an image thing.
the problem is that you have a mount point there.....
try this: [http://sysunconfig.net/unixtips/stale_nfs.txt](http://sysunconfig.net/unixtips/stale_nfs.txt)

---

### Post by mac666 on 2009-10-11
Can i do that from the livecd?

---

### Post by hantechbl on 2009-10-11
Oops, you can't.
I would try to use the live cd to backup the your important files and reinstall ubuntu without the bad hdd inserted.

---

### Post by mac666 on 2009-10-11
This is what i got...


ubuntu@ubuntu:~$ sudo fsck -f -p -c -v /dev/sda7
fsck 1.41.4 (27-Jan-2009)
/dev/sda7: Updating bad block inode.

  216517 inodes used (2.28%)
   12487 non-contiguous files (5.8%)
     198 non-contiguous directories (0.1%)
         antal inoder med ind/dind/tind-block: 20063/336/1
13903078 blocks used (36.65%)
       0 bad blocks
       5 large files

  173325 regular files
   20044 directories
      69 character device files
      26 block device files
       3 fifos
     506 links
   23039 symbolic links (22069 fast symbolic links)
       2 sockets
--------
  217014 files


Any ideas?

---

### Post by mac666 on 2009-10-11
Wops! Seems as my /etc folder is gone? :S
When i mounted it and was to cd into /media/disk/etc - i cant get in...
LS Gives me:
bin    home            lib32       mnt   sbin     tmp      vmlinuz.old
boot   initrd.img      lib64       opt   selinux  usr
cdrom  initrd.img.old  lost+found  proc  srv      var
dev    lib             media       root  sys      vmlinuz


No ETC! :O

Is that Weird?!

---

