---
title: "Home Folder Permissions"
date: 2010-09-29
forum: General Help
---

### Post by osarusan on 2010-09-29
Recently I moved my /home folder to another partition using the instructions here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

It all appeared to have worked fine -- I can log in fine, and the shortcuts to my home folder, pictures, etc all work fine.

However just the other day I noticed a strange problem with Pulseaudio not displaying the volume control properly. Sound works, but I keep getting the "Waiting for sound system" problem. After searching around some more, I saw this is related to permissions, as running from the terminal gives me the error E: core-util.c: Home directory /home/osarusan not ours. I also have the same problem with anything using Wine.

I tried a number of commands to give my username ownership of my home folder, but none of them worked. I tried using sudo nautilus and doing it with the GUI, but every time I select my username it immediately reverts back to root.

In short, root owns my home directory and no matter what I try I can't change that. Please help me!

---

### Post by tgm4883 on 2010-09-29
This would set the owner and group on the path and all subdirectories
```
sudo chown -R user:group /path/to/home/dir
```

---

### Post by yetiman64 on 2010-09-29
> **osarusan said:**
> In short, root owns my home directory and no matter what I try I can't change that. Please help me!
To change this in terminal
```
sudo chown -R <username>:<username> /path/to/home/dir
```where chown -R recursively changes ownership of your files and folders.
and /path/to/home/dir is your home directory. Replace <username> with your actual username. Anything in your home directory changed to roots ownership will be reverted with this. 

Also do NOT use sudo and nautilus, use gksudo or gksu, as doing this can leave folders/files in the home directory in root's ownership accidently. See Graphical Sudo section of link #4 in my sig for further explanations.

---

### Post by osarusan on 2010-09-29
I actually meant to say that I used gksudo nautilus, but yes, that's a very good point to mention -- thank you.

I tried that command a few times before, and I just tried it again now and restarted. No avail -- root remains the owner of all the files and folders in the home directory. :-\ Any idea why?

---

### Post by yetiman64 on 2010-09-29
> **osarusan said:**
> I actually meant to say that I used gksudo nautilus, but yes, that's a very good point to mention -- thank you. That's very good :wink:

> **osarusan said:**
> I tried that command a few times before, and I just tried it again now and restarted. No avail -- root remains the owner of all the files and folders in the home directory. :-\ Any idea why?

Try in terminal
```
ls -la /path/to/home
``` mainly to check what file/folder permissions are in play, may be stopping even root changing anything. Note, only navigate to /home and not /home/<username>.

---

### Post by osarusan on 2010-09-29
Thanks for the quick reply. I get this:

drwxrwxrwx  1 root root  20480 2010-09-28 07:36 .
drwxr-xr-x 24 root root   4096 2010-09-29 14:34 ..
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 AUTOEXEC.BAT
-rwxrwxrwx  1 root root     90 2010-09-28 07:36 bcmwl5.log
-rwxrwxrwx  1 root root    211 2010-08-31 14:00 boot.ini
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 CONFIG.SYS
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 IO.SYS
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 MSDOS.SYS
-rwxrwxrwx  1 root root  47772 2005-03-25 21:00 NTDETECT.COM
-rwxrwxrwx  1 root root 297072 2010-08-31 10:24 ntldr
drwxrwxrwx  1 root root  28672 2010-09-29 15:30 osarusan
drwxrwxrwx  1 root root      0 2010-08-31 23:09 RECYCLER
-rwxrwxrwx  1 root root   1253 2010-09-29 07:58 sti.log
drwxrwxrwx  1 root root      0 2010-09-28 07:36 SWSetup
drwxrwxrwx  1 root root   4096 2010-08-31 09:37 System Volume Information
-rwxrwxrwx  1 root root    988 2010-09-16 12:58 UFantasy.ini
drwxrwxrwx  1 root root      0 2010-09-16 12:53 USBStorage

The other files there are related to a Windows install on a separate partition. I didn't imagine they would be doing anything to interfere with this, but could they??

Come to think of it, the partition my /home directory is on is formatted NTFS. Could that have something to do with it??

---

### Post by yetiman64 on 2010-09-29
> **osarusan said:**
> Thanks for the quick reply. I get this:

