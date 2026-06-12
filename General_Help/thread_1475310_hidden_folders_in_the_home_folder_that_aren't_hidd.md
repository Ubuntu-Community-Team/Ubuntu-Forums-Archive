---
title: "hidden folders in the home folder that aren't hidden."
date: 2010-05-06
forum: General Help
---

### Post by krupintupple on 2010-05-06
just a general weirdness, but some folders that are in my /home folder don't show up. if i check "show hidden folders", they still don't show up. for all terms and purposes, they are simply not there. however, if i search for them through the search tool, or beagle, they show up as being in my /home folder.

so, anyone have any idea how this happened, or how i can remedy this?

---

### Post by mikewhatever on 2010-05-06
Example?

---

### Post by krupintupple on 2010-05-06
> **mikewhatever said:**
> Example?

i simply can't find the folders, no matter which preferences i check/de-select in the /home folder. i need to literally search for them, at which point, the search tool tells me they're actually in the /home folder. i can click on them via the search function and they work, but it's annoying to get to my ebooks or pictures via the search tool. 

for whatever reason, they are simply not displaying in the /home folder.

---

### Post by mikewhatever on 2010-05-06
What's the output of **ls -la ~**? Can you specify a hidden folder that you can't find.

---

### Post by krupintupple on 2010-05-06
this is the exact output of that command:

