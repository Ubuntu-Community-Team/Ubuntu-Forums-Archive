---
title: "Backing up to DVDs"
date: 2009-07-05
forum: General Help
---

### Post by Brian Vaughan on 2009-07-05
I'm about to install a DVD burner, and part of the reason I bought it was to use it for backups. I'm looking for tips on how to effectively backup my files.

I skimmed the chapter on backing up and restoring data from *Essential System Administration*, and after looking at the readily available backup software in the repositories, I think my best bet may be to use the GNU "tar" command, possibly in a simple shell script. Spanning media is supposed to be an option, but I'm not sure if it will handle writable DVDs.

I've got /home on a separate partition, if that is relevant. I don't think there's much point to backing up any files not on /home. /home has a bit less than 80 gigabytes of files, and if I exclude some folders (Neverwinter Nights, the .wine folders [rms, forgive me my sins]) there are about 50 gigabytes of files to back up.

It'd be nice if I could use the backup disks to facilitate copying music files to some of the MacBooks in the household.

Does anyone have any advice?

---

### Post by sdowney717 on 2009-07-05
IMO, best backup is another temporary drive

It is not worth backing up any system or application files as these can be easily redone.
that only leaves data like music, and personal files. So, why not just create data DVD's using DVD writer like k3b or Brasero or Nero Linux.

---

### Post by sdowney717 on 2009-07-05
you can backup entire /home and on a reinstall attach the user.
but I wonder how well this works on an install from one version to another.

---

### Post by Brian Vaughan on 2009-07-06
I'll try to simplify my questions:

Will tar span DVDs? Is there anything special I need to do to make sure it does?

---

### Post by spibou on 2009-07-06
What do you mean span DVDs?

---

### Post by Brian Vaughan on 2009-07-06
I'm trying to back up between 50 and 70 gigabytes, which is more than the capacity of a single DVD. I know some archiving software can create archives that are larger than a single physical volume of media; typically, they would prompt the user to insert another volume when the current one is full. I've done that in the past with floppies and tapes on Windows. I'm just not sure whether it will work properly with writable DVDs and a standard DVD burner.

---

