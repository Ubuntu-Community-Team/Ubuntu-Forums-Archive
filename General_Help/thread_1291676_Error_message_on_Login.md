---
title: "Error message on Login"
date: 2009-10-15
forum: General Help
---

### Post by jukingeo on 2009-10-15
Hello,

I have a bit of a problem that just appeared last night when signing on.   I have three gui's on my Ubuntu Studio:  Gnome, Xfde, Lxfc (I think...it is the new lightweight desktop).  Anyway, I use Gnome the most.   But as of last night the machine boots up into Lxfc after sign in...even if I select Gnome.   I also get this error message after I log in:

User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users.

I don't remember what I could have done that could have caused this except that I was trying to get Wine to show up in my main "geo" directory without having to constantly click "show hidden files" or constantly use sudo to access it.   Thus it is possible I could have done something wrong here.

Please assist.

Thank You,

Geo

---

### Post by jbrown96 on 2009-10-15
Could you check the permissions of your home folder and post them here? ```
ls -al /home
``` ```
ls -al /home/$USER
```
Most likely trying to change your wine folder had something to do with this. I wouldn't mess with the wine folder; it would be much easier just to make a shortcut to it, then you won't have to worry about it being hidden. You could also just create shortcuts to the program in .wine, but maybe you need access to the folder instead of an app.

---

### Post by jukingeo on 2009-10-15
> **jbrown96 said:**
> Could you check the permissions of your home folder and post them here? ```
ls -al /home
``` ```
ls -al /home/$USER
```
Most likely trying to change your wine folder had something to do with this. I wouldn't mess with the wine folder; it would be much easier just to make a shortcut to it, then you won't have to worry about it being hidden. You could also just create shortcuts to the program in .wine, but maybe you need access to the folder instead of an app.

Hello JBrown,

Sorry I didn't get back to you earlier but...gotta go to work!  Anyway, I did manage to get into Gnome tonight by selecting "Gnome-Failsafe" and I am once again back in.  But I do need to correct the problem because I am still getting that error message.

Moving along, I punched in to the terminal what you asked above and this was the result:

