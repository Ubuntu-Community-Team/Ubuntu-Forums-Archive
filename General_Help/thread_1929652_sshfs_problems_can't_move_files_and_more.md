---
title: "sshfs problems: can't move files and more"
date: 2012-02-22
forum: General Help
---

### Post by mbuell on 2012-02-22
I have seen some problems with sshfs, and not found any working solutions. Please read completely before replying - I have found some solutions that should have worked - but did not. 

[COLOR="DarkRed"]Basic situation:[/COLOR]
From ubuntu desktop (10.04 lts, gnome) I have been using sshfs to connect a share from my ubuntu server. I've been doing this for well over a year. The same directories are shared via samba for my Windows machines. Prior to Ubuntu 10.04 I had openSuse 11.2 on the same hardware. 

[COLOR="DarkRed"]The Problems:[/COLOR]
encfs can not open an encrypted file on the sshfs directories. I can not move a file from one spot to another on these directories. I can copy, I can delete. But I can not move a file - either through Nautilus or from the CLI using mv. 

These actions CAN be done when connecting to the server using a cifs (samba) mount. Both mv and the encfs files work. Nothing else has changed. I simply mount the same location using samba instead of sshfs.

[COLOR="DarkRed"]What Was Checked:[/COLOR]
Permissions have been checked. All permissions are correct and identical between machines. User name and group name have the same ID# on both machines. 

Sshfs has been noted to have a problem with mv. 
[COLOR="Blue"][/2008/08/10/short-tip-moving-files-on-sshfs-mounts]("http://liquidat.wordpress.com/2008/08/10/short-tip-moving-files-on-sshfs-mounts/#")[/COLOR]
[COLOR="Blue"][sourceforge mediawiki SshfsFaq]("http://sourceforge.net/apps/mediawiki/fuse/index.php?title=SshfsFaq#Configuring_the_ssh_connection")[/COLOR]
The "workaround" option is supposed to fix this. In my case, it does not. 


[COLOR="DarkRed"]Why sshfs and observations:[/COLOR]
I originally used sshfs because, at the time, I was setting up my first samba server, and I was having issues getting to the samba share from the linux box. So, I did it that way, it worked, and I didn't have any problems that I recall. I surely must have tried to move files around in the shared directories, but it is possible that I did not do so in all that time. As I said - I also connect to the same directories from other machines that are running windows. The encfs directories are in a similar status - originally to get them available from all the machines I switched to Truecrypt. Eventually Truecrypt failed to open the encrypted files from one machine - so I copied the encrypted stuff back to encfs directories on to my local drive to do what I needed. Figured I would get to fixing the problem eventually. Now that I am saying this - that Truecrypt failure may have been caused by whatever is causing the same issue today. But that is tmi, probably. 

[COLOR="DarkRed"]Questions:[/COLOR]
Anybody have any ideas about what is going on with sshfs? Is sshfs just buggy enough that it isn't up-to-speed? 

Am I on a wild-goose-chase for security using sshfs inside my network when I have a router with good WPA password security? 

Is sshfs necessary or advisable when connecting to this server using a VPN tunnel through the above-mentioned router?

---

### Post by roelforg on 2012-02-22
Could you open a terminal, cd in to the sshfs mount and run ls -la for me?

---

### Post by mbuell on 2012-02-25
Sure, I can do that. Sorry for the delayed response - thought I set this thread to notify. 

