---
title: "Swap partition access"
date: 2011-05-21
forum: General Help
---

### Post by milos27 on 2011-05-21
Hi I've recently just installed ubuntu 11.04 but seem to have made a big mistake. During the install process I was asked to specify a location to be used for swap. Not really understanding what this meant I chose another partition on my drive with some free space but also a lot of my data. Needless to say I now cant see that partition. 

Is there anyway for me to access it? or to at least recover the information I need from there? its about a 200gig partition, and it used to be ntfs. 

Please let me know if there is anything I can do.

Regards

Milos

---

### Post by oldfred on 2011-05-21
Welcome to the forums.

I hope you have backups.

Even liveCD will mount swap and use it overwriting more of your data. Since it has been reformated the files with names will not be recoverable, but some of the data that has not been overwritten will still be there. Photorec and others that scan partition and look for something that looks like a file will recover that file but not the file name. You need to have another drive with lots of room to copy data to. It then is a long process to figure out which files are which. I used photorec and it works, but it found a text file I wanted many times as I had saved it many times. It found all the old versions & I was not sure I ever found the last saved version. 

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

See post #22 for results from several recovery tools.
[http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)
[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

---

### Post by srs5694 on 2011-05-21
Sadly, oldfred is correct. I'll add that if you're running Linux now, you should *immediately* disable use of your swap space. You can do this by opening a Terminal window and typing the following:

```

sudo swapoff -a

```

Disabling use of swap will prevent any further damage from ongoing use of swap space. Do not reboot the computer until you've recovered your files; or if you do, you should reboot into a recovery tool that doesn't use swap, such as [PartedMagic.](http://partedmagic.com/) Alternatively, you could temporarily disable swap use in your /etc/fstab file by locating the line that references swap and commenting it out by placing a hash mark (#) at the start of the line.

There's a slim chance that you could use Windows' CHKDSK utility to recover at least some of your data. To do this, you'd need to use fdisk to change the type code of your swap partition back to 07, then boot Windows and run CHKDSK on it. It's quite possible that Windows won't be able to do anything with it, though. Worse, it's possible that in attempting to fix the problem, CHKDSK will do more damage. Thus, I recommend you do a low-level backup of the partition to another disk or a big enough file on another partition before you attempt this.

---

