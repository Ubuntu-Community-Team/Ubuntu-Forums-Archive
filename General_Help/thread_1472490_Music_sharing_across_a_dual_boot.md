---
title: "Music sharing across a dual boot"
date: 2010-05-04
forum: General Help
---

### Post by Shanty on 2010-05-04
I'm considering DBing Windows 7 with Ubuntu; I need 7 so that I can run CAD.  However, for entirely un-work related reasons, I'd also like to be able to access my music files through both OSes without having to make a copy of all the files on each OS.  There's a way to do this on XP, but is there any way to share music files with a 7/Ubuntu combo?

---

### Post by TommyBrunn on 2010-05-04
I believe there is an EXT3/4 driver for Windows, so if you install that and keep your music on your Ubuntu-partition, you should be able to access it from both OSs. Of course, you could also store the music on the Windows partition, as Ubuntu can read and write to NTFS partitions.

---

### Post by mb_webguy on 2010-05-04
Ubuntu works well with NTFS filesystems (and Windows can read ext2/3 filesystems with a third-party driver), so all you need to do is create a separate partition (I'd suggest NTFS) and mount it in both OSes.  I'd mount it under the /mnt directory in linux rather than just the ~/Music directory, since that way you can use it to share more than just music.  For example, I use a shared NTFS partition for my Documents, Music, Pictures, and Videos.  I have the partition mounted as /mnt/shared in linux and as the D drive in Windows.  I changed the location of those folders in my Windows user folder to those folders on the D drive, and replaced the directories in my linux home directory to symlinks pointing to those directories in /mnt/shared.  So I don't have to do anything special to access my data from whatever OS I happen to be using.  My documents will always be in my Documents folder/directory, my videos will always be in my Videos folder/directory, etc.

---

### Post by indytim on 2010-05-04
> I believe there is an EXT3/4 driver for Windows, so if you install that and keep your music on your Ubuntu-partition, you should be able to access it from both OSs. Of course, you could also store the music on the Windows partition, as Ubuntu can read and write to NTFS partitions.

Last time I checked (a couple of months ago), the ext3/4 driver did not play at all in Windows 7.

Go for the NTFS formatted partitions and all will be happy in both worlds.

-IndyTim / DataMan

---

### Post by WorMzy on 2010-05-04
What I do is have a terabyte NTFS partition for all the media I want to share between OS'. I mount that immediately after boot with fstab, and then use bind options to make my corresponding home folders (e.g. /home/wormzy/Downloads, /home/wormzy/Pictures, etc) link to folders on that partition.

So my fstab looks like this:
```

UUID=7A5C94995C94522D                     /media/Terastore        ntfs user,uid=1000,gid=1000,umask=007,dmask=007,fmask=007,exec,rw 0 0
/media/Terastore/Collection/              /home/wormzy/Collection none bind                                                         0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none bind                                                         0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none bind                                                         0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none bind                                                         0 0
/media/Terastore/Videos/                  /home/wormzy/Videos     none bind                                                         0 0

```

---

