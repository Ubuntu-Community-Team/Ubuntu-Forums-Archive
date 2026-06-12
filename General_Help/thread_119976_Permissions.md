---
title: "Permissions"
date: 2006-01-20
forum: General Help
---

### Post by bschuteker on 2006-01-20
I may be a noob but I am not entirely stoopid.;)  I have been dual booting for about a month now. Can't get rid of M$ because if propriatary software for work. I am getting closer and closer to using Ubuntu as my primary though.

I took a big step towards this today. I have an 80 Gb HD in my laptop. 15 for Win, 50 for data storage and 15 for Breezy. I converted the 50 storage partition to FAT32 so that I can still access it from Win but also write to it from Ubuntu. I have multiple backups so I just deleted everything on it, converted and then reloaded what I wanted. All that went just fine and when I booted Ubuntu for the first time I went in and changed fstab. The drive mounts like it used to but of the 10 folders on the part 2 of them come up locked. This is driving me nuts. Why would only some folders do it and not all of them?  

Here is fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2 /data vfat iocharset=utf8,umask=000 0 0

Here are the permissions:

bill@ubuntu:~$ sudo ls -ld /data
drwxrwxrwx  14 root root 4096 2006-01-20 20:14 /data
bill@ubuntu:~$ sudo ls -ld /data/docs
dr-xr-xr-x  14 root root 8192 2006-01-20 17:00 /data/docs
bill@ubuntu:~$ sudo ls -ld /data/images
drwxrwxrwx  2 root root 4096 2006-01-20 16:57 /data/images

Data is the partition, images is not locked but docs is?????????:confused: 

if I do chmod 777 /data/docs will it also change permissions on all subfolders?

You guys are great so thanks in advance,

Bill

---

### Post by earobinson on 2006-01-20
fat32 dose not support perminsions as I understand it, this is really weird.

EDIT: [yup im correct]("http://www.linuxquestions.org/questions/showthread.php?t=136031")

---

### Post by bschuteker on 2006-01-20
This is now getting more confusing. FAT32 must somehow support permissions because It has me locked out of some folders due to permissions. 

I was expirementing a bit and tried "chmod 777 music" it did change permissions for the music folder but not for all of the sub-folders. when I explored the sub-folders that were still locked I found that they all contained a file called desktop.ini. Hmmmmm, so I booted in to M$ and deleted all of them. Then when I went back to Breezy that had fixed most of the problem. There are still 3 folders that are locked. When I go in to them they show a file named desktop.ini, but when I open the folder in windows desktop.ini is nit there. Bizzare!

Somewhat related question. When I am navigating in terminal I can cd in to a folder that has a one word file name but not a folder with a 2 word file name. ie. cd korn works but cd marilyn manson does not. Am I missing something?

---

### Post by earobinson on 2006-01-20
that is really weird,

as for your second issue to get use cd "marilyn manson" or cd marilyn\ manson

---

### Post by carlosqueso on 2006-01-20
I can help you with two things.  If you want to chmod subfolders, you need to use -R after the chmod command.  This will cause it to change the permissions on all of the folders.  Secondly, linux requires you to put a "\" (backslash) before certain characters, one of which is the space.  A nice shortcut is to type cd and start typing the directory.  Once you get far enough that no other name has the same beginning, hit the tab key and it'll finish it for you.   A great trick for lazy typists like me.

Edit: Dang....I type too much too slowly.

---

### Post by earobinson on 2006-01-20
carlosqueso (Its ok its + your answer was more in depth than mine, + if we both say the same thing chances are we are correct giving the op more info to use) the problem is fat32 should not have permisions, I know my fat drive has none.

---

### Post by bschuteker on 2006-01-20
carlosqueso,

Thanks, the -R worked YAY!!! but I still can not cd in to a dir with a 2 word file name. When I hit tab the puter makes a strange sound and does nothing. Any other ideas????

Bill

---

### Post by bschuteker on 2006-01-20
[QUOTE=earobinson]that is really weird,

as for your second issue to get use cd "marilyn manson" or cd marilyn\ manson[/QUOTE]
 

Neither of these is working...

---

### Post by carlosqueso on 2006-01-20
first, are you in the directory that contains "marilyn manson"?.  Second, make sure you capitalize any letters that are capitalized on the folder as linux is case-sensitive (unlike DOS or windows).  If you've checked those two things, try typing "cd marilyn" and hitting tab twice.   A couple of choices should come up.  Just copy the one of those you want EXACTLY.

---

### Post by bschuteker on 2006-01-20
OK now that I feel quite stupid... I'm going to bed. It is rather late here in the desert. 

The frickin caps got me, I had tried using caps without the backslash and then when I was trying the tab and backslash I guess I forgot to try caps also. 

Thanks for the help I got it now.:D

---

### Post by earobinson on 2006-01-20
If that dont work post the ls -la of the dir

EDIT: never mind guess Im a slow typer now. Glad to know it works now

---

### Post by carlosqueso on 2006-01-20
Glad it worked....those caps got me when I switched from winders too.

---