drwxrwxrwx  1 root root  20480 2010-09-28 07:36 .
drwxr-xr-x 24 root root   4096 2010-09-29 14:34 ..
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 AUTOEXEC.BAT
-rwxrwxrwx  1 root root     90 2010-09-28 07:36 bcmwl5.log
-rwxrwxrwx  1 root root    211 2010-08-31 14:00 boot.ini
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 CONFIG.SYS
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 IO.SYS
-rwxrwxrwx  1 root root      0 2010-08-31 09:33 MSDOS.SYS
-rwxrwxrwx  1 root root  47772 2005-03-25 21:00 NTDETECT.COM
-rwxrwxrwx  1 root root 297072 2010-08-31 10:24 ntldr
drwxrwxrwx  1 root root  28672 2010-09-29 15:30 osarusan
drwxrwxrwx  1 root root      0 2010-08-31 23:09 RECYCLER
-rwxrwxrwx  1 root root   1253 2010-09-29 07:58 sti.log
drwxrwxrwx  1 root root      0 2010-09-28 07:36 SWSetup
drwxrwxrwx  1 root root   4096 2010-08-31 09:37 System Volume Information
-rwxrwxrwx  1 root root    988 2010-09-16 12:58 UFantasy.ini
drwxrwxrwx  1 root root      0 2010-09-16 12:53 USBStorage

The other files there are related to a Windows install on a separate partition. I didn't imagine they would be doing anything to interfere with this, but could they??