```
duck@duck-desktop:~/share2$ ls -la
total 902300
drwxrwx---  1 duck zeron      4096 2012-02-23 20:59 .
drwxr-xr-x 57 duck duck       4096 2012-02-25 09:48 ..
-rwxrwxrwx  1 duck zeron   2591191 2009-03-29 13:33 01292009.mp3
-rw-------  1 duck zeron   4616281 2007-02-18 06:42 bkm_full-4.0.6.exe
-rwx------  1 duck zeron    176496 2010-05-29 21:48 bookmarks_susemozilla_edited_052810.html
-rw-r-----  1 duck zeron    575945 2011-01-10 08:45 DokanInstall_0.6.0.exe
-rw-r-----  1 duck zeron   1063646 2011-11-02 04:52 encfs.zip
drwxrwx---  1 duck zeron      4096 2011-07-22 23:16 gb_senior_page_photo_shoot
drwxrwx---  1 duck zeron      4096 2011-07-22 23:16 Graemes
-rw-------  1 duck zeron  10064279 2008-11-30 12:17 GreatWar.zip
-rwxr--r--  1 duck duck        374 2012-02-23 20:59 KINGSTON (E) - Shortcut.lnk
-rwxr--r--  1 duck zeron   3170441 2010-05-22 15:12 klinger!.JPG
drwxrwx---  1 duck zeron     16384 2010-04-16 15:43 lost+found
drwxrwx---  1 duck zeron      4096 2012-02-23 21:15 Lr1
drwxrwx---  1 duck zeron      4096 2012-02-23 21:02 Lr2
drwxrwx---  1 duck zeron      4096 2012-02-21 17:23 mark
-rw-------  1 duck zeron    743904 2006-03-24 15:14 Operation Overlord_0001.zip
-rwxr--r--  1 duck zeron     16384 2010-12-12 19:55 Revised Bedside sing log FY2010-1.xls
-rw-------  1 duck zeron   4382413 2009-07-31 16:22 The Battle of Bunker Hill.zip
-rw-------  1 duck zeron  12575391 2009-07-06 20:56 The Great War - Somme.zip
drwxrwx---  1 duck zeron      4096 2010-04-26 11:16 .Trash-1000
-rwxr--r--  1 duck zeron 721127424 2012-01-06 15:21 ubuntu-10.04.3-desktop-i386.iso
-rw-------  1 duck zeron   3984860 2006-08-18 15:47 Utah Beach.zip
-rw-------  1 duck zeron   6863866 2008-12-18 19:05 Verdun.zip
-rw-------  1 duck zeron    379858 2010-06-16 19:08 water_wave_surfing-1280x1024.jpg
-rw-r--r--  1 duck zeron         2 2011-12-03 17:59 .windows-serial
drwxrwx---  1 duck zeron     20480 2010-04-22 14:11 Zan's Documents
-rwxr--r--  1 duck zeron 151512576 2010-11-01 20:40 zaSuiteSetup_93_037_000_en.exe


```

I tell ya what - looking at that listing - I'm wondering if somehow the permissions thing is still getting in the way. I know I've reset them a few times - and I'm pretty sure I did that recursively - but I see files at this level using the group name of an older username. The group NUMBER still matches - but maybe not the name. Hmmmmm -  investigation time.

---

### Post by mbuell on 2012-02-25
Well - not sure still. The directories and files in the shared area have two groups - 1000 and 1001. Both groups exist on both machines, with the matching group names. All the files and directories in the shared area belong to the same user - the same user that I log in as when using sshfs.

Still investigating.

One hour later: 
Let's look at the permissions. User duck is a member of group duck and zeron on both machines. Groups duck and zeron are 1000 and 1001, identically on both machines. 
Using Nautilus to view the sshfs directory - at the base level - the file zaSuiteSetup etc will move to directory Mark, but not to directory Lr1. This file is owned by group 1001 - zeron. Both directories are also owned by that group. 

I dig a little deeper. Permissions do not seem to be it. However - here is something - Lr1 is on a different partition. A different hdd, for that matter. I try to move a file from one location on that partition to another directory on that partition. I can. The first move (zasuitesetup etc) was also from one directory to another on the same partition. BUT, when I try to move a file between directories on the different partitions - it fails. 

I will look again later, but at the moment this is the most information I have gotten. This small test seems to indicate a definite correlation between the different partitions and the file move problems. 

This is still very odd - anybody know why sshfs would even recognize that they were different partitions?

---

### Post by mbuell on 2012-02-26
I rewrote the situation - hopefully to make it clearer. 


I looked at permissions again, but I still found nothing in permissions that seems to be related to the symptoms. However, here is what I DID notice this time: it seems to be related to partitions. 

A while back, on the server, I mounted a new hard drive in the shared area when I needed more space. This mount has seemed to be transparent in normal usage. I've been using the space for months. However, it is entirely possible that I never tried to move files across the partition boundaries before. 

It is mounted like this. Everything under server-share is shared and visible to all users. I don't need security in this situation. Server-share is on its own partition on the primary hard drive. 

server-share/samba user directories/ 
server-share/Lr1/ (this is the main partition for the new hard drive)

So - on the first partition, where "server-share" is, I can copy and move files. Encfs can open an encrypted directory, as it should. 

But when I try to move files to the new partition, it doesn't work when using sshfs. And, encfs will not open encrypted directories that reside on that newer partition. I can move files from one location on the new partition to another location, but not off the partition. 

Using samba to make the connection, the partitions are transparent, as I would expect them to be. Using sshfs - they seem to be, except as noted. I can not move files between them, and encfs will not open an encrypted directory that resides in the 2nd partition. 

Is that strange enough for ya?  :D

---

### Post by mbuell on 2012-04-08
bump - still no solution. Using workarounds and submitted bug report to ssh. However, I am not convinced it is an ssh bug. On my laptop, when I run wireless (not when I am hard-wired) and try to use samba to connect I get a similar problem - I can't do anything between the partitions. I can access and act on stuff in each partition - but not move between them. 

Could be coincidental. Maybe it has something to do with the fstab settings?

---

