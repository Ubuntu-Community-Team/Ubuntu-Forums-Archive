---
title: "hard drive recovery"
date: 2011-05-29
forum: General Help
---

### Post by lozerfreek669 on 2011-05-29
hi big fan of multi-boot,  but when i went to install caos linux, before ubuntu it deleted my 1tb hdd, i dont have a the space to recover to, is there an in place recovery tool?

the hdd was in ntfs now is in 2 partitions ext2-or3,and swap for 512 mb total and the rest is un-partitioned, i run windows/ubuntu,any ideas would be a great help, lots of irreplaceable music

---

### Post by katykat on 2011-05-29
> **lozerfreek669 said:**
> hi big fan of multi-boot,  but when i went to install caos linux, before ubuntu it deleted my 1tb hdd, i dont have a the space to recover to, is there an in place recovery tool?

the hdd was in ntfs now is in 2 partitions ext2-or3,and swap for 512 mb total and the rest is un-partitioned, i run windows/ubuntu,any ideas would be a great help, lots of irreplaceable music

You are going to have to remove the drive (assuming you did not write any data to it, and that Linux did not actually install...). Run off a bootcd and google as much as you can on Partition Recovery Tools. Probably one good place to look is the torrents or the web for HIREN'S BOOTCD (or Paragon Disk Recovery). Hiren's may have more tools. Download and burn from a pen drive. And reinstall the drive if there is a promising utility. Read the docs. 

I used it one time *immediatley* after changing a partition, and was able to recover everything. 

If it actually formatted into ext4 and installed , the chaces are very slim of getting any  data back. Very slim.

---

### Post by wildmanne39 on 2011-05-29
> **lozerfreek669 said:**
> hi big fan of multi-boot,  but when i went to install caos linux, before ubuntu it deleted my 1tb hdd, i dont have a the space to recover to, is there an in place recovery tool?

the hdd was in ntfs now is in 2 partitions ext2-or3,and swap for 512 mb total and the rest is un-partitioned, i run windows/ubuntu,any ideas would be a great help, lots of irreplaceable music
Hi, I found a couple of programs that will let you recover files but I have not used them personally. [http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)
[http://www.google.co.uk/search?q=undelete+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=undelete+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

---

### Post by Quackers on 2011-05-29
tesdisk could be a possibility. It has worked for many :-)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Although this link may be more useful
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by oldfred on 2011-05-29
You will have to have another drive of a size large enough to store the data you recover. If the data is valuable enough to try to restore then you need the space for backups anyway.

There are not in place tools to recover data that I know of. Once you overwrote the partition table and installed a new system you overwrote all the file names & data structures.

I have used photorec to recover data. But it finds everything ever stored on drive that looks like a file. I had saved a text file many times and since I had lots of room on drive it just kept storing copies in new places. Photorec recovered just about every version I had saved and I was never sure I found the last saved. It did find my FLAC files and I was able to rename them using the internal data.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by jerrrys on 2011-05-29
testdisk is usually fast and simple

---