Come to think of it, the partition my /home directory is on is formatted NTFS. Could that have something to do with it??
Saw that and nearly died of shock :lolflag:. What are windows files doing in your home directory. Looks like something went horribly wrong during the /home move, also yeah NTFS is absolutely no good for a Linux home folder (NTFS won't support Linux permissions as far as I understand - maybe the cause of it all etc). In all seriousness I better leave your question to someone more experienced. Good Luck osarusan.

---

### Post by osarusan on 2010-09-29
Haha yea, well Windows automatically mounts that partition since it's NTFS, and it puts files on there as it pleases, as Windows is insane like that. At first I was deleting the files, but Windows replaces them every time I boot up, so I just let them be.

But yeah, the permissions thing might be the issue. Thanks for helping me realize that! I'll have a look to see if there's any way to get it to work this way, or else I'll just have to reformat to a linux file system.

Thanks!

---

### Post by yetiman64 on 2010-09-29
> ...I'll just have to reformat to a linux file system. Yes that sounds better for a Linux home partition :). I fully suspect that will fix all the ownership and permissions hassles you're currently facing.

---

### Post by osarusan on 2010-09-29
Well, that did it! It was definitely an NTFS problem. I can't believe I hadn't thought of that on my own, but there ya go. Thanks a lot for helping me out with that one. I reformatted as ext4 and now the command fixed the files!

---

### Post by MLawrence on 2011-09-17
Well, I too have an issue with my home folder permissions.

chown gives me this:
mario@DASAKAMOV:~$ sudo chown -R mario:mario /home/mario
chown: cannot access `/home/mario/.gvfs': Permission denied

ls on the folder gives me this:
mario@DASAKAMOV:~$ ls -la /home/mario
total 892
drwxr-xr-x 36 mario mario   4096 2011-09-14 18:29 .
[COLOR=Red]drwxr-xr-x  3 root  root    4096 2011-09-11 23:18 ..[/COLOR]
drwx------  3 mario mario   4096 2011-09-13 19:18 .adobe
drwxr-xr-x  2 mario mario   4096 2011-09-13 19:24 Audiobooks
-rw-------  1 mario mario    794 2011-09-17 08:25 .bash_history
-rw-r--r--  1 mario mario    220 2011-09-11 23:18 .bash_logout
-rw-r--r--  1 mario mario   3353 2011-09-11 23:18 .bashrc
drwx------ 18 mario mario   4096 2011-09-14 18:30 .cache
drwxr-xr-x  3 mario mario   4096 2011-09-14 18:29 .compiz-1
drwxr-xr-x 15 mario mario   4096 2011-09-14 10:46 .config
drwx------  3 mario mario   4096 2011-09-12 00:03 .dbus
drwxr-xr-x  2 mario mario   4096 2011-09-16 09:57 Desktop
-rw-r--r--  1 mario mario     92 2011-09-14 16:16 .dmrc
drwxr-xr-x  6 mario mario   4096 2011-09-11 23:18 Documents
drwxr-xr-x  2 mario mario   4096 2011-09-12 00:03 Downloads
-rw-------  1 mario mario     16 2011-09-12 00:03 .esd_auth
-rw-r--r--  1 mario mario    179 2011-09-11 23:18 examples.desktop
drwxr-xr-x  2 mario mario   4096 2011-09-17 07:57 .fontconfig
drwxr-xr-x  5 mario mario   4096 2011-09-17 08:27 .gconf
drwx------  2 mario mario   4096 2011-09-17 08:32 .gconfd
drwxr-xr-x  8 mario mario   4096 2011-09-14 17:31 .gnome2
drwx------  2 mario mario   4096 2011-09-12 00:04 .gnome2_private
drwx------  2 mario mario   4096 2011-09-14 17:11 .gnupg
drwxr-xr-x  2 mario mario   4096 2011-09-16 23:22 .gstreamer-0.10
-rw-r--r--  1 mario mario    164 2011-09-14 18:21 .gtk-bookmarks
dr-x------  2 mario mario      0 2011-09-17 08:27 .gvfs
[COLOR=Cyan]-rw-r--r--  1 mario mario   2640 2011-09-14 16:16 .ICEauthority[/COLOR]
drwxr-xr-x  3 mario mario   4096 2011-09-16 23:42 .icons
drwxr-xr-x  3 mario mario   4096 2011-09-12 16:47 .libreoffice
drwxr-xr-x  3 mario mario   4096 2011-09-12 00:03 .local
drwx------  3 mario mario   4096 2011-09-13 19:18 .macromedia
drwx------  3 mario mario   4096 2011-09-13 19:05 .mission-control
drwxr-xr-x  4 mario mario   4096 2011-09-12 00:04 .mozilla
drwxr-xr-x  2 mario mario   4096 2011-09-14 16:29 Music
-rw-------  1 mario mario     59 2011-09-14 09:44 nano.save
drwxr-xr-x  2 mario mario   4096 2011-09-12 00:04 .nautilus
drwxr-xr-x  2 mario mario   4096 2011-09-14 16:29 Pictures
drwxr-xr-x  2 mario mario   4096 2011-09-13 19:24 Podcasts
-rw-r--r--  1 mario mario    675 2011-09-11 23:18 .profile
drwxr-xr-x  2 mario mario   4096 2011-09-12 00:03 Public
drwx------  2 mario mario   4096 2011-09-17 08:32 .pulse
-rw-------  1 mario mario    256 2011-09-12 00:03 .pulse-cookie
-rw-r--r--  1 mario mario      0 2011-09-13 19:09 .sudo_as_admin_successful
drwxr-xr-x  2 mario mario   4096 2011-09-12 00:03 Templates
drwxr-xr-x  4 mario mario   4096 2011-09-16 23:46 .themes
drwx------  4 mario mario   4096 2011-09-12 00:05 .thumbnails
-rw-r--r--  1 mario mario 642987 2011-09-11 23:18 TranscodedWallpaper.jpg
drwxrwxr-x  2 mario mario   4096 2011-09-13 19:04 Ubuntu One
drwxr-xr-x  2 mario mario   4096 2011-09-14 16:19 Videos
-rw-------  1 mario mario  20815 2011-09-17 08:32 .xsession-errors
-rw-------  1 mario mario  47420 2011-09-14 11:04 .xsession-errors.old


Ive highlighted in red, what I'm assuming is the problem.
I've highlighted in cyan, a file that my system says it cannot update everytime I log in.

Since I don't identify any Windows files in this list, I'm assuming there's a way to remedy this without doing something as drastic as a reformat.

I would like to learn how to remedy these two situations, for future reference.
This is my second time posting. :)

---

### Post by MLawrence on 2011-09-17
As an addendum, I used sudo before a gui program. I'm assuming that's the cause of my issue.

I did sudo deja-dup. Couldnt figure out why a previous backup wasn't being restored to my new ubuntu install. Im guessing the encryption was a problem (definitely wasn't necessary), and an actual restore point was missing. Again, I'm just assuming.

Any help would be appreciated.

I understand the thread says SOLVED, but is it appropriate to open a new thread, about a previously addressed issue? :(

---

### Post by Morbius1 on 2011-09-17
> s on the folder gives me this:
mario@DASAKAMOV:~$ ls -la /home/mario
total 892
drwxr-xr-x 36 mario mario   4096 2011-09-14 18:29 .
[COLOR=Red]drwxr-xr-x  3 root  root    4096 2011-09-11 23:18 ..[/COLOR]The line with the "." at the end refers to /home/mario and is as it should be.
The line with the ".." at the end refers to /home itself. Root owns /home not you so it too is as it should be.

As for the [COLOR=Black]ICEauthority line except for the last 2 "r"'s is also correct so there really is no issue here.[/COLOR]

---

### Post by MLawrence on 2011-09-17
> **Morbius1 said:**
> The line with the "." at the end refers to /home/mario and is as it should be.
The line with the ".." at the end refers to /home itself. Root owns /home not you so it too is as it should be.

As for the [COLOR=Black]ICEauthority line except for the last 2 "r"'s is also correct so there really is no issue here.[/COLOR]

Apparently, those last 2 "r"s are causing a window pop up that delays my login by an additional 5 seconds. It's picking at the nits, but I don't have much patience with my machine.

I know this isn't the thread for the second issue, however. So I'll do some more searching.

Thanks for your help. :)

---

