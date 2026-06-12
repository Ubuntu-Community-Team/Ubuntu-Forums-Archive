---
title: "Deleting Wine symlinks?"
date: 2011-04-12
forum: General Help
---

### Post by SixStringSW on 2011-04-12
I did a "backup" of my .wine folder by copying it to my network attached storage drive. Now, that folder thinks it has about 200gb of data! Specifically, it's the .wine/dosdevices folder. I didn't grasp that Wine had created some kind of hard links to my ~ folder on my Ubuntu box. 

Since that folder is clearly recursively linking to all my files, I'm afraid to just delete it. I did delete one file within it as a test and, sure enough, the original file back on my Ubuntu box disappeared!

So . . . how can I delete the .wine "backup" folder I created on my NAS _without_ deleting all the original files?

Thanks!

---

### Post by SixStringSW on 2011-04-12
Okay, further examination shows that the dosdevices folder on my NAS contains symlinks, including the culprit:  z: -> /

Can I safely delete the z: symlink without deleting / (i.e., everything)? I'm guessing I can, and that even if not permissions would prevent me from actually deleting the files, but I'd really like some confirmation from someone whose Linux kung fu outclasses mine.

Thanks.

---

### Post by earthmeLon on 2011-04-12
Whenever you install a program in wine, it installs it to that wineprefix.  The wineprefix has a directory (.wine by default) which contains drive_c and dosdevices.  dosdevices is a list of symlinks for wine to use for windows drive notation (A:, B:, C:...), while drive_c contains all of the information (DATA).  The c: in dosdevices is a SOFT link to drive_c.  Because it's SOFT, it means that it only *points* to the location, it does not *mirror* it.

I am not 100% clear on what you've done, but if you did something similar to this:
```
cp ~/.wine ~/.winebackup
```
Why not try
```
cp ~/.winebackup ~/.wine
```
Do some testing, and then if everything is how it needs to be, remove .winebackup.


Since you're dealing with so much data, you could:
```
mv ~/.winebackup ~/.wine
```
but, if .winebackup doesn't work, then you have nothing to compare.


Please read through this carefully and understand that I'm not 100% sure of the actual situation you're in or what you're trying to accomplish :P   What's your ultimate goal?

---

### Post by SixStringSW on 2011-04-13
I made the original backup using the copy command (something like "cp .wine /home/xxx/shares/nas") so now there is a "duplicate" of my entire file system on my NAS, since there is a symlink under .wine that points to my root). I don't need the backup anymore and wish to delete it (not restore it). In the .wine/dosdevices folder on my backup (my NAS) there is a single symlink,  z: -> /

Can I delete that symlink safely? I presume that will, in effect, delete the backup. (Right now, that folder clams to have over 200GB of data in it, but it's all links to my original data on my Ubuntu box and to the NAS files. I'm surprised there isn't some horrific recursion thing going on.) 

It appears that if I delete any files _under_ the z: directory, which I suspect are hard links, it deletes both that link and the original file. I don't want that!

So is it okay to delete the z: symlink on my NAS? Or, if I delete it, is it going to try to delete all my files (/)?

I'm pretty sure I can; I just want to be 100.0000% safe here.

---

### Post by SixStringSW on 2011-05-22
Since no one could be bothered to answer this, I thought I'd go ahead and post the answer (which I eventually found myself) for anyone else who's wondering.

It's actually quite simple: just "unlink" the symbolic link:

$unlink z:

and the link to the / directory is gone. The folder containing the symlink can now be removed.

---

### Post by earthmeLon on 2011-05-22
Very glad that you have gotten it working the way you need :D

In the future, you can 'rm -rf' the link as well.

[QUOTE=SixStringSW]Can I safely delete the z: symlink without deleting / (i.e., everything)?[/QUOTE]

*THIS* wording was tricky.



Please mark your post as solve under the Thread Tools menu.

---

