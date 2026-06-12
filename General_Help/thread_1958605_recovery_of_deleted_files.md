---
title: "recovery of deleted files"
date: 2012-04-14
forum: General Help
---

### Post by wolf187 on 2012-04-14
Hello

I desperately need some help, over 40gb of files has been erased from my computer, I am currently running Ubuntu 12.04, is there a way of recovering these files, these files are very hard to get back and I regret not making a backup of all these files, can anyone help me asap, I tried extundelete and also recover and scalpel but they do not seem to find the deleted files,thanks in advance.

---

### Post by Rodney9 on 2012-04-14
Do Not Use The Drive, that over writes your data.

SpinRite is the only recover software I've heard of, that actually works.
It will not give up, it's record is one year. 
It does cost though, depends how important the data is ?

[https://www.grc.com/sr/spinrite.htm](https://www.grc.com/sr/spinrite.htm)

Rodney

---

### Post by mörgæs on 2012-04-14
Photorec is another option.

---

### Post by dragonfly41 on 2012-04-14
You don't explain the format of the devices erased.

ext3, ext4, ntfs ?

Here is yet another data recovery utility.

[http://download.cnet.com/Stellar-Phoenix-Linux-Data-Recovery/3000-2248_4-10204904.html](http://download.cnet.com/Stellar-Phoenix-Linux-Data-Recovery/3000-2248_4-10204904.html)

As explained above don't install recovery utilities into the drive you're trying to recover.
Safer to have another USB drive to clone into.


Some other approaches which might help ..

[http://www2.opensourceforensics.org/tools/unix](http://www2.opensourceforensics.org/tools/unix)

[http://forensiccop.blogspot.com/2009/09/experiment-14-on-deleted-files-recovery.html](http://forensiccop.blogspot.com/2009/09/experiment-14-on-deleted-files-recovery.html)

[http://accessdata.com/products/computer-forensics/ftk](http://accessdata.com/products/computer-forensics/ftk)

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

install foremost from Synaptics Package Manager
install scalpel from Synaptics Package Manager
the target partition containing the deleted data to be recovered should not be mounted

[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

---

### Post by wolf187 on 2012-04-15
I tried Photorec, the files are music files the file formats are .mp3, .avi, .dat, .flv, .mpg, .wma, .wmv, Photorec gives too many results of files I do not need, ther are over 5000 songs that have been deleted and 300 music videos, I'm not so worried about the music videos, scalpel would work if it was possible to put mp3s into the configuration file. It is an ext4 file system that I am trying to recover from, it was all deleted from one main folder and there were various subfolders within the folder, is it possible to recover from just that folder instead of searching the whole partition and giving me back useless junk? Oh and the files deleted were only deleted yesterday. Thanks

---

### Post by dragonfly41 on 2012-04-15
Stellar Phoenix Linux (see link above) should help you recover ext4 (runs on Windows)

Read also here [http://ubuntuforums.org/showthread.php?t=1958153](http://ubuntuforums.org/showthread.php?t=1958153)

---

### Post by wolf187 on 2012-04-15
The problem is that I have now Windows system to use and I can only use this hard drive, is there no other way to recover the data using the hard drive currently mounted. Thanks.

---

### Post by dragonfly41 on 2012-04-15
This explains the Live CD data recovery options .. although you may have already tried some of these

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

[p.s.]

that tutorial above warns you ..

> [COLOR=Red]*Note: Do not recover files to the hard drive you&#8217;re recovering from.*[/COLOR]Same warning from Rodey9 above

> [COLOR=Red]Do Not Use The Drive, that over writes your data[/COLOR]So you may have to invest in a external USB drive .. which will be useful/essential for backup.

However if you have 40 GB of data to recover you could gamble that by installing Stellar Phoenix on Windows (or RecoverMyFiles) you won't lose _too_ much data (you might lose some .. but not 40 GB).

You will still need an external drive to save the recovered data into.

---

### Post by robi6 on 2012-04-15
Recommendation: [ext4magic]("http://developer.berlios.de/projects/ext4magic/")

on ubuntu you must compile it.
[Docu :]("http://openfacts2.berlios.de/wikien/index.php/BerliosProject:Ext4magic")  see also:  Scenarios-Site: Howto 1..3
use: the histogram function to determine the begin of the deletion process and use it as "AFTER" time

and recover
```
ext4magic DEVICE -m -a 127??????? -d /FREE/SPACE/FOR/RECOVER
```Of course, you need external drive space to save the recovered data.
If extundelte can't find these files, no old inode copies of these files available,
so you have to look through the whole file system to find the data blocks,
and so you will find a lot files that you do not need.

ext4magic looking and recover based on the journal data which were written during the deletion.

It's a multistage recover process
* First recover step: similar "extundete --recover-all"
* Second recover step: is not included in any other program
* Third step: works like Photorec but more accurately matched to ext4

For a good result, the journal data of the filesystem should not be overwritten after deletion.
Therefor a good idea immediately after the deletion, umount or
[LEFT] or create a copy of the file system or save the journal data.[/LEFT]

---

### Post by dragonfly41 on 2012-04-15
I forgot this one .. extundelete .. might be the same as above ..

[http://samiux.blogspot.co.uk/2011/04/howto-undelete-files-and-directories-on.html](http://samiux.blogspot.co.uk/2011/04/howto-undelete-files-and-directories-on.html)

---

### Post by oldfred on 2012-04-15
With photorec you can tell it to only recover certain files extensions like only mp3s. But you still have to copy files to another drive and not mount drive you are using. 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

With mp3 and some others you can use internal data to rename files also.
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by Church on 2012-09-17
I'll note to ext4magic that i had success only when referencing single file name to restore. It segfaulted if whole dir file was in referenced to restore (extundelete didn't restore anything when referenced file or dir, and segfaulted when referencing whole fs to restore). Luckily i knew file name and that one file restored was all i needed so i stopped at that.

---

