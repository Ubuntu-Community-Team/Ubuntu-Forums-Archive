---
title: "resizing the size of RAM fs on an Ubuntu LiveCD"
date: 2009-12-19
forum: General Help
---

### Post by yawnmoth on 2009-12-19
Say you've inserted an Ubuntu LiveCD into a computer with 3 GB of RAM and the LiveCD reserves maybe 500MB or so for it's own purposes.  Would it be possible to resize this to 1GB or 2GB without restarting?

---

### Post by yawnmoth on 2009-12-19
Related to this, how do I delete stuff?  I downloaded a large file with Firefox and tried to download another only to get a "you don't have sufficient free space" error.  I deleted what I downloaded but I'm still getting the error.

In Windows, you'd have to empty the Recycle Bin as well.  In Ubuntu...  i have no clue.  Any ideas?

Also, it'd be nice to see the full capacity of the RAM filesystem - not just the available free space (which is all that the File Browser tells you and even that's not dependable since right now the File Browser isn't telling me anything).

---

### Post by dcstar on 2009-12-19
> **yawnmoth said:**
> Related to this, how do I delete stuff?  I downloaded a large file with Firefox and tried to download another only to get a "you don't have sufficient free space" error.  I deleted what I downloaded but I'm still getting the error.

In Windows, you'd have to empty the Recycle Bin as well.  In Ubuntu...  i have no clue.  Any ideas?

Also, it'd be nice to see the full capacity of the RAM filesystem - not just the available free space (which is all that the File Browser tells you and even that's not dependable since right now the File Browser isn't telling me anything).

The Live CD is for trying Ubuntu without affecting an existing system, nothing more and nothing less. It is not configured for normal operations.

If you want something like that, create a USB Startup Disk with Persistence.

---

### Post by yawnmoth on 2009-12-20
> **dcstar said:**
> The Live CD is for trying Ubuntu without affecting an existing system, nothing more and nothing less. It is not configured for normal operations.

If you want something like that, create a USB Startup Disk with Persistence.

For some reason, I can't help but think this is a cop out answer, so let's pretend I want to do it without a LiveCD.  How do you do that?

If deleting a file on an Ubuntu LiveCD doesn't really delete it how do I know deleting it on a regular Ubuntu installation even works?

---

### Post by StuartN on 2009-12-20
> **yawnmoth said:**
> If deleting a file on an Ubuntu LiveCD doesn't really delete it how do I know deleting it on a regular Ubuntu installation even works?

On a full install there is a trash bin in the bottom-right panel, which can be emptied from the right-click menu or opened with a left click. Items deleted from trash should be gone. Apllications->Accessories->Disk usage analyzer gives a comprehensive view of disk use, **df** or **du -sk** at the command line show summaries.

I do not know if it is possible to resize a filesystem that is in use, although it must be possible to create an additional ram file system if there is sufficient memory or swap.

You can always read and write to a physical hard disk, or to a USB flash disk, or an external storage drive, although you may need to mount it first. USB devices should automount.

---