> 
danno2@android-desktop:~$ ls -la ~
ls: cannot access /home/danno2/.netx: Permission denied
ls: cannot access /home/danno2/.pcsx: Permission denied
ls: cannot access /home/danno2/.scim: Permission denied
ls: cannot access /home/danno2/.clamtk: Permission denied
ls: cannot access /home/danno2/.gtkhackrc: Permission denied
total 1058
drwxr-xr-x         77 danno2     danno2             2888 2010-05-06 21:03 .
drwxr-xr-x          7 root       root                152 2010-04-02 14:51 ..
drwx------          3 danno2     danno2               80 2009-05-09 18:40 .adobe
drwxr-xr-x          4 danno2     danno2               96 2009-05-23 01:54 .alien-arena
drwxr-xr-x          2 danno2     danno2               72 2009-05-23 02:35 .amph
-rw-r--r--          1 danno2     danno2              122 2009-10-31 17:51 .apport-ignore.xml
drwxrwxrwx         13 danno2     danno2             1280 2010-04-28 16:48 .azureus
-rwxrwxrwx          1 danno2     danno2            15851 2010-05-06 20:32 .bash_history
-rwxrwxrwx          1 danno2     danno2              220 2009-05-05 13:26 .bash_logout
-rwxrwxrwx          1 danno2     danno2             3115 2009-05-05 13:26 .bashrc
drwx------          7 danno2     danno2              232 2010-05-06 21:43 .beagle
drwx------         19 danno2     danno2              728 2010-05-06 20:23 .cache
??????????          ? ?          ?                     ?                ? .clamtk
drwxrwxrwx          3 danno2     danno2               72 2009-05-05 14:27 .compiz
drwxrwxrwx         28 danno2     danno2              896 2010-04-28 03:32 .config
drwxrwxrwx          3 danno2     danno2               80 2009-05-05 13:28 .dbus
drwxrwxrwx          3 danno2     danno2              104 2010-05-06 04:42 Desktop
-rw-r--r--          1 danno2     danno2               58 2010-05-06 21:03 .dmrc
drwxr-xr-x          5 danno2     danno2              280 2010-03-02 22:22 .elc
-rwxrwxrwx          1 danno2     danno2               16 2009-05-05 13:28 .esd_auth
drwx------          8 danno2     danno2              312 2009-11-14 04:58 .evolution
drwxr-xr-x          4 danno2     danno2              104 2009-06-09 00:06 .fltk
drwxrwxrwx          2 danno2     danno2             2096 2010-05-01 03:35 .fontconfig
drwx------          2 danno2     danno2              248 2010-05-06 21:01 .freedroid_rpg
drwxr-xr-x          7 danno2     danno2              176 2010-02-14 14:37 FrostWire
drwxr-xr-x          8 danno2     danno2              896 2010-04-28 16:09 .frostwire4.18
drwxrwxrwx          6 danno2     danno2              144 2010-05-06 21:03 .gconf
drwxrwxrwx          2 danno2     danno2               80 2010-05-06 23:27 .gconfd
drwxrwxrwx          4 danno2     danno2               96 2009-05-05 13:50 .gegl-0.0
drwxrwxrwx         22 danno2     danno2              920 2010-04-15 13:51 .gimp-2.6
-rwxrwxrwx          1 danno2     danno2                0 2010-05-06 21:01 .gksu.lock
drwxr-xr-x          3 danno2     danno2              320 2009-05-23 02:01 .glest
drwxr-xr-x          3 danno2     danno2               80 2009-08-23 12:11 .gnome
drwxrwxrwx         13 danno2     danno2              520 2010-05-06 21:02 .gnome2
drwxrwxrwx          2 danno2     danno2               48 2009-05-05 13:28 .gnome2_private
drwxr-xr-x          5 danno2     danno2              224 2009-06-19 01:45 .gnunet
drwxrwxrwx          2 danno2     danno2              168 2010-05-06 21:01 .gnupg
drwxr-xr-x          3 danno2     danno2               72 2009-05-07 00:10 .google
drwxrwxrwx          2 danno2     danno2               88 2010-05-06 23:25 .gstreamer-0.10
-rwxrwxrwx          1 danno2     danno2              156 2010-04-26 04:41 .gtk-bookmarks
??????????          ? ?          ?                     ?                ? .gtkhackrc
drwxr-xr-x          2 danno2     danno2               80 2010-03-07 13:17 .gunroar
dr-x------          2 danno2     danno2                0 2010-05-06 21:03 .gvfs
drwx------          3 danno2     danno2              208 2009-05-17 16:26 .gxmame
-rw-------          1 danno2     danno2            99632 2010-05-06 21:03 .ICEauthority
drwx------          3 danno2     danno2              232 2010-04-18 15:19 .icedteaplugin
drwxrwxrwx          2 danno2     danno2               48 2009-05-05 14:31 .icons
drwxr-xr-x          4 danno2     danno2              112 2010-01-13 01:58 .java
-rwxrwxrwx          1       1000       1000        27423 2010-01-18 04:03 journal.odt
drwx------          3 danno2     danno2              192 2009-05-07 02:40 .kde
drwxr-xr-x          2 danno2     danno2               80 2009-05-23 02:39 .kq
drwx------          3 danno2     danno2              208 2009-05-17 13:32 .kxmame
drwxrwxrwx          3 danno2     danno2               72 2009-05-05 13:31 .local
drwxrwxrwx          5 danno2     danno2              120 2009-09-07 15:42 danno
drwx------          3 danno2     danno2               80 2009-05-09 18:40 .macromedia
-rw-r--r--          1 danno2     danno2           587813 2009-05-17 00:10 .meritous.sav
drwxrwxrwx          6 danno2     danno2              216 2010-02-04 02:32 .mozilla
drwxr-xr-x          2 danno2     danno2              176 2009-09-11 02:09 .mplayer
-rw-------          1 root       root                  9 2010-05-06 20:23 .nano_history
drwxrwxrwx          3 danno2     danno2               80 2009-05-05 13:28 .nautilus
??????????          ? ?          ?                     ?                ? .netx
-rwxrwxrwx          1 danno2     danno2             1029 2010-05-06 20:11 .nvidia-settings-rc
drwxrwxrwx          3 danno2     danno2               72 2009-05-05 13:31 .openoffice.org
drwx------         14 danno2     danno2             1288 2010-04-19 03:24 .opera
??????????          ? ?          ?                     ?                ? .pcsx
c--xrw-r-x 1634296937 1970473587 1629515620 1390, 493417 2025-11-21 09:17 .prboom
-rwxrwxrwx          1 danno2     danno2              675 2009-05-05 13:26 .profile
drwx------          2 danno2     danno2              808 2010-05-06 21:03 .pulse
-rwxrwxrwx          1 danno2     danno2              256 2009-05-05 13:28 .pulse-cookie
drwx------          4 danno2     danno2              232 2010-03-13 13:14 .purple
drwxr-xr-x          2 danno2     danno2              152 2009-05-07 14:34 .pyNeighborhood
drwxr-xr-x          2 danno2     danno2              120 2010-04-28 15:12 .qt
-rwxrwxrwx          1 danno2     danno2           147853 2010-04-19 20:07 .recently-used
-rw-------          1 danno2     danno2              923 2010-05-06 20:35 .recently-used.xbel
-rw-r--r--          1 danno2     danno2            49762 2009-06-26 02:55 .recently-used.xbel.S5OZVU
-rw-r--r--          1 danno2     danno2            49762 2009-06-26 02:55 .recently-used.xbel.YGKGWU
drwxr-xr-x          3 danno2     danno2              104 2010-02-02 23:00 .ripoff
??????????          ? ?          ?                     ?                ? .scim
drwxrwxrwx          7 danno2     danno2              184 2010-02-04 23:12 share
drwx------          3 danno2     danno2              144 2010-04-21 11:16 .Skype
drwxrwxrwx          2 danno2     danno2               48 2009-05-05 14:50 .ssh
drwxrwxrwx         10 danno2     danno2              288 2010-03-02 20:53 stuff
-rwxrwxrwx          1 danno2     danno2                0 2009-05-05 14:37 .sudo_as_admin_successful
drwxrwxrwx          2 danno2     danno2               48 2009-05-05 14:31 .themes
drwxrwxrwx          5 danno2     danno2              120 2009-11-10 00:03 .thumbnails
drwxrwxrwx          7 danno2     danno2            12672 2009-10-31 03:00 .tomboy
drwxrwxrwx          7 danno2     danno2              168 2010-03-28 18:12 trent
drwxrwxr-x          5 danno2     danno2              200 2010-04-18 08:22 Ubuntu One
drwxr-xr-x          2 danno2     danno2              336 2010-02-17 17:07 .umit
drwxrwxrwx          2 danno2     danno2               80 2009-05-05 15:42 .update-manager-core
drwxrwxrwx          2 danno2     danno2               80 2009-09-11 01:56 .update-notifier
drwxrwxrwx          2 danno2     danno2               48 2010-04-28 02:10 .wapi
drwxr-xr-x          4 danno2     danno2              232 2010-02-03 01:07 .wine
drwxr-xr-x          2 danno2     danno2              184 2009-09-12 03:33 .winff
-rw-------          1 danno2     danno2                0 2010-05-06 20:32 .Xauthority
drwxr-xr-x          2 danno2     danno2              104 2010-04-28 15:12 .xine
drwxr-xr-x          2 danno2     danno2               72 2009-10-31 03:05 .xinput.d
drwxr-xr-x         10 danno2     danno2              240 2009-05-17 13:27 .xmame
-rwxrwxrwx          1 danno2     danno2              573 2009-11-10 00:02 .xscreensaver-getimage.cache
-rw-------          1 danno2     danno2             5351 2010-05-06 23:28 .xsession-errors
-rw-------          1 danno2     danno2             7896 2010-05-06 21:02 .xsession-errors.old
drwxr-xr-x          2 danno2     danno2              336 2010-02-14 15:51 .zsnes