geo@home:~$ ls -al /home
total 32
drwxr-xr-x  5 root root  4096 2008-12-15 21:16 .
drwxrwxrwx 25 root root  4096 2009-10-14 23:26 ..
drwxrwxrwx 74 geo  geo   4096 2009-10-15 22:35 geo
drwx------  2 root root 16384 2008-08-06 23:57 lost+found
drwx------  4 root root  4096 2008-12-15 21:16 .Trash-0
geo@home:~$ ls -al /home/$USER
total 29056
drwxrwxrwx 74 geo  geo      4096 2009-10-15 22:35 .
drwxr-xr-x  5 root root     4096 2008-12-15 21:16 ..
-rwxrwx---  1 geo  geo    822034 2009-09-09 23:09 ABCMovie.flv
drwx------  3 geo  geo      4096 2008-08-07 00:51 .adobe
drwxr-xr-x  8 geo  geo      4096 2008-08-08 12:05 alsatmp
drwxr-xr-x  2 geo  geo      4096 2008-10-02 00:23 .ardour2
drwxr-xr-x  2 geo  geo      4096 2009-09-07 15:42 .audacity1.3-geo
drwxr-xr-x  5 geo  geo      4096 2009-09-07 15:42 .audacity-data
drwxr-xr-x  4 geo  geo      4096 2008-08-07 00:40 Audio
-rw-------  1 geo  geo      8424 2009-10-14 01:07 .bash_history
-rw-r--r--  1 geo  geo       220 2008-08-07 00:23 .bash_logout
-rw-r--r--  1 geo  geo      2940 2008-08-07 00:23 .bashrc
drwx------  2 geo  geo      4096 2009-09-11 23:21 .bcast
drwxr-xr-x  5 geo  geo      4096 2009-09-13 23:20 .blender
drwxr-xr-x  5 geo  geo      4096 2009-09-06 15:25 .cache
drwxr-xr-x  2 geo  geo      4096 2008-11-05 01:13 .cddb
drwx------ 16 geo  geo      4096 2009-09-09 21:50 .config
drwx------  3 root root     4096 2008-10-02 00:12 .dbus
drwxrwxrwx  2 geo  geo      4096 2009-10-01 22:28 Desktop
-rw-------  1 geo  geo        26 2009-10-13 23:03 .dmrc
drwxr-xr-x  3 geo  geo      4096 2008-11-12 21:46 Documents
drwxr-xr-x 11 geo  geo      4096 2009-10-14 23:53 Downloads
-rw-r--r--  1 geo  geo      4860 2009-09-11 00:25 Drive-In Intro.osp
drwxr-xr-x  2 geo  geo      4096 2009-09-04 23:37 .dvdrip
drwxr-xr-x  5 geo  geo      4096 2009-09-10 01:34 dvdrip-data
drwxr-xr-x  4 geo  geo      4096 2009-09-04 23:37 .dvdrip-master
-rw-r--r--  1 geo  geo     25766 2009-09-10 01:06 .dvdriprc
drwxr-xr-x  2 geo  geo      4096 2009-09-09 23:09 dwhelper
drwxr-xr-x  2 geo  geo      4096 2008-10-23 00:14 envy24control
-rw-------  1 geo  geo        16 2008-08-07 00:25 .esd_auth
drwxr-xr-x  7 geo  geo      4096 2008-11-17 21:55 .evolution
drwxr-xr-x  2 geo  geo      4096 2009-09-12 00:33 .fontconfig
drwx------  3 geo  geo      4096 2009-10-01 00:42 .FontForge
drwx------  3 geo  geo      4096 2008-12-01 23:43 .fr-41Ec7i
drwx------  3 geo  geo      4096 2008-12-01 23:44 .fr-6Ni7KW
drwx------  3 geo  geo      4096 2008-12-01 23:44 .fr-c10dqM
drwx------  3 geo  geo      4096 2008-12-01 23:44 .fr-ui2eEf
drwx------  9 geo  geo      4096 2009-10-13 23:58 Games
drwxr-xr-x  2 geo  geo      4096 2008-10-01 22:26 .gamix
drwx------  5 geo  geo      4096 2009-10-15 22:35 .gconf
drwx------  2 geo  geo      4096 2009-10-15 22:40 .gconfd
drwx------  2 geo  geo      4096 2008-10-19 13:03 .gens
drwxr-xr-x 22 geo  geo      4096 2009-09-10 22:19 .gimp-2.4
-rw-r-----  1 geo  geo         0 2009-10-14 23:17 .gksu.lock
drwx------ 12 geo  geo      4096 2009-10-15 00:16 .gnome2
drwx------  2 geo  geo      4096 2008-08-07 00:24 .gnome2_private
drwx------  2 geo  geo      4096 2009-10-14 23:58 .gnupg
-rw-r--r--  1 geo  geo      1461 2008-11-16 15:43 .grip
-rw-r--r--  1 geo  geo        65 2008-11-16 15:43 .grip-mp3encode
-rw-r--r--  1 geo  geo       100 2008-11-05 01:28 .grip-oggenc
drwxr-xr-x  2 geo  geo      4096 2009-09-12 00:33 .gstreamer-0.10
drwx------  2 geo  geo      4096 2008-08-07 00:25 .gvfs
-rw-r--r--  1 geo  geo      2007 2009-09-04 21:43 .hugin
-rw-------  1 geo  geo      4217 2009-10-15 22:35 .ICEauthority
drwxr-xr-x  2 geo  geo      4096 2008-08-07 00:26 .icons
-rw-r--r--  1 geo  geo        64 2008-12-21 21:19 .jackdrc
drwxr-xr-x  3 geo  geo      4096 2009-01-07 01:38 .java
-rw-r--r--  1 geo  geo      3256 2009-10-13 23:20 .joystick
drwx------  3 geo  geo      4096 2008-11-15 14:57 .kde
-rw-r--r--  1 geo  geo     98671 2009-09-12 14:55 .libquicktime_codecs
drwx------  3 geo  geo      4096 2008-08-07 00:41 .local
drwx------  3 geo  geo      4096 2008-08-07 00:51 .macromedia
drwxr-xr-x  3 geo  geo      4096 2008-11-16 15:51 .mcop
-rw-------  1 geo  geo        31 2009-09-10 00:49 .mcoprc
drwxr-xr-x 10 geo  geo      4096 2008-10-19 14:11 .mednafen
drwx------  3 geo  geo      4096 2008-08-07 00:25 .metacity
-rw-r--r--  1 geo  geo       614 2008-10-02 00:41 .mixxxbpmscheme.xml
-rw-r--r--  1 geo  geo      1342 2008-10-02 00:41 .mixxx.cfg
-rw-r--r--  1 geo  geo      9904 2008-10-02 00:41 .mixxxtrack.xml
drwx------  5 geo  geo      4096 2008-08-07 00:51 .mozilla
drwxr-xr-x  2 geo  geo      4096 2008-08-07 01:00 Music
-rw-r--r--  1 geo  geo   9061934 2009-09-12 14:55 MyMovie.mp4
-rw-r--r--  1 root root        1 2008-10-25 16:43 nautilus
drwxr-xr-x  3 geo  geo     16384 2009-10-15 00:16 .nautilus
-rw-r--r--  1 geo  geo       344 2009-09-12 14:55 .openme.prefs
drwx------  3 geo  geo      4096 2009-10-09 23:56 .openoffice.org2
drwx------  2 geo  geo      4096 2008-10-17 01:39 PDF
-rw-r--r--  1 geo  geo       586 2008-08-07 00:23 .profile
drwxr-xr-x  2 geo  geo      4096 2008-08-07 00:27 .pulse
-rw-------  1 geo  geo       256 2008-08-07 00:25 .pulse-cookie
drwxr-xr-x  4 geo  geo      4096 2009-08-21 02:34 qjoypad-4.0.0
drwxr-xr-x  2 geo  geo      4096 2008-11-15 14:57 .qt
-rw-------  1 geo  geo      3556 2009-10-09 23:56 .recently-used
-rw-r--r--  1 geo  geo    448959 2009-10-15 00:17 .recently-used.xbel
drwxr-xr-t  2 geo  geo      4096 2009-02-01 16:04 .retroroids
drwx------  2 geo  geo      4096 2008-08-07 00:25 .ssh
drwxr-xr-x  4 geo  geo      4096 2008-08-07 00:46 .stella
-rw-r--r--  1 geo  geo         0 2008-08-07 00:26 .sudo_as_admin_successful
drwxr-xr-x  7 geo  geo      4096 2008-10-02 00:37 test
-rw-r--r--  1 geo  geo  18706882 2009-09-08 00:11 testb.mp4
-rw-r--r--  1 geo  geo      4310 2009-09-03 23:55 Test.osp
drwxr-xr-x  2 geo  geo      4096 2008-08-07 00:26 .themes
drwxr-xr-x  2 geo  geo      4096 2009-09-11 00:22 thumbnail
drwx------  5 geo  geo      4096 2008-11-19 21:45 .thumbnails
drwxr-xr-x  2 geo  geo      4096 2008-08-21 01:36 .update-manager-core
drwx------  2 geo  geo      4096 2008-11-11 19:32 .update-notifier
drwxr-xr-x  3 geo  geo      4096 2004-08-28 23:47 usbmidi-20040829
-rw-r--r--  1 geo  geo     65160 2004-08-28 23:49 usbmidi-20040829.tar.gz
-rw-r--r--  1 geo  geo         0 2008-12-10 23:21 verify.txt
drwxr-xr-x  2 geo  geo      4096 2008-10-05 19:09 Video Projects
drwxr-xr-x  3 geo  geo      4096 2009-08-24 23:36 .vlc
drwxr-xr-x  6 geo  geo      4096 2008-12-01 22:53 .wahcade
drwxr-xr-x  2 geo  geo      4096 2008-12-15 19:48 .wapi
-rw-r--r--  1 geo  geo         4 2009-09-05 12:38 .windows-label
drwxr-xr-x  5 geo  geo      4096 2009-10-14 23:54 .wine
-rw-------  1 geo  geo       115 2009-10-13 23:03 .Xauthority
-rw-r--r--  1 geo  geo       464 2009-10-14 23:58 .xsession-errors
drwxr-xr-x  2 geo  geo      4096 2009-10-01 00:30 .xtrkcad
drwxr-xr-x  4 geo  geo      4096 2009-10-01 00:27 xtrkcad-4.0.3a.i386
drwxr-xr-x  2 geo  geo      4096 2008-10-19 13:52 .zsnes


Can you tell what went wrong and what I have to do to correct it?

Thanx,

Geo

---

### Post by Johnny B on 2009-10-15
run 
> chmod 644 $Home/.dmrc
to set the correct permissions, however there is probably another problem...

---

### Post by jbrown96 on 2009-10-16
Change the permission of .dmrc ```
chmod 644 ./.dmrc
```

---

### Post by jukingeo on 2009-10-17
Ok, I tried that and now I can't get into Gnome at all.  It goes through a 'boot up' list of items (some of which fail) and then I get a text prompt login.  When I put my login and password in, it isn't accepted.  The same thing happens in recovery mode.

What do I do now?  I can't even get into Ubuntu.  Luckily I have Puppy Linux on this machine as well and I am able to come back here and report what happened.

Does this mean that I have to reinstall Ubuntu?  I sure hope not.

Please get back to me as soon as you can.  I need to get Ubuntu running ASAP because I am setting up a video presentation for Halloween and I can't have Ubuntu down for that much longer.

Thanx,

Geo

---

