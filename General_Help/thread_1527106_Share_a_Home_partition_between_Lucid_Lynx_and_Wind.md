---
title: "Share a Home partition between Lucid Lynx and Windows 7"
date: 2010-07-08
forum: General Help
---

### Post by cfalzone on 2010-07-08
Hi guys,

I was going to freshly format my laptop with Windows 7 x86_64 and Lucid Lynx x86_x64... I have a HUGE amount of media (music, videos, pictures, documents) and I don't keep all of it on my external harddrive.

The plan is to have the basic 2 partitions for Windows 7 and Ubuntu but I would like to have a 3rd partition that is just for media that I could share between the two OSes.

I guess I would create symbolic links in the Ubuntu Home folder to point to the partition with media and in Windows I could probably just add those folders to libraries (unless someone knows how to move the User folder to another parition?)

What should I format this new partition as?  NTFS?  It needs to support files larger than 4GB and Windows can't read/write to basically anything.

Any help/suggestions?

---

### Post by Yarui on 2010-07-08
If it needs to be able to store files over 4GB then fat is out, ntfs is what I would go with since you need windows to be able to read it.  You shouldn't really need to do anything special to make the partition show up on either OS.  If you just format it as NTFS and don't do anything to it, Windows should automatically mount it as a disk drive, most likely your D:/ drive.

Ubuntu should also automatically detect it and it will show up in your "places" menu.  When you open it, you will have to enter your password so that it can be mounted with gksu, and then there will be a disk icon on your desktop to show that it is mounted.

---

### Post by oldfred on 2010-07-09
All my  linux data is in a hidden mount of a data partition and every folder is linked into /home replacing the standard /home folders.
I used to directly mount my NTFS partition that I share with windows into /home but am in the process of mounting it like my /data and linking it into /home.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by cfalzone on 2010-07-09
good replies.  I'm still thinking of going the route of linking the partition into /home and replacing the standard home folders as oldfred suggested.

One concern is that if I make my fstab automount the NTFS partition it will then always appear on my desktop... I don't really like that and I do want to still have some drives appear (like externals) so the gconf-editor configuration won't help

---

### Post by Vaphell on 2010-07-09
edit: not read whole stuff and mentioned gconf, my bad :)

i think i've read somewhere that stuff mounted in media is shown, but if you mount it somewhere else like in /mnt it won't - i can't say if that's the case though, so try that and see what happens

[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

---

### Post by oldfred on 2010-07-09
It was my understanding that anything in /media and /home appears again unless you make special settings in fstab.

I mount in /usr/local, and had to create /usr/local/fred and /usr/local/fred/shared. Then I link from that. Ignore extra str & " as this is from a bash file I run to reconnect everything on a new install.
str5="# Entry for /dev/sdc2 :"
str6="UUID=44332FD360AA9657                      /usr/local/fred/shared  ntfs-3g      defaults                             0  0  "

From /home
ln -s /usr/local/fred/shared

But for all my data folders
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Pictures
#ln -s /usr/local/fred/data/Videos
When you want the link in the folder you run from, it defaults, so you do not have to specify where.
 man ln
 the 2nd form, create a link to TARGET in the current directory.

I have a lot of folder in /data to link:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done
Does all of them in one command.

---

