---
title: "Cannot extract frame (252, 0) from grid"
date: 2009-12-16
forum: General Help
---

### Post by Bartender on 2009-12-16
Any gedit command returns the odd error in title, then a second later I get the file.

If I type "sudo gedit" I don't get the error message.  This first popped up yesterday but I'm not into terminal on a regular basis.

Googled it a bit, searched Ubuntu Forums, not seeing any clear ideas on what causes this.

Also, noticing the cursor sometimes goes from solid black to a white box with thin black outline, and PC goes unresponsive.  A few seconds later it snaps out of it.

---

### Post by pt123 on 2009-12-17
me too, installed Karmic and I am having the same error message when running gedit with a file,

the error msg does not show when just gedit is run

** (gedit:7121): WARNING **: Cannot extract frame (252, 0) from the grid

---

### Post by Bartender on 2009-12-20
Hey, pt, thanks for writing!

I'm still on 9.04.  Since I don't go into terminal a lot I can't verify when this started, but wondering if it has something to do with an update?  Didn't do this before, I don't think.  

On your machine, does it matter whether you type sudo before or not?

---

### Post by louieb on 2009-12-20
Use** ls -la  **and look for files in your home folder owned by root. 

If you find one or more change the owner back to you. 

Thats one of the reasons you want to use gksudo to run graphical apps such as gedit.

---

### Post by pt123 on 2009-12-20
> **Bartender said:**
> Hey, pt, thanks for writing!
On your machine, does it matter whether you type sudo before or not?
Both ways I get the same message.

> **louieb said:**
> 
Thats one of the reasons you want to use gksudo to run graphical apps such as gedit.
even using gksudo I get the same message

Even calling a gedit file in my home dir I get that warning.

---

### Post by Bartender on 2009-12-20
louieb, I'm sorry, I'm just not very familiar with file ownership, permissions, etc.  Below is the output of ls -la.  What am I looking for?  I've never understood the distinction between sudo and gksudo, even though folks like aysiu have tried to enunciate it.

