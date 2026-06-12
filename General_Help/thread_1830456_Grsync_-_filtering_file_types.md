---
title: "Grsync - filtering file types"
date: 2011-08-21
forum: General Help
---

### Post by rockette morton on 2011-08-21
Hi there,

I've googled around for this for a couple of days and don't seem to be getting anywhere.

I'm using Grsync and what I want it to do is in essence very simple. I want to be able to plug in any drive into my laptop and run rsync on it to back up all the user documents on there to another external hdd and to exclude everything else. Working on the principle that user documents don't always appear where we'd expect I want rsync to look through the whole drive and filter what it backs up by file type. I am only having partial success, however.

I am using the 'filter' option in the 'additional options' box. I am using the command ```
--filter='merge /home/tim/Desktop/filter'
``` and I am attaching the filter file I have written. (I have added the .txt extention to upload it).

I have tested this script on my home folder and here's what's going wrong. Rsync will copy the entire directory structure regardless of whether there are any files to be copied over in those directories. I am also getting only some file types getting included and not others. .odt and .ods files are copied, for instance, but not .doc or .rtf.

I am scratching my head at this point. Any help is appreciated. I'm not attached to using Grsync so if you have a suggestion or something I can do from the command line, that would work for me too. Thank you so much,

Tim

---

### Post by papibe on 2011-08-28
The reason docs and rtfs are not being transfer is because there are trailing spaces at the ends of each rules:
```
...
+ *.doc
+ *.rtf
...
```
If you delete the spaces at the end of those lines, it will work. Note that there are several lines with trailing spaces. In order to make the those rules work you'll to remove all the ending spaces.

BTW, those rules are case insensitive, so it may be necessary to add uppercase rules for old MS Office files. For example
```
+ *.DOC
+ *.XLS
```

I hope this helps,
Regards.

---

### Post by papibe on 2011-08-28
> **rockette morton said:**
> Rsync will copy the entire directory structure regardless of whether there are any files to be copied over in those directories.Oops, I missed that one.

To avoid copying empty directories use the 'prune' option:
```
--prune-empty-dirs
```
It will surely work for a first time run. For later syncs, you would need a couple of extra 'delete' options:
```
--prune-empty-dirs --delete --delete-excluded
```
Regards.

---

### Post by rockette morton on 2011-08-29
gosh - thank you SO much. that is an enormous help to me. and of course i am in awe of your know-how. will do a trial run of this soon and mark as solved. thanks once again!

tim

---

