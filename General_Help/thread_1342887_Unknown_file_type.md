---
title: "Unknown file type?"
date: 2009-12-01
forum: General Help
---

### Post by babelproofreader on 2009-12-01
I have today noticed that throughout my various directories I have numerous files that look like the attachment. Can anyone explain what they are, why they seem to have mysteriously appeared? Overnight I ran a virus check using ClamAV and may be this produced the files?

---

### Post by anaconda on 2009-12-01
the "~" at the end usually means that the file is a autosave backup file. 
Eg the gedit editor autosaves a bacup copy of files that you edit (before you save the file), and it appends the ~ to the end of the filename.

---

### Post by babelproofreader on 2009-12-01
Why have they only just appeared? I've been running Ubuntu for some time now and this is the first time this has happened. Is this some new feature of gedit? Furthermore, it would appear that this is undesirable behaviour. I now have randomly named backup files e.g a file named "3x" which contains nothing but 31,08,1962,12,13,15,52. This is not a file I have created and I certainly don't want my file system being bloated by such junk files. In addition, those files that appear to be genuine backups of files I have created in the past are not saved in the same directory/folder as the original copy of the file.

---

### Post by anaconda on 2009-12-01
Your files don't sound like autosave copies.. 

I checked, and gedit does not save ~ backupcopies, but some other editors like kate do.

But the backup copies are always in the same directory than the edited file or in the editors own backup folder in the home directory...

---

### Post by babelproofreader on 2009-12-01
Further research on this has led me to think that something called "application/x-trash" may have recovered (or recycled, hence the recycle symbol of the above attachment) all my deleted files going back over 18 months! Can anyone shed any light on this? What is application/x-trash and why has it done what I suspect?

---

### Post by t0p on 2009-12-01
> **babelproofreader said:**
> Further research on this has led me to think that something called "application/x-trash" may have recovered (or recycled, hence the recycle symbol of the above attachment) all my deleted files going back over 18 months! Can anyone shed any light on this? What is application/x-trash and why has it done what I suspect?

I've never heard of this behaviour.  But it sounds rather unlikely.

For all of your deleted files going back 18 months to reappear, those deleted files would have had to have been stored somewhere.  Are you saying that you haven't emptied your trashcan/deleted items folder in 18 months?

---

### Post by babelproofreader on 2009-12-01
I regularly empty my trash so that's not the reason. I *assume* that some of the files are recovered from somewhere simply because when I do a search of my file system some of the original files cannot be found i.e. the file "3x~" is found but not the presumed original "3x". I further *assume* it's recovered from a previously deleted file because the associated file type from the properties tab is "backup file (application/x-trash)"

---

### Post by davidpbrown on 2010-04-11
files~ are backups made where you've edited files directly. I see them usually only from text editors. It's not quite incremental autosave. No surprise then you have X.txt~

If you edit a system file it can be a useful backup, in case of a slip.. delete the latest and rename the backup~

If you want to, deleting all files~ will have no effect on your current system.

Blessed are the pessimists, for they have backups.

---

