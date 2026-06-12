---
title: "use tar backup method to change file-system?"
date: 2006-05-16
forum: General Help
---

### Post by pellgarlic on 2006-05-16
i think this backup method, using the "tar" command: 

[http://ubuntuforums.org/showthread.php?t=35087&](http://ubuntuforums.org/showthread.php?t=35087&) 

is a really cool technique - shows the sheer flexibility and powerful simplicity of linux (as opposed to some other, unmentionable OSes). 

i have not used it to restore anything yet, though i have used it to backup. (when i was installing a new motherboard recently - expected to have to reinstall or reconfigure or something, but ubuntu just kept on rolling like nothing had changed at all, so i didn't need to restore anything! the mobo change killed my xp installation tho, and it remains dead, cos i refuse to resuscitate it ..... *again*!)

i have a question about this method tho - i have been reading about the different file-systems available in linux, and have decided that i would rather have used "XFS" than "ext3" (which was the default, so i left it at that). 

using a restore method like acronis, or ghost or whatever, would replace the whole partition, hence overwriting the file-system, but this method would not, right? it would simply copy the files into the new file-system. however, are there any issues with doing this? 

what i am purporting to do, is reinstall ubuntu, but using the "XFS" file-system, then restore my previous "ext3" installation using the "tar-backup" method. would there be any implications involving the change of file-system? does ubuntu make configuration choices during installation and setup, *or *write settings in any system files, which would relate to, and perhaps rely upon the file-system in use? 

i'm reluctant to go down the "try-it-and-see" path with this, as i have just got my setup the way i want it, after a couple of weeks quite intensive effort (mainly made worse by having major problems also trying to sort my girlfriend's ailing windows xp machine) and i want to just have a working setup, rather than still be experimenting. (for a little while at least ;) )

---

### Post by evilgold on 2006-05-16
A tar is just basically just a containing file, like zip without the compression. So yes if you changed file systems, restoring a tar backup wouldnt affect the filesystem at all.

---

### Post by pellgarlic on 2006-05-17
[QUOTE=evilgold]A tar is just basically just a containing file, like zip without the compression. So yes if you changed file systems, restoring a tar backup wouldnt affect the filesystem at all.[/QUOTE]

yeah, i understand that restoring a tar backup wouldn't change the file system that is already in place, but what i wasn't sure about was if the installation would still work properly.

for example, during the installation or setup of ubuntu, does anything happen along the lines of this:

"if 'ext3' file system found, do 'a' to 'x' file,
 else if 'XFS' file system found, do 'b' to 'x' file"

or does linux not care which file system is used? 

i'm finding it hard to explain myself, as my concern is really theoretical, and not based on an actual problem - i'd just like to avoid an actual problem if possible.

---

### Post by DougC on 2006-05-17
As far as Ubuntu concerned the files should still perfectly fine when you restore them. As long as the filesystem is supported in the kernel (and XFS is) then all is ok.

Hope that clears things up for you.

---

### Post by pellgarlic on 2006-05-17
spot on, DougC - that's what i wanted to know. just wish i could have put it as concisely as you just did! 

cheers.

---

### Post by DougC on 2006-05-17
No probs. On my current suse system I have Reiser for / and XFS for /home. I can move files between them without issue.

---

### Post by pellgarlic on 2006-05-17
[QUOTE=DougC]No probs. On my current suse system I have Reiser for / and XFS for /home. I can move files between them without issue.[/QUOTE]

:eek: interesting... didn't consider that possibility (i.e. using two different file systems like that). i guess that would mean good performance for working with small files for / and good performance for working with large files for /home?

or did you have other reasons for choosing those particular file systems? i was just gonna go with XFS cos it seemed about equivalent in overall terms with Resier, but better at working with large files, and as i do a lot of home-audio-recording (big wav files!) and working with <ahem!> "video", it seemed the best choice. i like the idea of your setup tho - can i steal it? :D

---

### Post by DougC on 2006-05-17
Lol yeah ok.

I've got / as reiser, /home as XFS and a /data also as as XFS.

I don't have Ubuntu installed as yet on this machine though I've got another reiser and another XFS partition waiting.

Oh and while I remember, I'm sure I read recently that Ubuntu has a problem with XFS on the partition containing /boot (or rather Ubuntu's grub has the problem) so you may want to search the forum just to check.

The /data is just a seperate area out of the home filesystem I use for downloads etc.

I just wanted to try XFS really, I didn't really have a strategy for it. I read some web site recently comparing them all, according to them XFS seemed to come out on top for most things; sio I thought I'd give it a go. 

Seems ok to me :)

---

### Post by garretwp on 2006-05-21
Tar is a great way to back up! I use it in my perl script to backup my home partition. As for issues between file systems, you will not have any when restoring your files. They are tech. just copied over onto the new filesystem and you should be on your way. Also yes it has been reported that grub as issues with having the boot partition as anything other then ext2 and ext3. So if you were to redo your system, I would suggest you have your boot partition formated as ext2 or ext3 and the rest of your partitions and drives any filesystem you would like that is supported by the kernel. Not sure if I am correct on this or not, but I do think you have to modify grub file to locate the new partitions that yo u have made. Again I am not postitive on this as I do not know grub all that well.

Garrett

---

### Post by pellgarlic on 2006-05-22
[QUOTE=garretwp]it has been reported that grub as issues with having the boot partition as anything other then ext2 and ext3. So if you were to redo your system, I would suggest you have your boot partition formated as ext2 or ext3 and the rest of your partitions and drives any filesystem you would like that is supported by the kernel.[/QUOTE]

actually, i was going to go for reiser for / and jfs for /home. can't actually find anything relating to grub having problems with reiser in particular - only that it can't read jfs or xfs, (and people usually recommend ext3 for regular computer usage anyway, because of its reliability). have you had any experience with reiser? 

as i do a lot of multi-track audio editing, i want to squeeze as much performance out of my pc as possible, including careful selection of the file system i use, which is why i'm looking at alternatives to ext3. 

i like the sound of jfs best for my home partition, where a lot of large audio files reside, and reiser seems best for / due to its "faster" performance than ext3. 

(i realise a lot of the tests i am basing my opinions on are maybe not exactly analogous to "real-world" scenarios, but they are my best indication).

---

