---
title: "Can't access folders...???"
date: 2011-04-08
forum: General Help
---

### Post by robertcoulson on 2011-04-08
Hi
I can not access any folders under "places" anymore...Made a shortcut to to get at them, wonder what is going on...See attachment error when I click on any folder...Help
Robert

---

### Post by AmuletOfNight on 2011-04-08
Can you access the folders when your not using the shortcuts?

---

### Post by robertcoulson on 2011-04-08
No, only when I create a shortcut off any of those folders...
Robert

---

### Post by Copper Bezel on 2011-04-08
See [here]("http://ubuntuforums.org/showthread.php?t=1714010"). Common problem - if you open a folder with any application, the dialog that comes up has a checkbox to make that application the default folder handler, and it's checked by default for some reason.

---

### Post by garvinrick4 on 2011-04-08
open a terminal and run this:
```
ls -la
```It will show who has permissions for those folders, maybe not you anymore.
Copy and paste here and will give you instructions include your user name line:
such as:
```
rick@rick-HP:~$ ls -la
total 468
drwxr-xr-x 44 rick rick  4096 2011-04-08 19:49 .
drwxr-xr-x  3 root root  4096 2011-01-11 14:45 ..
drwx------  3 rick rick  4096 2011-01-11 17:49 .adobe
-rw-r--r--  1 rick rick 27247 2011-04-07 00:25 alsa-info.sh
-rw-r--r--  1 rick rick   146 2011-01-26 14:39 .apport-ignore.xml
drwx------  2 rick rick  4096 2011-04-07 01:10 .aptitude
-rw-------  1 rick rick 14832 2011-04-08 19:57 .bash_history
-rw-r--r--  1 rick rick   220 2011-01-11 14:45 .bash_logout
-rw-r--r--  1 rick rick  3353 2011-01-11 14:45 .bashrc
drwx------ 24 rick rick  4096 2011-04-06 11:57 .cache
drwx------  3 rick rick  4096 2011-01-11 15:34 .compiz
drwxr-xr-x 27 rick rick  4096 2011-04-05 12:23 .config
drwx------  3 rick rick  4096 2011-01-11 14:54 .dbus
drwxr-xr-x  2 rick rick  4096 2011-04-08 17:13 Desktop
-rw-r--r--  1 rick rick    91 2011-04-08 19:30 .dmrc
drwxrwxrwx  2 rick rick  4096 2011-04-07 19:02 Documents
drwxr-xr-x  3 rick rick  4096 2011-04-08 17:13 Downloads
drwxr-xr-x  4 rick rick  4096 2011-03-29 20:56 .emerald
-rw-------  1 rick rick    16 2011-01-11 14:54 .esd_auth
-rw-r--r--  1 rick rick   179 2011-01-11 14:45 examples.desktop
drwxr-xr-x  2 rick rick  4096 2011-03-28 18:34 .fontconfig
drwx------  5 rick rick  4096 2011-04-08 19:30 .gconf
drwx------  2 rick rick  4096 2011-04-08 19:58 .gconfd
-rw-r-----  1 rick rick     0 2011-04-07 19:17 .gksu.lock
drwx------ 10 rick rick  4096 2011-04-03 13:56 .gnome2
drwx------  2 rick rick  4096 2011-01-11 15:06 .gnome2_private
drwxr-xr-x  2 rick rick  4096 2011-04-07 20:47 .gstreamer-0.10
-rw-r--r--  1 rick rick   132 2011-04-08 19:30 .gtk-bookmarks
dr-x------  2 rick rick     0 2011-04-08 19:30 .gvfs
-rw-------  1 rick rick 69604 2011-04-08 19:30 .ICEauthority
drwxr-xr-x  3 rick rick  4096 2011-01-12 17:14 .icedtea
drwxr-xr-x  2 rick rick  4096 2011-01-11 15:32 .icons
-rw-r--r--  1 rick rick 42094 2011-01-21 00:43 installedsoftware
drwx------  2 rick rick  4096 2011-04-05 03:14 .kde
drwxr-xr-x  3 rick rick  4096 2011-01-20 00:31 .libreoffice
drwxr-xr-x  3 rick rick  4096 2011-01-11 14:54 .local
drwx------  3 rick rick  4096 2011-01-11 17:49 .macromedia
drwx------  5 rick rick  4096 2011-03-30 09:34 .mozilla
drwxr-xr-x  2 rick rick  4096 2011-04-06 23:43 .mplayer
drwxr-xr-x 17 rick rick  4096 2011-04-05 14:12 Music
drwxr-xr-x  2 rick rick  4096 2011-01-11 14:54 .nautilus
-rw-r--r--  1 rick rick  1441 2011-04-07 01:19 network.txt
drwxr-xr-x  2 rick rick  4096 2011-04-08 14:15 Pictures
drwx------  3 rick rick  4096 2011-01-27 15:20 .pki
-rw-r--r--  1 rick rick    37 2011-01-11 18:37 .printer-groups.xml
-rw-r--r--  1 rick rick   675 2011-01-11 14:45 .profile
drwxr-xr-x  2 rick rick  4096 2011-01-11 14:54 Public
drwx------  2 rick rick  4096 2011-04-08 19:30 .pulse
-rw-------  1 rick rick   256 2011-01-11 14:54 .pulse-cookie
-rw-------  1 rick rick  1597 2011-04-04 13:37 .ripperXrc
drwxr-xr-x  2 rick rick  4096 2011-04-03 22:44 Share
drwxr-xr-x  5 rick rick  4096 2011-01-25 14:18 .shotwell
-rw-r--r--  1 rick rick     0 2011-01-11 14:55 .sudo_as_admin_successful
drwx------  2 rick rick  4096 2011-01-11 17:36 .synaptic
drwxr-xr-x  2 rick rick  4096 2011-01-11 14:54 Templates
-rw-r--r--  1 rick rick   734 2011-03-25 18:03 testdisk.log
drwxr-xr-x  2 rick rick  4096 2011-01-11 15:32 .themes
drwx------  5 rick rick  4096 2011-01-16 23:42 .thumbnails
drwxrwxr-x  2 rick rick  4096 2011-04-05 12:23 Ubuntu One
drwxr-xr-x  2 root root  4096 2011-01-27 09:24 .ure
drwxr-xr-x  2 rick rick  4096 2011-04-05 03:10 Videos
drwxr-xr-x  2 rick rick  4096 2011-04-04 00:39 wallpapers
drwxr-xr-x  2 rick rick  4096 2011-01-18 21:58 .xinput.d
-rw-r--r--  1 rick rick   834 2011-04-06 19:37 .xscreensaver-getimage.cache
-rw-------  1 rick rick 20544 2011-04-08 20:00 .xsession-errors
-rw-------  1 rick rick 46261 2011-04-08 17:24 .xsession-errors.old
rick@rick-HP:~$ 

``` Highlight whole thing after copy and paste and hit # sign in upper right of
Message box and will put in nice box like this to read in.

