---
title: "Extract tarball into directory without overwriting .svn files (merge)"
date: 2011-09-21
forum: General Help
---

### Post by nicholas.alipaz on 2011-09-21
I have a tarball with identical structure to an existing directory.  Here is the existing directory:
/directory
/directory/file.txt
/directory/file2.txt
/directory/.svn
/file3.txt
/file4.txt
/.svn

Here is the tarball:
/directory
/directory/file.txt
/directory/file2.txt
/file3.txt
/file4.txt

I want to extract the tarball on top of the directory without overwriting the .svn files.  Is there a good graphical interface to doing this?  Perhaps an extension to the "Archive Manager" (file-roller)?

TIA

---

### Post by searchfgold6789 on 2011-09-21
Ark does it but it's KDE.

---

### Post by nicholas.alipaz on 2011-09-21
> **searchfgold6789 said:**
> Ark does it but it's KDE.

hmmm, I guess I could install Ark with KDE but that seems overkill to do that.  Anyone else know of anything?

---

### Post by Slim Odds on 2011-09-21
The second tar file does not have .svn files, so just untar it in the same location.

---

### Post by nicholas.alipaz on 2011-09-21
> **Slim Odds said:**
> The second tar file does not have .svn files, so just untar it in the same location.

There is only one tar file.

The first is a directory to which I would like to extract the tar file on top of without removing the .svn files.  file-roller seems to "recreate" each directory before replacing files, this causes all .svn directories to be deleted.

I need to "merge" the extract with the directory on my computer, not wipe and replace like file-roller seems to do.

---

### Post by nicholas.alipaz on 2011-09-21
OK, I found a solution, not really optimal but it works.

I used the Linux 7zip utility with Q7z frontend and it works.  But I find this a bit clunky even though it does work.

I am still open to alternate solutions if people know them.

Best

---

### Post by jvance492 on 2011-09-21
Sorry if this is not what your looking for as you are looking for graphical solutions. but as a side note:

If you area extracting from command line. I know there is an exclude for directories:

tar cvpzf backup.tgz --exclude=/proc

This would extract the tgz file but it would exclude any directory named proc 

Maybe you can do something similar with .svn extensions?

---

### Post by Slim Odds on 2011-09-21
> **nicholas.alipaz said:**
> There is only one tar file.

The first is a directory to which I would like to extract the tar file on top of without removing the .svn files.  file-roller seems to "recreate" each directory before replacing files, this causes all .svn directories to be deleted.

I need to "merge" the extract with the directory on my computer, not wipe and replace like file-roller seems to do.

Sorry, but your example does not show a tar file with .svn files in it.

---

### Post by patryk77 on 2011-09-21
> **Slim Odds said:**
> Sorry, but your example does not show a tar file with .svn files in it.

/directory/ contains /directory/.svn/

Extracting the /directory/ from the tarball overwrites the /directory/ on the drive, deleting .svn/ in the process.

---

### Post by nicholas.alipaz on 2011-09-22
> **patryk77 said:**
> /directory/ contains /directory/.svn/

Extracting the /directory/ from the tarball overwrites the /directory/ on the drive, deleting .svn/ in the process.

patryk77 is right.  My example is meant to show a tarball containing only files and directories and then a directory on my hard-drive that has identical structure but has additional .svn directories.

The issue to resolve here is extracting the tarball on top of the directory without wiping out the .svn directories.

Thanks for all the comments.  I am familiar with the tar command and it's options, but wanted a gui for it due to my pure laziness in some scenarios.  I will continue using Q7z for now, but hope to find a better gui as it is a little clunky.

---