and no, there is nothing that is physically missing or gone. it's just not showing where it should be. i wish i could explain it better, but my /home is mostly empty. i can find all of my folders via searching - which tells me that they're actually in /home - but they're not, and neither are they hiding, as i've checked that.

update: just tried to create a new folder on the desktop and it spat out the following:

> There was an error creating the directory in /home/danno2/Desktop.

---

### Post by mikewhatever on 2010-05-07
Well, according to the output, there should be several not hidden folders there - Desktop, Frostwire, dano, trent, Ubuntu one, share. I may have missed a few, but the question is, which one of these, if any, is not visible?

---

### Post by krupintupple on 2010-05-07
danno, share and frostwire are visible, the rest are not.

so, this is even stranger now...i can't delete a folder i just made on my desktop. i was going to try to make a 'new' folder with the same name as the old, and then drag it into /home to see what would happen. it said it wouldn't overwrite, so i tried to delete it. it said it was read-only. 

i then tried to delete it via sudo, but was declined. so i logged in as root, and was still told it was read-only and i was denied. so...at this point, i'm wondering just what the heck is going on?

i'm going to make a new user profile, to see if the problems are localized just to danno2 or if there's a weird, larger issue going on with the system.

update: so, i was checking around "users and groups" under 'administration' and discovered that "danno2" was a limited account, or something to that effect. i changed it back and now i can make bookmarks in firefox, delete folders on my desktop, and all of the other lovely things i could before. however, the /home folder is still mostly empty.

even if i switch on "show hidden folders" i still only see the three and nothing else...there should at least be piles of config files and other .this and .that files, shouldn't there?

---

### Post by mikewhatever on 2010-05-07
Odd indeed. What about the new profile? Does it have the same issue?

---

### Post by krupintupple on 2010-05-08
hmm...

disappointingly, after a reboot and an attempt to make "danno3" there is no change - and startlingly, no ability to actually make "danno3" - as it tells me that "...useradd: cannot create directory /home/danno3"

