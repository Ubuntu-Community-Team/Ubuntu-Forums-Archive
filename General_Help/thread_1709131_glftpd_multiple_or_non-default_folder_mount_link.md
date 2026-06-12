---
title: "glftpd multiple or non-default folder? mount? link?"
date: 2011-03-17
forum: General Help
---

### Post by malwi on 2011-03-17
Hi!

I've had enough fighting my glftpd installation by myself, here's the thing.. I got an glftpd server running nicely and all, I've been using the default glftp/site/ directory as incoming/storage/file-folder. However the disk space on my OS-disk is running low and I was hoping to expand the storage with another disk.. 

I formatted a ext3 disk just as any other and mounted it to a /media/diskdirectory but now what?.. at first I was hoping to merge the disk so that newer files would be stored on the new hard drive while keeping the old ones in place but that seemed hard to achieve so I copied the entire /site/ folder to the new disk so that I could point glftpd to use that directory instead and here's my problem. Simply trying to edit the glftpd.conf or site command change homedir did not work, I have tried mounting, mount --bind, linking(?) all of which without great results.

The mount --bind thing worked though my uploaded files were written to both directories(both hard drives), the old glftpd/site/ and the new mount --bind:ed /media/disk/site directory...

Basically I want to use a hard drive that is not the OS drive as the default download/upload directory in glftpd how do I accomplish that?

Of course I tried searching the forums and the glftpd resources available and all I found was an old thread from 2006 that didn't get answered.

[http://ubuntuforums.org/showthread.php?t=202281&highlight=glftpd](http://ubuntuforums.org/showthread.php?t=202281&highlight=glftpd)

If anyone could guide me, it would be greatly appreciated!

/malwi

---

