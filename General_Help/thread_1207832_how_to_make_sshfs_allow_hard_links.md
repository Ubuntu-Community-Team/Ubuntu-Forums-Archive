---
title: "how to make sshfs allow hard links?"
date: 2009-07-08
forum: General Help
---

### Post by quixote on 2009-07-08
I'm trying to set up automated incremental backups to a headless server running Debian.  The backups use hard links, pretty much following [Mike Rubel's script]("http://www.mikerubel.org/computers/rsync_snapshots/").  I'm using sshfs to mount the target directory to my local partition:```
$ sshfs quixote@ourmole:teaching_backups /mnt/ourmole_local/teaching_backups -o uid=1000 -o nonempty
```and then the idea is that rsync can do its magic: ```
rsync -avu --delete-delay --link-dest=$RTARGET/daily.2 $SOURCES/ $RTARGET/daily.1
```
The copying part works fine, but the --link-dest gives an error message that the link could not be made, "function not implemented (38 )."  If I try to make a hard link manually, I get "hard link not allowed for directory."

So I'm guessing I need to set an option in sshfs or fuse to allow this, but I don't see anything in the man pages that says "if you want to allow hardlinks, use -o allow-hardlinks"  or something! :p  The options I am using above are an attempt to get sshfs / fuse to stop messing me about.

I realize I'm pretty deep in the weeds here, but I'm hoping somebody can help!

---

### Post by capscrew on 2009-07-08
Hard links don't cross partitions or filesystems.  See [_here_]("http://www.linfo.org/hard_link.html").

---

### Post by quixote on 2009-07-08
Hard links don't cross partitions?  Oh noes!  

But then I don't get how all the hardlink-based incremental backup scripts work.  The scripts (like Rubel's for instance) are explicitly there to back up to some other machine, like a server.  And the script works when I back up using hard links to another 500GB hard drive I have in the house.  But the 500GB one is not secure.  It uses nfs, and I mount one its directories locally and then rsync to that, rather than using sshfs.  

The 1TB "ourmole" that I'm having all the trouble with, is secure.  I log into it with ssh, or mount a dir with sshfs.  And then I can't do hardlinks.

So it seemed to me that the issue had to be sshfs rather than the hard links themselves.  Why can it cross partitions in an unsecure environment, but not in a secure one?  :confused:  

Or is it reiserfs that's letting me do what I want?  But, again, if that's the case, how are all the incremental backup scripts supposed to work??

filesystems:
local machine: ext3 (Jaunty)
500GB unsecure: reiserfs (HP Mediavault, OS is some kind of tiny linux)
1TB: ext3 (Debian, Lenny (I think!))

---

### Post by capscrew on 2009-07-08
> **quixote said:**
> ...the script works when I back up using hard links to another 500GB hard drive I have in the house.  But the 500GB one is not secure.  It uses nfs, and I mount one its directories locally and then rsync to that, rather than using sshfs.

I am by no means an expert here, but I believe that you have sorta answered you our question.  You can't use a virtual filesystem (sshfs) as that is crossing filesystems.  The NFS mount is considered local to the host filesystem.  

In this case "local" does not have to mean "directly attached".> 


The 1TB "ourmole" that I'm having all the trouble with, is secure.  I log into it with ssh, or mount a dir with sshfs.  And then I can't do hardlinks. This is no a local mount.> 

So it seemed to me that the issue had to be sshfs rather than the hard links themselves. Indeed, the problem is not security, but the use of a virtual FS. > 
 Why can it cross partitions in an unsecure environment, but not in a secure one?  :confused: Your not crossing partitions when mounted as NFS.  The mountpoint is local. > 

Or is it reiserfs that's letting me do what I want?  But, again, if that's the case, how are all the incremental backup scripts supposed to work??

I believe that you rsync script uses the hardlinks to create the snapshots only.  This data can't be spread across un-linkable partitions/filesystems.  Once again the use of the sshfs (virtual filesystem) is what is stopping you.> 

filesystems:
local machine: ext3 (Jaunty)
500GB unsecure: reiserfs (HP Mediavault, OS is some kind of tiny linux)
1TB: ext3 (Debian, Lenny (I think!))

---

### Post by quixote on 2009-07-08
So using nfs is the crucial element.  That's answered my question.  Thank you!  Now all I have to do is work out how to use the 1TB drive via nfs.  

Thanks again!

---