so, i'm going to try to coax it into giving me my system back without messing with the permissions and see how that goes. just an FYI, i can't bookmark in opera and firefox isn't even starting up. methinks that during the update, the permissions were wonked. i'm honestly stumped with this one ...

---

### Post by mikewhatever on 2010-05-08
You can check what's wrong with opera's permissions with *ls -ls ~/.opera*, as for firefox, try starting it from a terminal windows, you might get some useful output this way.

---

### Post by efflandt on 2010-05-08
Something hammered permissions on your home directory.  Who or what gave those directories and files 777 permission (drwxrwxrwx or -rwxrwxrwx)?  That is totally insecure.

They should be more like this:
```

total 508
drwxr-xr-x 56 efflandt efflandt  4096 2010-05-08 05:33 .
drwxr-xr-x  3 root     root      4096 2009-11-08 18:34 ..
drwx------  3 efflandt efflandt  4096 2009-11-08 19:57 .adobe
drwx------  2 efflandt efflandt  4096 2010-02-07 09:30 .aptitude
-rw-------  1 efflandt efflandt  7120 2010-05-08 05:19 .bash_history
-rw-r--r--  1 efflandt efflandt   220 2009-11-08 18:34 .bash_logout
-rw-r--r--  1 efflandt efflandt  3180 2009-11-08 18:34 .bashrc
drwxr-xr-x  2 efflandt efflandt  4096 2010-05-04 12:32 bin
drwx------  7 efflandt efflandt  4096 2010-01-08 02:29 .cache
drwx------  3 efflandt efflandt  4096 2009-11-08 19:09 .compiz
drwxr-xr-x 14 efflandt efflandt  4096 2010-04-18 20:08 .config
drwx------  3 efflandt efflandt  4096 2009-11-08 18:44 .dbus
drwxr-xr-x  2 efflandt efflandt  4096 2010-02-07 09:30 .debtags
drwxr-xr-x  2 efflandt efflandt  4096 2010-04-04 22:38 Desktop
-rw-r--r--  1 efflandt efflandt    42 2010-05-08 04:56 .dmrc
drwxr-xr-x  2 efflandt efflandt  4096 2010-05-08 05:33 Documents
drwxr-xr-x  9 efflandt efflandt  4096 2010-05-06 18:34 Downloads
drwxr-xr-x  8 efflandt efflandt  4096 2010-02-06 17:03 .dvdcss
-rw-------  1 efflandt efflandt    16 2009-11-08 18:44 .esd_auth
drwxr-xr-x  3 efflandt efflandt  4096 2009-11-23 02:51 .evolution
-rw-r--r--  1 efflandt efflandt   167 2009-11-08 18:34 examples.desktop
drwxr-xr-x  2 efflandt efflandt  4096 2010-02-28 09:56 .fontconfig
drwx------  4 efflandt efflandt  4096 2010-05-08 04:56 .gconf
drwx------  2 efflandt efflandt  4096 2010-05-08 05:32 .gconfd
drwx------  4 efflandt efflandt  4096 2009-11-19 02:26 .gegl-0.0
drwxr-xr-x 22 efflandt efflandt  4096 2010-02-21 21:00 .gimp-2.6
-rw-r-----  1 efflandt efflandt     0 2010-05-08 04:24 .gksu.lock
drwx------ 12 efflandt efflandt  4096 2010-05-08 04:52 .gnome2
drwx------  2 efflandt efflandt  4096 2009-11-08 18:44 .gnome2_private
drwx------  3 efflandt efflandt  4096 2010-05-08 04:56 .gnupg
drwxr-xr-x  2 efflandt efflandt  4096 2009-12-28 03:40 .gpilotd
-rw-r--r--  1 efflandt efflandt     4 2009-12-28 03:40 .gpilotd.pid
drwxr-xr-x  2 efflandt efflandt  4096 2009-12-12 18:37 .gpsman-dir
drwxr-xr-x  2 efflandt efflandt  4096 2010-04-28 17:48 .gstreamer-0.10
-rw-r--r--  1 efflandt efflandt   320 2010-05-08 04:56 .gtk-bookmarks
dr-x------  2 efflandt efflandt     0 2010-05-08 04:56 .gvfs
drwxr-----  2 efflandt efflandt  4096 2009-11-08 19:26 .hplip
-rw-r--r--  1 efflandt efflandt   530 2010-03-13 01:59 .huludesktop
-rw-r--r--  1 efflandt efflandt   529 2010-01-15 06:21 .huludesktop~
-rw-------  1 efflandt efflandt 35136 2010-05-08 04:56 .ICEauthority
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 19:47 .icons
drwxr-xr-x  3 efflandt efflandt  4096 2010-01-24 17:18 .java
drwx------  3 efflandt efflandt  4096 2009-12-18 23:23 .kde
-rw-------  1 efflandt efflandt    70 2009-12-29 12:02 .lesshst
drwx------  3 efflandt efflandt  4096 2009-11-08 18:50 .local
drwx------  2 efflandt efflandt  4096 2010-01-24 17:19 .logmein
drwx------  3 efflandt efflandt  4096 2009-11-08 19:57 .macromedia
drwx------  3 efflandt efflandt  4096 2010-01-08 02:27 .mission-control
drwxr-xr-x  5 efflandt efflandt  4096 2009-11-29 17:43 .mozilla
drwxr-xr-x  3 efflandt efflandt  4096 2009-11-08 19:43 Music
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 18:44 .nautilus
drwxr-xr-x  3 efflandt efflandt  4096 2009-11-09 02:16 .openoffice.org
drwx------  2 efflandt efflandt  4096 2009-12-28 03:45 palm1de
drwx------  2 efflandt efflandt  4096 2010-05-06 19:07 PDF
drwxr-xr-x  3 efflandt efflandt  4096 2010-02-21 20:59 Pictures
drwxr-xr-x  6 efflandt efflandt  4096 2009-11-08 18:56 ppd_files
-rw-r--r--  1 efflandt efflandt    37 2009-11-08 19:26 .printer-groups.xml
-rw-r--r--  1 efflandt efflandt   675 2009-11-08 18:34 .profile
drwxr-xr-x  2 efflandt efflandt  4096 2009-12-12 03:59 Public
drwx------  2 efflandt efflandt  4096 2010-05-08 04:16 .pulse
-rw-------  1 efflandt efflandt   256 2009-11-08 18:44 .pulse-cookie
-rw-------  1 efflandt efflandt  1814 2010-05-06 20:15 .recently-used
-rw-------  1 efflandt efflandt 34714 2010-05-08 04:52 .recently-used.xbel
-rw-r--r--  1 efflandt efflandt 53248 2009-11-29 04:54 .recently-used.xbel.1QF23U
-rw-r--r--  1 efflandt efflandt 52184 2009-11-28 00:23 .recently-used.xbel.VXUK4U
drwx------  2 efflandt efflandt  4096 2009-11-08 18:57 .ssh
-rw-r--r--  1 efflandt efflandt     0 2009-11-08 18:59 .sudo_as_admin_successful
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 18:44 Templates
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 19:47 .themes
drwx------  5 efflandt efflandt  4096 2009-11-19 02:24 .thumbnails
drwxr-xr-x  2 efflandt efflandt  4096 2010-05-08 05:32 Tmp
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 18:45 .update-manager-core
drwx------  2 efflandt efflandt  4096 2009-11-08 18:44 .update-notifier
-rw-r--r--  1 efflandt efflandt 22305 2009-12-19 15:08 .usbcreator.log
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-08 18:44 Videos
drwxr-xr-x  2 efflandt efflandt  4096 2009-12-16 07:57 .virt-manager
drwxr-xr-x  2 efflandt efflandt  4096 2009-11-19 02:26 .wapi
-rw-------  1 efflandt efflandt     0 2009-11-29 04:54 .Xauthority
drwxr-xr-x  2 efflandt efflandt  4096 2009-12-18 23:25 .xine
-rw-------  1 efflandt efflandt  5336 2010-05-08 05:32 .xsession-errors
-rw-------  1 efflandt efflandt  5324 2010-05-08 04:52 .xsession-errors.old
```