```
bpbar@bpbar-laptop:~$ ls -la 
total 700 
drwxr-xr-x 80 bpbar bpbar   4096 2009-12-20 14:35 . 
drwxr-xr-x  4 root  root    4096 2009-07-10 12:13 .. 
drwx------  3 bpbar bpbar   4096 2009-07-11 12:53 .adobe 
drwxr-xr-x  2 bpbar bpbar   4096 2009-09-01 11:15 .aptoncd 
drwxr-xr-x  2 bpbar bpbar   4096 2009-10-16 15:28 .audacity1.3-bpbar 
drwxr-xr-x  5 bpbar bpbar   4096 2009-10-16 15:28 .audacity-data 
drwxr-xr-x  6 bpbar bpbar   4096 2009-11-21 07:06 Audiobooks 
-rw-r--r--  1 bpbar bpbar   1193 2009-09-07 09:17 .banter.log 
-rw-------  1 bpbar bpbar   7368 2009-12-20 14:35 .bash_history 
-rw-r--r--  1 bpbar bpbar    220 2009-07-10 12:13 .bash_logout 
-rw-r--r--  1 bpbar bpbar   3115 2009-07-10 12:13 .bashrc 
drwx------  2 bpbar bpbar   4096 2009-07-11 13:35 .bcast 
drwx------  2 bpbar bpbar   4096 2009-08-14 12:44 .bogofilter 
drwxr-xr-x  9 bpbar bpbar   4096 2009-12-18 07:41 .cache 
drwxr-xr-x  2 bpbar bpbar   4096 2009-08-12 11:38 .cddb 
drwx------  3 bpbar bpbar   4096 2009-07-11 12:02 .compiz 
drwxr-xr-x 17 bpbar bpbar   4096 2009-12-18 07:40 .config 
-rw-r--r--  1 bpbar bpbar  14472 2009-12-14 10:01 .conkyrc 
-rw-r--r--  1 bpbar bpbar  12967 2009-12-14 09:58 .conkyrc~ 
drwx------  2 bpbar bpbar   4096 2009-11-07 16:11 .cups 
drwx------  3 bpbar bpbar   4096 2009-07-10 05:17 .dbus 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-16 13:20 Desktop 
-rw-------  1 bpbar bpbar      2 2009-12-20 13:07 .dmrc 
drwxrwxrwx 10 bpbar bpbar   4096 2009-12-14 10:06 Documents 
drwxr-xr-x  4 bpbar bpbar   4096 2009-12-16 13:20 Downloads 
drwxr-xr-x 43 bpbar bpbar   4096 2009-12-20 03:30 .dvdcss 
drwxr-x---  2 bpbar bpbar   4096 2009-08-09 14:49 .easytag 
-rw-------  1 bpbar bpbar     16 2009-07-10 05:17 .esd_auth 
drwxr-xr-x  8 bpbar bpbar   4096 2009-09-20 08:25 .evolution 
-rw-r--r--  1 bpbar bpbar    357 2009-07-10 12:13 examples.desktop 
drwxr-xr-x  2 bpbar bpbar   4096 2009-11-06 11:52 .fontconfig 
drwxr-xr-x  6 bpbar bpbar   4096 2009-08-09 15:42 FrostWire 
drwxr-xr-x  7 bpbar bpbar   4096 2009-12-15 10:28 .frostwire4.18 
drwx------  5 bpbar bpbar   4096 2009-12-20 13:07 .gconf 
drwx------  2 bpbar bpbar   4096 2009-12-20 14:36 .gconfd 
drwx------  4 bpbar bpbar   4096 2009-07-18 13:14 .gegl-0.0 
drwxr-xr-x 22 bpbar bpbar   4096 2009-11-27 20:09 .gimp-2.6 
-rw-r-----  1 bpbar bpbar      0 2009-12-18 08:22 .gksu.lock 
drwx------ 14 bpbar bpbar   4096 2009-12-20 11:59 .gnome2 
drwx------  2 bpbar bpbar   4096 2009-07-10 05:17 .gnome2_private 
drwx------  4 bpbar bpbar   4096 2009-12-08 08:54 .gnucash 
drwx------  2 bpbar bpbar   4096 2009-11-14 08:46 .gnupg 
drwxr-xr-x  3 bpbar bpbar   4096 2009-11-28 10:33 .google 
drwxr-xr-x  2 bpbar bpbar   4096 2009-07-20 10:18 .gpilotd 
-rw-r--r--  1 bpbar bpbar      4 2009-07-20 10:18 .gpilotd.pid 
-rw-r--r--  1 bpbar bpbar   1513 2009-09-03 18:09 .grip 
-rw-r--r--  1 bpbar bpbar    100 2009-09-03 18:09 .grip-oggenc 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-18 10:25 .gstreamer-0.10 
-rw-r--r--  1 bpbar bpbar    108 2009-12-20 13:08 .gtk-bookmarks 
dr-x------  2 bpbar bpbar      0 2009-12-20 13:07 .gvfs 
drwxr-xr-x  2 bpbar bpbar   4096 2009-09-01 11:35 .hotssh 
drwxr-----  2 bpbar bpbar   4096 2009-12-20 13:08 .hplip 
-rw-r--r--  1 bpbar bpbar    471 2009-09-07 06:38 .hugin 
-rw-------  1 bpbar bpbar  32832 2009-12-20 13:07 .ICEauthority 
drwx------  2 bpbar bpbar   4096 2009-11-06 12:04 .icedteaplugin 
drwxr-xr-x  8 bpbar bpbar   4096 2009-12-05 15:45 .icons 
-rw-r--r--  1 bpbar bpbar      0 2009-11-08 06:48 installed-apps 
drwx------  2 bpbar bpbar   4096 2009-10-13 03:35 Jukebox Disc 
drwx------  3 bpbar bpbar   4096 2009-07-11 12:45 .kde 
drwxr-xr-x  5 bpbar bpbar   4096 2009-07-11 13:37 kdenlive 
drwx------  2 bpbar bpbar   4096 2009-07-11 13:35 .kino-history 
-rw-r--r--  1 bpbar bpbar   2969 2009-07-11 13:35 .kinorc 
drwx------  3 bpbar bpbar   4096 2009-07-11 13:37 .local 
drwx------  3 bpbar bpbar   4096 2009-07-11 12:53 .macromedia 
drwx------  4 bpbar bpbar   4096 2009-07-13 12:30 .mozilla 
drwx------  3 bpbar bpbar   4096 2009-07-13 12:30 .mozilla-thunderbird 
drwxr-xr-x 19 bpbar bpbar   4096 2009-12-20 14:31 mp3 
drwxr-xr-x  2 bpbar bpbar   4096 2009-08-12 12:22 .mplayer 
drwxr-xr-x  5 bpbar bpbar   4096 2009-10-13 09:21 Music 
drwxr-xr-x  3 bpbar bpbar   4096 2009-07-10 05:17 .nautilus 
drwxr-xr-x  2 bpbar bpbar   4096 2009-09-03 18:03 ogg 
drwxr-xr-x  3 bpbar bpbar   4096 2009-07-12 16:55 .openoffice.org 
drwxr-xr-x  2 bpbar bpbar   4096 2009-08-14 19:15 .pdfedit 
drwxr-xr-x  3 bpbar bpbar   4096 2009-08-21 05:48 Photos 
drwxr-xr-x  2 bpbar bpbar   4096 2009-09-02 17:35 Pictures 
-rw-r--r--  1 bpbar bpbar     37 2009-08-10 15:47 .printer-groups.xml 
-rw-r--r--  1 bpbar bpbar    675 2009-07-10 12:13 .profile 
drwxrwxrwx  2 bpbar bpbar   4096 2009-11-30 12:12 Public 
drwx------  2 bpbar bpbar   4096 2009-12-20 13:07 .pulse 
-rw-------  1 bpbar bpbar    256 2009-07-10 05:17 .pulse-cookie 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-07 14:56 .qt 
-rw-------  1 bpbar bpbar   8257 2009-12-14 09:37 .recently-used 
-rw-------  1 bpbar bpbar 119544 2009-12-20 14:35 .recently-used.xbel 
-rw-r--r--  1 bpbar bpbar  39132 2009-10-24 16:46 .recently-used.xbel.M84A2U 
-rw-r--r--  1 bpbar bpbar  38238 2009-10-17 13:50 .recently-used.xbel.Y8C51U 
-rw-r--r--  1 bpbar bpbar    237 2009-11-19 07:15 .registry 
drwx------  2 bpbar bpbar   4096 2009-09-08 10:34 .remote-help-assistant 
-rw-------  1 bpbar bpbar   1629 2009-09-03 18:10 .ripperXrc 
drwxr-xr-x  2 bpbar bpbar   4096 2009-08-11 21:38 .rubyripper 
drwx------  2 bpbar bpbar   4096 2009-07-24 10:10 .scim 
drwxr-xr-x  3 bpbar bpbar   4096 2009-08-14 11:40 .scribus 
drwx------  2 bpbar bpbar   4096 2009-09-07 08:58 .ssh 
-rw-r--r--  1 bpbar bpbar      0 2009-07-10 21:50 .sudo_as_admin_successful 
drwxr-xr-x  8 bpbar bpbar   4096 2009-11-12 16:03 TAudiostuff 
drwxr-xr-x  2 bpbar bpbar   4096 2009-07-10 05:17 Templates 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-05 13:20 .themes 
drwx------  5 bpbar bpbar   4096 2009-08-22 19:38 .thumbnails 
drwxr-xr-x  5 bpbar bpbar   4096 2009-12-05 15:45 .tomboy 
-rw-r--r--  1 bpbar bpbar   5640 2009-12-05 15:56 .tomboy.log 
drwx------  2 bpbar bpbar   4096 2009-09-01 08:31 .tsclient 
drwxr-xr-x  2 bpbar bpbar   4096 2009-07-11 10:22 .update-manager-core 
drwx------  2 bpbar bpbar   4096 2009-07-11 11:16 .update-notifier 
drwxr-xr-x  2 bpbar bpbar   4096 2009-11-22 03:00 vid4fuze 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-20 03:31 Videos 
drwxr-xr-x  2 bpbar bpbar   4096 2009-09-07 15:14 .vnc 
drwxr-xr-x  3 bpbar bpbar   4096 2009-08-11 21:39 vorbis 
drwxr-xr-x  2 bpbar bpbar   4096 2009-12-18 08:11 .wapi 
drwxr-xr-x  2 bpbar bpbar   4096 2009-11-21 07:07 Windows Downloads 
drwxr-xr-x  4 bpbar bpbar   4096 2009-12-14 09:31 .wine 
-rw-------  1 bpbar bpbar    641 2009-08-15 17:29 .wvdial.conf 
-rw-------  1 bpbar bpbar    123 2009-12-20 13:07 .Xauthority 
-rw-r--r--  1 bpbar bpbar    163 2009-08-10 15:33 .xscreensaver-getimage.cache 
-rw-r--r--  1 bpbar bpbar   5234 2009-12-20 14:07 .xsession-errors 
bpbar@bpbar-laptop:~$ 
```

Wait, wait, second one down says "root root" instead of "bpbar"  I was looking at the write permissions, not the ownership.  Most of these files or applications I recognize or at least have heard of them.  What's ".."??
Next question of course is how would I change ownership back to myself?  If you have a link or something instead of spoon-feeding me that would be super..


pt, can you post some of the exact commands you're using when getting the error message?  I just tried a couple of gedit commands and did NOT get the error.  I thought they were the same ones as the other day (??!!?)

---

### Post by louieb on 2009-12-20
Ownership look fine - Whatever is causing the error you see - ownership was not it.  

the 2nd down is /home and should be owned by root. The .. is shorthand for parent directory. To see what I mean do a **cd ..**  Some other shorthand directories - a single . (dot) stands for the current directory  and the ~ (tilde) stands for your home directory.

---

### Post by Bartender on 2009-12-21
OK, thanks -
I've gotta get more serious about command line basics.  Start a notebook or something.  Since I don't do anything to retain the knowledge that people such as yourself put in front of me, it goes in one ear and out the other.

---

