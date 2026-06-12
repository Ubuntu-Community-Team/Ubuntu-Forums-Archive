---
title: "backup /home"
date: 2010-12-30
forum: General Help
---

### Post by mkstallings1 on 2010-12-30
run 10.10 and have read a lot about moving /home to its own partition and how it is a good idea.  I was wondering, since I already backup /home to an external hard drive using grsync, would installing say 11.04 when it comes out and then restoring my /home from the external hard drive pretty much do the same thing?

---

### Post by mkstallings1 on 2011-01-10
anyone?

---

### Post by chmac on 2011-05-01
Not sure if this is still an issue for you or not, but yes, you could backup /home as a part of the / partition, then install 11.04 with a dedicated partition for /home and restore the files. Linux doesn't really care if /home is a folder on the / (root) partition or if it's a separate partition mounted as /home. Either way, the folder will be treated like a folder, and all should be well. :-)

---

### Post by quadproc on 2011-05-01
> **mkstallings1 said:**
> run 10.10 and have read a lot about moving /home to its own partition and how it is a good idea.  I was wondering, since I already backup /home to an external hard drive using grsync, would installing say 11.04 when it comes out and then restoring my /home from the external hard drive pretty much do the same thing?
If you move your /home to its own partition then you won't need to do any restoring of files - your same old /home can be used by many different Ubuntu releases.  I have 4 releases on this computer and they all use the same /home directory.

Of course, you still need to back up your /home partition for all the usual reasons.  The backup process will be simplified by having /home separated from the OS.

quadproc

---

### Post by mkstallings1 on 2011-05-02
Thanks

---

### Post by chmac on 2011-05-03
quadproc, as far as I'm aware, one can't "move" /home onto a new partition. The folder needs to be backed up somewhere (or renamed) and then the new partition mounted as /home and the data copied over. As far as I'm aware, if one mounts a partition onto a folder that already contains files, those files will not be copied onto the new partition.

mkstallings1, I'm not sure if I've fully understood your original question. If you feel like it's been answered, great. If not, please feel free to post back and I'll do my best to answer.

---

### Post by quadproc on 2011-05-03
> **chmac said:**
> quadproc, as far as I'm aware, one can't "move" /home onto a new partition. The folder needs to be backed up somewhere (or renamed) and then the new partition mounted as /home and the data copied over. As far as I'm aware, if one mounts a partition onto a folder that already contains files, those files will not be copied onto the new partition.

I think that we have a semantics issue here - by "move home" I meant to change the location of /home from whatever it used to be to a new partition; I was not referring to the data contained within that directory.  Of course, when you first do this your new partition will be empty and you need to use something such as rsync to get your user files from wherever they used to be and to install them into the new /home.  Having done that, you can dispose of the old /home.

Subsequently, for example when a new release comes out, you can just change its /home to something like old_home, fix up your fstab, reboot, and be running without doing any copying or restoring.  Then you can discard old_home.

There are several detailed sets of instructions on the web which explain how to move a /home.

quadproc

---

### Post by chmac on 2011-05-04
Agreed, we're both saying the same thing in slightly different language. :-)

Reading mkstallings1's original question again, I wonder if they are asking whether backing up and restoring /home is the same as putting it onto its own partition. Was that the original question? If it was, the answer is no.

Putting /home on its own partition changes a few other things. For example, it's sets a very hard limit on how big /home can be. It also means you could potentially boot two systems with the same /home partition. It's quite easy to use your existing partition as /home when installing a new version. I imagine if you were to dist-upgrade from 11.04 to 11.10 it would simply work.

---