---

### Post by krupintupple on 2010-05-08
i'll get back to you on both of those when i'm @ home, but an early test this morning seemed to show that the entire system was read-only. i even logged in as root and it denied me access and told me that "read only file-system" - so i'm thinking there may be some serious damage or issues with my install? this is so weird, i've no idea why this would be happening.

---

### Post by Spr0k3t on 2010-05-08
I'm wondering if the user owns the /home/{user} directory or if it's part of a different user/group association.  The permission denied tells me the owner might be different.  Just a thought, I could be wrong though.

---

### Post by QLee on 2010-05-08
[QUOTE=krupintupple]hmm...

disappointingly, after a reboot and an attempt to make "danno3" there is no change - and startlingly, no ability to actually make "danno3" - as it tells me that "...useradd: cannot create directory /home/danno3"

so, i'm going to try to coax it into giving me my system back without messing with the permissions and see how that goes. just an FYI, i can't bookmark in opera and firefox isn't even starting up. methinks that during the update, the permissions were wonked. i'm honestly stumped with this one ...[/QUOTE]

krupintupple, tell us which guide or suggestion in a post you followed to get to the point that you have non-standard permissions in your ~home folder (and possibly) on the /home folder itself, it might take a reversal of what you did to try and solve some other problem (and it probably was not the correct solution). No amount of rebooting will change the permissions you have set and the system did not change them on it's own.