---

### Post by robertcoulson on 2011-04-09
robert@Robert-aspire-5742:~$ ls -la
total 920
drwxr-xr-x 115 robert robert  12288 2011-04-09 16:27 .
drwxr-xr-x   4 root   root     4096 2011-04-03 21:19 ..
drwx------   2 robert robert   4096 2011-04-08 21:49 .AbiSuite
drwx------   3 robert robert   4096 2010-12-29 19:35 .adobe
drwxr-xr-x   3 robert robert   4096 2011-01-01 16:10 .alice
drwx------   8 robert robert   4096 2011-03-31 16:50 .amsn
drwx------   2 robert robert   4096 2010-12-29 16:28 amsn_received
-rw-r--r--   1 robert robert    657 2011-04-08 20:08 .amSynthControllersrc
-rw-r--r--   1 robert robert 116217 2011-04-08 20:08 .amSynth.presets
-rw-r--r--   1 robert robert   1893 2010-12-29 20:55 .amSynthrc
-rw-r--r--   1 robert robert    263 2011-01-09 16:05 .apertium-tolk.cfg
drwxr-xr-x   2 robert robert   4096 2010-12-30 23:04 .aptoncd
drwxr-xr-x   3 robert robert   4096 2011-01-06 16:44 .ardour2
drwxr-xr-x   3 robert robert   4096 2011-01-17 21:42 .assaultcube_v1.04
-rw-r--r--   1 robert robert    220 2010-12-28 17:22 .bash_logout
-rw-r--r--   1 robert robert   3353 2010-12-28 17:22 .bashrc
drwxr-xr-x   5 robert robert   4096 2010-12-29 17:07 .blender
drwx------   9 robert robert   4096 2011-04-09 16:16 .cache
drwxr-xr-x   3 robert robert   4096 2011-01-21 17:24 .cddb
drwxr-xr-x   2 robert robert   4096 2011-04-03 21:52 .cellwriter
drwxr-xr-x   3 robert robert   4096 2011-01-10 16:12 chrome
drwxr-xr-x   5 robert robert   4096 2011-01-09 16:07 .clamtk
drwx------   3 robert robert   4096 2010-12-28 22:52 .compiz
drwxr-xr-x   2 robert robert   4096 2011-01-10 16:12 components
drwxr-xr-x  37 robert robert   4096 2011-04-07 16:31 .config
-rw-r--r--   1 robert robert    577 2010-12-29 20:31 .convertall
drwx------   2 robert robert   4096 2011-01-18 19:18 .cups
drwxr-xr-x   3 robert robert   4096 2011-04-08 18:35 .cxoffice
drwx------   3 robert robert   4096 2010-12-28 17:26 .dbus
-rw-r--r--   1 robert robert     67 2011-01-10 21:25 .DCOPserver_robert-Aspire-5742__0
lrwxrwxrwx   1 robert robert     46 2011-01-06 17:28 .DCOPserver_robert-Aspire-5742_:0 -> /home/robert/.DCOPserver_robert-Aspire-5742__0
drwxr-xr-x   4 robert robert   4096 2011-04-08 22:03 Desktop
drwxr-xr-x   2 robert robert   4096 2010-12-28 17:26 Documents
drwxr-xr-x   2 robert robert   4096 2011-03-27 20:54 .dooble
drwxr-xr-x   2 robert robert  12288 2011-04-08 22:02 Downloads
drwxr-xr-x   3 robert robert   4096 2011-03-09 21:41 .emacs.d
drwxr-xr-x   4 robert robert   4096 2011-03-11 22:50 .emerald
drwx------   2 robert games    4096 2011-01-02 16:23 .emilia
-rw-------   1 robert robert     16 2010-12-28 17:26 .esd_auth
drwxr-xr-x   2 robert robert   4096 2011-04-05 17:45 .etracer
drwx------   8 robert robert   4096 2011-04-07 09:46 .evolution
-rw-r--r--   1 robert robert    179 2010-12-28 17:22 examples.desktop
drwxr-xr-x   3 robert robert   4096 2011-04-08 19:57 .fltk
drwxr-xr-x   2 robert robert   4096 2011-03-09 15:56 .fontconfig
drwxr-xr-x   2 robert robert   4096 2011-01-31 17:47 .FreeCAD
drwx------   6 robert robert   4096 2011-04-09 16:16 .gconf
drwx------   2 robert robert   4096 2011-04-09 16:22 .gconfd
drwx------   4 robert robert   4096 2010-12-29 17:13 .gegl-0.0
drwxr-xr-x   2 robert robert   4096 2011-03-26 21:07 .gespeaker
drwxr-xr-x  22 robert robert   4096 2011-04-05 21:10 .gimp-2.6
-rw-r-----   1 robert robert      0 2011-04-08 10:47 .gksu.lock
drwxr-xr-x   2 robert robert   4096 2011-01-12 23:40 .gnaural
drwx------  13 robert robert   4096 2011-04-03 20:22 .gnome2
drwx------   2 robert robert   4096 2010-12-28 22:27 .gnome2_private
drwx------   2 robert robert   4096 2011-03-30 20:08 .gnupg
drwxr-xr-x   3 robert robert   4096 2011-04-08 21:38 .gourmet
drwxr-xr-x   7 robert robert   4096 2011-01-13 13:39 .gramps
drwxr-xr-x   2 robert robert   4096 2011-04-08 10:42 .gstreamer-0.10
-rw-r--r--   1 robert robert    142 2011-04-09 16:16 .gtk-bookmarks
dr-x------   2 robert robert      0 2011-04-09 16:16 .gvfs
-rw-------   1 robert robert 104738 2011-04-09 16:16 .ICEauthority
drwxr-xr-x   4 robert robert   4096 2011-04-08 19:27 .icons
-rw-r--r--   1 robert robert   2058 2008-05-16 13:48 install.rdf
-rw-r--r--   1 robert robert     75 2011-01-06 16:43 .jackdrc
drwxr-xr-x   3 robert robert   4096 2011-01-13 13:07 .java
drwx------   4 robert robert   4096 2011-02-24 20:57 .kde
drwx------   3 robert robert   4096 2011-01-13 13:26 .kompozer.net
drwxr-xr-x   3 robert robert   4096 2011-01-04 17:21 .libreoffice
-rw-------   1 robert robert   1284 2011-02-17 17:23 .linphonerc
drwxr-xr-x   3 robert robert   4096 2011-01-19 15:17 .linuxmint
drwxr-xr-x   5 robert robert   4096 2011-01-06 16:48 lmms
-rw-r--r--   1 robert robert    966 2011-01-28 09:51 .lmmsrc.xml
drwxr-xr-x   3 robert robert   4096 2010-12-28 17:26 .local
drwxr-xr-x   3 robert robert   4096 2011-02-24 20:55 .lotus
drwx------   3 robert robert   4096 2010-12-29 19:35 .macromedia
drwx------   4 robert robert   4096 2011-01-09 15:58 Maps
drwxr-xr-x   4 robert robert   4096 2011-03-22 19:31 .miro
drwx------   3 robert robert   4096 2011-01-04 22:18 .mission-control
drwxr-xr-x   2 robert robert   4096 2011-01-14 19:39 .monsterz
drwx------   5 robert robert   4096 2011-02-24 20:56 .mozilla
drwxr-xr-x   2 robert robert   4096 2011-02-20 21:20 .mplayer
drwxr-xr-x   2 robert robert   4096 2010-12-28 17:26 Music
drwxr-xr-x   4 robert robert   4096 2011-03-15 21:31 My GCompris
drwxr-xr-x   2 robert robert   4096 2010-12-28 17:26 .nautilus
drwxr-xr-x   2 robert robert   4096 2011-04-03 21:05 .navit
drwx------   3 robert robert   4096 2010-12-29 21:40 .neverball
-rw-r--r--   1 robert robert    335 2011-04-07 09:13 .nvidia-settings-rc
drwxr-xr-x   2 robert robert   4096 2011-03-24 09:52 .oes
drwxr-xr-x   3 robert robert   4096 2010-12-28 23:26 .openoffice.org
drwxr-x---   6 robert robert   4096 2011-03-04 18:55 .openshot
drwx------   5 robert robert   4096 2011-03-20 00:06 .pam-face-authentication
drwxr-xr-x   3 robert robert   4096 2011-03-15 21:50 .pan2
drwxr-xr-x   2 robert robert   4096 2011-01-27 18:21 .penguinpills
drwxr-xr-x   3 robert robert   4096 2011-02-06 10:18 Pictures
drwx------   3 robert robert   4096 2010-12-28 22:30 .pki
drwxr-xr-x  11 robert robert   4096 2011-01-18 18:28 .PlayOnLinux
drwxr-xr-x   2 robert robert   4096 2011-04-03 21:43 .praat-dir
-rw-r--r--   1 robert robert     37 2010-12-29 22:36 .printer-groups.xml
drwx------   4 robert robert   4096 2011-01-01 11:49 .prism
-rw-r--r--   1 robert robert    675 2010-12-28 17:22 .profile
drwxr-xr-x   2 robert robert   4096 2010-12-28 17:26 Public
drwx------   2 robert robert   4096 2011-04-09 16:16 .pulse
-rw-------   1 robert robert    256 2010-12-28 17:26 .pulse-cookie
drwxr-xr-x   2 robert robert   4096 2010-12-30 23:18 .pykaraoke
drwxr-xr-x   2 robert robert   4096 2011-01-12 17:15 .qt
-rw-------   1 robert robert   4183 2011-04-08 21:55 .recently-used
-rw-------   1 robert robert    218 2011-04-09 16:27 .recently-used.xbel
drwxr-xr-x   7 robert robert   4096 2011-01-06 16:43 Robert
drwxr-xr-x   2 root   root     4096 2011-02-24 20:22 .rpmdb
drwxr-xr-x   3 robert robert   4096 2011-02-19 20:43 .schoolsplay.rc
drwxr-xr-x   5 robert robert   4096 2010-12-29 17:01 .shotwell
drwxr-xr-x   3 robert robert   4096 2011-01-29 22:35 .shutter
drwxr-xr-x   2 robert robert   4096 2011-03-11 22:48 .SimDock
drwx------   3 robert robert   4096 2011-03-19 16:07 .Skype
drwxr-xr-x   7 robert robert   4096 2010-12-30 18:44 .smc
-rw-r--r--   1 robert robert     32 2011-02-20 21:20 .smile.cnf
drwxr-xr-x   3 robert robert   4096 2011-01-09 11:28 .softmaker
drwx------   2 robert robert   4096 2010-12-30 10:27 .ssh
-rw-r--r--   1 robert robert      0 2010-12-28 23:16 .sudo_as_admin_successful
drwx------   3 robert robert   4096 2011-01-26 21:34 .supertux2
drwxr-xr-x   2 robert robert   4096 2010-12-29 21:52 .supertuxkart
drwx------   2 robert robert   4096 2011-01-09 15:58 .tangogps
drwxr-xr-x   2 robert robert   4096 2010-12-28 17:26 Templates
-rw-r--r--   1 robert robert     59 2011-02-20 21:20 .testdep.sh
drwxr-xr-x   3 robert robert   4096 2011-04-08 19:46 .themes
drwx------   5 robert robert   4096 2011-04-08 21:30 .thumbnails
drwx------   2 robert robert   4096 2011-02-20 10:24 .tsclient
drwx------   3 robert robert   4096 2011-04-07 10:58 .twinkle
drwxrwxr-x   2 robert robert   4096 2011-02-12 20:42 Ubuntu One
drwxr-xr-x   2 root   root     4096 2011-01-04 17:13 .ure
drwxr-xr-x   3 robert robert   4096 2010-12-29 20:58 Videos
drwxr-xr-x   3 robert robert   4096 2011-04-08 13:31 .VirtualBox
drwxr-xr-x   4 robert robert   4096 2011-04-08 12:59 VirtualBox VMs
drwxr-xr-x   3 robert robert   4096 2011-01-01 11:48 .webapps
drwxr-xr-x   4 robert robert   4096 2011-01-02 20:21 .wine
drwxr-xr-x   2 robert robert   4096 2011-02-20 21:03 .wireshark
drwxr-xr-x   2 robert robert   4096 2011-01-10 16:51 .xaralx
drwxr-xr-x   2 robert robert   4096 2011-01-06 18:52 .XaraLXFilters
drwxr-xr-x   2 robert robert   4096 2011-04-08 18:24 .xine
drwxr-xr-x   2 robert robert   4096 2011-02-21 19:27 .xinput.d
-rw-r--r--   1 robert robert    774 2011-01-11 19:28 .xscreensaver-getimage.cache
-rw-------   1 robert robert  11392 2011-04-09 16:27 .xsession-errors
-rw-------   1 robert robert 113627 2011-04-09 11:07 .xsession-errors.old
drwxr-xr-x   4 robert robert   4096 2011-03-26 18:16 .xVideoServiceThief
drwxr-xr-x   2 robert robert   4096 2011-03-26 18:00 xVideoServiceThief_downloads
-rw-r--r--   1 robert robert   2351 2011-04-08 19:58 .zynaddsubfxXML.cfg
robert@Robert-aspire-5742:~$ 
```

```

