---
title: "Viewing deleted files on nfs (or cifs) mount?"
date: 2009-11-11
forum: General Help
---

### Post by Beachside on 2009-11-11
Hello Fine Folk.  Just joined, but been leveraging this great forum to build/get a clue for a while.

I have a nas box using an EXT3 (I believe, 2 if not) file system.  I deleted (moved) a folder from it to an XP MCE box.  MCE ate the folder and contents.  I recovered roughly half using NTFS recovery tools and I can't even see the names of the remaining files.

I haven't put any new data on the nas.  Following the DataRecovery thread, I've tried/failed to recover (or just see) the files with Foremost and Autopsy via an nfs mount.  Is there a way I can simply view the deleted file names so I know what's gone?  I can mount the nas via nfs and cifs on my Ubuntu box.

Working on removing M$ from the house,
 Beachside

---

### Post by Beachside on 2009-11-11
I can't seem to save my edit so here it is.  Note: I moved some of a folder rather than all.

----
EDIT: It is EXT3, and never mind I found my answer.  Using debugfs I could ls -d (list deleted files, which I assume only works while in debugfs because ls -d in the terminal is list directory) in a test directory.

I hope sharing other sites is, at most, a wrist slap offense in this fine forum.  Google "Data Recovery on Linux and ext3" for detailed instructions.  My 1st hit had a 5 star Web of Trust rating.  It goes on to walk through data carving your results. 

WARNING: I'm an amateur, with system experience elsewhere.  So use caution with my advice.  

Now to get root to my nas or drop the drive in a usb shell, and figure out how to mark this thread closed. :)

---