Give a little more detail with your answers, tell step-by-step what you are trying and not just your interpretation of the error.

Did you try to add a user as root (if you don't understand that please ask)?

---

### Post by dino99 on 2010-05-08
> **krupintupple said:**
> i'll get back to you on both of those when i'm @ home, but an early test this morning seemed to show that the entire system was read-only. i even logged in as root and it denied me access and told me that "read only file-system" - so i'm thinking there may be some serious damage or issues with my install? this is so weird, i've no idea why this would be happening.

this kind of mess cant be smootly fixed, never change the rights into unix, you will break everything. Better to make a clean install now.

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by krupintupple on 2010-05-08
ok, so i'm back home and everything is working perfectly, at least as far as my concerns: my machine is no longer in "read only" mode, and my home folder has been repopulated fully.

@QLee - this is mostly my own fault, i believe. i leapt into the beta for 10.04 and it completely screwed my system, and i had to rely on a scratch-built kernel. things were going fine and well, and then when the actual release date hit, another update came down the pike that apparently did something that my machine didn't really like. or, and i think this is more likely, it was some time at 5 am when i was frantically attempting to get my computer back to life that i'd probably done something stupid. although, i don't specifically recall messing with the permissions. maybe i'll recheck them, since the "fix" but i'd doubt it'd have any effect.

which brings me to my other point. i snooped around the forums and realised that sometimes when the file-tree of a reiserfs system is b0rked - potentially due to an ambitious plan to get into beta - it sometimes locks the file system in read only mode. i booted into repair mode and ran a fsck on my /dev/sdb4 and it found 11 errors that were serious enough to worry my system, but apparently not serious enough to ruin anything else. with these cleaned up, i logged back in and my home folder has been "repopulated", so to speak and i've full access to the rest of my system.

unless someone with more insight into what may have happened would like to correct me, i think i've learned my lesson about ambitiously leaping into beta testing and kernel compiling for now.

i'll leave this here for a while before i check it as [Solved], just in case. i'd hate to jump the gun.

---

### Post by QLee on 2010-05-08
krupintupple, I suggest moving to another file system, I'm not sure if reiserfs is still maintained after Reiser was convicted of murdering his wife. I still have some Debian(Lenny) installs that have some reiser partitions and they still work but I think you'd be well advised to consider alternatives, especially with modern kernels and distros.

Edit:I found this which explains why SUSE dropped reiser, you might want to read it. 
[http://article.gmane.org/gmane.linux.suse.opensuse.devel/4312](http://article.gmane.org/gmane.linux.suse.opensuse.devel/4312)

---

### Post by krupintupple on 2010-05-08
yeah, i'd nearly forgotten what i actually had under the hood until now. i migrated over from archlinux like 3 years ago and haven't looked back since. amazingly, ubuntu has always "just worked" for me, so my knowledge really atrophied, but also, there were a lot of little settings here and there that i wasn't aware of, or just kind of put out of mind.

both home and root are reiserfs, so methinks i'll get myself to an ext3 or ext4 as soon as possible. the only thing stopping me is the pain of a reinstall - from what i do recall about linux, you can't just "change file-systems" with a mouse click...although i would like to be proven wrong on this count! :)

---

### Post by QLee on 2010-05-09
[QUOTE=krupintupple]
both home and root are reiserfs, so methinks i'll get myself to an ext3 or ext4 as soon as possible. the only thing stopping me is the pain of a reinstall - from what i do recall about linux, you can't just "change file-systems" with a mouse click...although i would like to be proven wrong on this count! :)[/QUOTE]

Mouse click??? Did I stumble into a forum for some other operating system??? Real sys admins don't use no mouse. <chuckle>

If you have the space to carve a new partition out of what's there you could do that, format as you choose and then rsync the files to the new partition, change your fstab and deal with any pips and squeeks that occur when you reboot. Of course, you might choose to do it all with your "backups", eh?

---