---

### Post by robertcoulson on 2011-04-09
I figured it out...See attachment....Maybe I am not as stupid as I thought (ha,ha)...Thanks for all your help guys.
Robert

---

### Post by garvinrick4 on 2011-04-09
Very good I am glad you figured it out.

---

### Post by robertcoulson on 2011-04-09
Hi garvinrick4...As you can see, I have all access to ALL my folders again...THANKS
Robert

---

### Post by robertcoulson on 2011-04-09
One question...What and where is Nautilus....???...I here it mentioned sometimes.
Robert

---

### Post by garvinrick4 on 2011-04-09
> **robertcoulson said:**
> One question...What and where is Nautilus....???...I here it mentioned sometimes.
Robert Nautilus is your file browser type in terminal:
```
nautilus
```
##There is a ubuntu pocket guide in .pdf format that is a free download in
my signature is a handy little reference quide, explains a lot about the file system.

---

### Post by garvinrick4 on 2011-04-09
When you make a long post like when I asked you to post the ls -la command in a terminal if
you highlight it all after you have pasted to your message box and hit the # sign in upper right
 of your Message box it will put it a nice little box that scrowls and not take up a lot of space. They are called code tags.

---

### Post by robertcoulson on 2011-04-09
Sorry about that garvinrick4...I hit the # sign at the wrong sequence..Sorry.
Robert

---

### Post by robertcoulson on 2011-04-09
Hey garvinrick4, isn't typing "nautilus" in the terminal the same as clicking on my "Home" folder...???...It brings up the same folders....
Robert

---

### Post by garvinrick4 on 2011-04-09
> **robertcoulson said:**
> Hey garvinrick4, isn't typing "nautilus" in the terminal the same as clicking on my "Home" folder...???...It brings up the same folders....
Robert
That box that opens is nautilus you can.
```
nautilus /etc/apt
```or any (directory) you wish.

To open a file.
```
gedit /etc/apt/sources.list
```to open a file in root as to make changes and be able to save.
```
gksudo gedit /etc/apt/sources.list
```#gedit being the text editor can be changed to any text editor you prefer.

* And yes you can open the nautilus file system by GUI or from terminal. Gets you to the same place.
To make changes in permissions and other it is best done from terminal so nice to learn.*

---

### Post by robertcoulson on 2011-04-09
10/4....Understood
Robert

---

