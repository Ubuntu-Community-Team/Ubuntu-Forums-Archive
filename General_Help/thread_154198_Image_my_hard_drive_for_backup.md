---
title: "Image my hard drive for backup???"
date: 2006-04-02
forum: General Help
---

### Post by dmorlow on 2006-04-02
Hi, I have Ubuntu loaded on my laptop and it is working pretty much perfect now.  I would like to create an image of the install so when I mess it up (I know I will), I could just restore the image to the way it was working perfect.  Are there any programs for Linux that does that?

Thank You,

David

---

### Post by Ramses de Norre on 2006-04-02
tar?

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=dmorlow]Hi, I have Ubuntu loaded on my laptop and it is working pretty much perfect now.  I would like to create an image of the install so when I mess it up (I know I will), I could just restore the image to the way it was working perfect.  Are there any programs for Linux that does that?

Thank You,

David[/QUOTE]
There is a program that can back-up/restore all your important ubuntu stuff. Automatix has the option to install it and I think that there is also a tutorial under the How To's. I don't think that any back-up program can make an image though.

---

### Post by mlalkaka on 2006-04-02
[QUOTE=dmorlow]
I would like to create an image of the install so when I mess it up (I know I will), I could just restore the image to the way it was working perfect.  Are there any programs for Linux that does that?
[/QUOTE]
Yes there is such a program for Linux! Yay! The program is called Partition Image (Partimage), and it is free, in both forms of the word. Here is the URL: [http://www.partimage.org](http://www.partimage.org). I haven't used it, but it looks promising. (Tell me how well it works, if you don't mind.)

[QUOTE=MasterChief1234]
I don't think that any back-up program can make an image though.
[/QUOTE]
Please see above. :D

---

### Post by cmatheson on 2006-04-02
Hi.  In this case 'dd' is your friend.  Read the man-page for more information... but basically it will be as simple as 'dd if=/dev/hda1 of=/media/other/hard_drive.img' (where /dev/hda1 is the partition you want to back up.  you can't make the backup to the same partition, so you'll have to do it on another drive/partition/network-mount/etc.

good luck.

---

### Post by m.musashi on 2006-04-03
I've been looking for a way to do this too. I came across [partimage](http://www.partimage.org/Main_Page) which sounds like a good option. I haven't tried it yet but I like that is says images can be compressed and stored on removalble media. I'd like to put an image on a DVD so I'm going to give this a try.

Anyone have any experience with this and suggestions?

---

### Post by Meteor on 2006-11-11
This thread seems to have died a natural (or unnatural death) but I'm hoping to revive (restore) it...

I'm a newbie using Ubuntu 6.10 and am looking for a way to [U]easily[U] backup my hard drive. I have an external drive that I used with WinXP files just doing a (excuse the trademark) 'ghost' of the files. Fortunately, I have never (yet) had to restore my files. Making the backup (I did NOT use Symantec's program) was easy. Just answer a few questions and tell the program to do it.

Is there a program for Ubuntu/Linux that will fully back up all files and then do incremental backups on a scheduled or selected basis without having to fiddle around on the command line? (I haven't quite figured out the command line yet and haven't used one since M$ DOS...)

I looked at the link for Partition Image but can't see where it's developed for Ubuntu. Synaptic says that the only choice in 'rdiff-backup' and it appears to be run from a command line.

Assistance on this would be appreciated. Losing the data on a hard drive is not something I wish to experience.

Thank you,
Meteor

---

### Post by drpaul on 2006-11-11
partimage works for its intended purpose. It doesn't know about files.

File backup usually uses tar in some form. There are probably gui interfaces available out there, but man tar will show you the basics pretty easily. Put your backup on some external or secondary disk storage so you'll have some safety margin for your primary storage crashing.

HTH

Paul

---

### Post by Meteor on 2006-11-12
Thank you, drpaul, for your suggestion. I'll take a look at 'man tar' and see what it says. I hope that it will enable me to compress all my files including settings, bookmarks, etc., and then copy the 'tar' file(s) to my external hard drive.

I shall take this 'challenge' after work today or tomorrow morning and see what happens.

Meteor

---

### Post by podunk on 2006-11-12
Try mondo and mindi fom the package manager. Unlike tar you can verify your backup before you burn it or transfer it. also compresses more. *Very* user friendly.

---

### Post by click4851 on 2007-01-23
I am also interested in mondo and mindi, although Ive not had much luck.

---

