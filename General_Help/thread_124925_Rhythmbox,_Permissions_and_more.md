---
title: "Rhythmbox, Permissions and more"
date: 2006-02-02
forum: General Help
---

### Post by xerman on 2006-02-02
Hello forum,

I've found certain issues when I try to change author, title, and genre to audio files in Rhythmbox. Firs I'll copy the fstab for the record:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext3    defaults        0       2
/dev/sdb1       /home           ext3    defaults        0       2
/dev/sdb2       /media/datos    vfat    rw,user,umask=000	0	0
/dev/sda1       /media/windows  ntfs    umask=0222,nls=utf8	0	0
/dev/sda4       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

The issue I have is due to the fact of having /media/datos as a drive for storing any kind of data so this is shared between ubuntu and win.
I can read, delete and write anything to /media/datos though owner is "root" in fact, any file in that drive is owned by root. If I create a folder, the folder owner is root, if I write a text doc in OOO, the owner is root. I have not activated root account though.

The funny thing happens when I open audio files located in /media/datos in Rhythmbox and I try to change those audio file parameters, I'm not allowed. If I copy those files in /media/datos to /home I get the same thing, I can't change nothing though owner and permissions are set to user's.

And the funniest thing is that when I close Rhythmbox, I get nautilus file browser locale changed from spanish to english.

This is so weird I'm shocked.

Any ideas?
Thanks.

By the way, I'm on Breezy AMD64.

---

### Post by lysis on 2006-02-02
my understanding is rhythmbox does not yet support editing id3 tags.  if this isn't what you're talking about, i'm sorry for my mis-interpretation.

/media/datos . . .

everything on media/datos is owned by root?   chown -R /media/datos

that would fix that . . . if you did anything with sudo -s inside there, that would explain why it was owned that way.  if you did NOT set the ownership on /media/datos then it is by default owned by root. (all things are)


it IS true that root is disabled, but it can still own since sudo can do root commands. =)

---

### Post by xerman on 2006-02-05
[QUOTE=lysis]
everything on media/datos is owned by root?   chown -R /media/datos

that would fix that . . . if you did anything with sudo -s inside there, that would explain why it was owned that way.  if you did NOT set the ownership on /media/datos then it is by default owned by root. (all things are)[/QUOTE]

Hi lysis,

I had already tried that "chown -R user /media/datos" even with "sudo" but anytime I try I get "Operation not allowed" all the time and cannot change owner of that drive.
Actually, I did not set the ownership on /media/datos, in fact, I did not know where to set that when I installed Ubuntu. I just know that /media/datos is owned by root, and group is root too.
Though I don't have issues when writing to /media/datos, the point is when uploading files to a web server, as they are owned by root with root file permissions, so I cannot get to the files on the web server, and this is annoying.

I've got the rhythmbox stuff, and you might be right on the not possible to write idtags in rythmbox, as I tried banshee and this one allows it perfectly.
Thanks

---

