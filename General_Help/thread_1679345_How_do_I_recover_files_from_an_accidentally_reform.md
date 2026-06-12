---
title: "How do I recover files from an accidentally reformatted drive?"
date: 2011-01-31
forum: General Help
---

### Post by jhsu802701 on 2011-01-31
ABOUT ME: I'm looking for a position as a computer forensics/recovery specialist in the Minneapolis/St. Paul area. I've been providing free computer recovery services in exchange for a testimonial and recommendation. 
[BR]
THE SITUATION: I have a client with a 500 GB hard drive that originally had an NTFS partition for about the first 370 GB and a Linux partition for the rest. He tried to install Ubuntu on the Linux partition. But for some reason, the installer reformatted the entire drive as ext4. He then reformatted the first 370 GB or so as NTFS to get the original formatting back so he could recover the Windows files from the original partition. However, the original Windows files did not appear, and Iolo Search and Recover couldn't find the files either.  What do you suggest for recovering the files? PhotoRec will take 100 hours and does NOT recover filenames or the directory structure. I'll end up with numerous files with random names, and many of these files will be system files rather than personal files.  What alternatives to PhotoRec do you suggest? I need something that's both faster AND that saves filenames and the directory structure.

---

### Post by Ocxic on 2011-01-31
You could try "testdisk" it will search for partitions and recover them for you, it's available in the repos.

As for formatting, if you installed any data onto the drive it would have overwritten the existing data, just "re-formatting" a drive with the same partition info will not recover the contents as it will create a new "data table"(not the correct term I know) that will not have any pointers to any files.

---

### Post by psusi on 2011-01-31
Wow, given that intro you really should already know the answer to this.  Given that it has been formatted not once, but twice, it's time to restore from backup.

---

### Post by jhsu802701 on 2011-01-31
> **psusi said:**
> Wow, given that intro you really should already know the answer to this.  Given that it has been formatted not once, but twice, it's time to restore from backup.

Recovering files from Windows rot is easy - just boot up a Linux live CD and copy the files to an external hard drive.

I've recovered files from bad hard drives simply by connecting the hard drive to my IDE/SATA-to-USB adapter and using Puppy Linux to copy the files from the bad drive to a working external hard drive.  It's a slow process, but it works very well.

The situation I described here is much more challenging.  Are you sure that there is no way to recover anything?  Just how much does the reformatting process overwrite?

I'm learning so much by doing data recovery work that I couldn't really learn merely by reading books or studying theory.

---

### Post by psusi on 2011-02-01
Reading files with another system from a disk with a messed up windows install is a far cry from forensics or recovery.  The format wipes out everything needed to identify file names and directories, which is why photorec can not recover that.

---

### Post by jhsu802701 on 2011-02-01
> **psusi said:**
> Reading files with another system from a disk with a messed up windows install is a far cry from forensics or recovery.  The format wipes out everything needed to identify file names and directories, which is why photorec can not recover that.

Are you saying that PhotoRec is the only thing that will work?  If so, is there a way to speed it up so that it doesn't take 100 hours to go through the entire drive?

---

### Post by psusi on 2011-02-01
> **jhsu802701 said:**
> Are you saying that PhotoRec is the only thing that will work?  If so, is there a way to speed it up so that it doesn't take 100 hours to go through the entire drive?

It is the last resort and the only one open to you at this point if you don't have backups.  I doubt there is a way to speed it up, but I have never used it.  It is much more reliable and less time consuming to keep good backups.

---

