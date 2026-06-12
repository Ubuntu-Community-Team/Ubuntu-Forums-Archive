---
title: "Hidden files in home folder"
date: 2011-09-26
forum: General Help
---

### Post by bala150985 on 2011-09-26
Of late I am seeing lots of file which begin with a "dot", I know some of these files were created because of my actions like .ssh, .vnc, .bashrc, .bash_history, .evolutions. 

I have highlighted certain files which I cannot really associate with my actions,  Is there any way to find out why these files were created here for ? 

bala@bala-laptop:~$ ls -lah
total 419M
drwxr-xr-x 70 bala bala 4.0K 2011-09-26 10:43 .
drwxr-xr-x  5 root root 4.0K 2011-09-10 23:01 ..
-rw-r--r--  1 bala bala 199M 2011-09-17 13:50 1.flv
drwx------  3 bala bala 4.0K 2010-08-08 17:02 .adobe
drwx------  2 bala bala 4.0K 2010-11-07 11:55 .aptitude
-rw-------  1 bala bala  36K 2011-09-25 21:26 .bash_history
-rw-r--r--  1 bala bala  220 2010-08-08 15:54 .bash_logout
-rw-r--r--  1 bala bala 3.1K 2010-08-08 15:54 .bashrc
drwx------  2 bala bala 4.0K 2011-09-11 17:43 .bogofilter
**drwx------ 18 bala bala 4.0K 2011-09-26 09:29 .cache**
[B]drwx------  2 bala bala 4.0K 2011-09-14 09:12 .camel_certs
drwx------  3 bala bala 4.0K 2010-08-08 16:08 .compiz
drwxr-xr-x 22 bala bala 4.0K 2011-09-17 11:07 .config
drwx------  3 bala bala 4.0K 2010-08-08 16:01 .dbus
drwxr-xr-x  2 bala bala 4.0K 2010-08-10 20:33 .debtags
-rw-r--r--  1 bala bala   36 2011-09-26 09:29 .dmrc
drwxr-xr-x  2 bala bala 4.0K 2010-08-12 18:15 .dwa_store
-rw-------  1 bala bala   16 2010-08-08 16:01 .esd_auth
[/B]drwxr-xr-x  8 bala bala 4.0K 2011-09-25 12:25 .evolution
[B]-rw-r--r--  1 bala bala  39K 2011-02-10 21:31 .face
drwxr-xr-x  2 bala bala 4.0K 2011-07-16 14:55 .fontconfig
-rw-r--r--  1 bala bala   63 2011-05-21 11:57 .gammurc
drwx------  5 bala bala 4.0K 2011-09-26 09:29 .gconf
drwx------  2 bala bala 4.0K 2011-09-26 10:43 .gconfd
drwx------  6 bala bala 4.0K 2011-01-09 19:16 .gdesklets
-rw-r-----  1 bala bala    0 2011-09-23 10:28 .gksu.lock
drwx------ 12 bala bala 4.0K 2011-09-25 21:26 .gnome2
drwx------  2 bala bala 4.0K 2010-08-08 16:02 .gnome2_private
[/B]drwxr-xr-x  2 bala bala 4.0K 2010-08-25 10:03 .gns3
[B]drwxr-xr-x  2 bala bala 4.0K 2011-09-25 15:12 .gstreamer-0.10
-rw-r--r--  1 bala bala  132 2011-09-26 09:29 .gtk-bookmarks
[/B]-rw-r--r--  1 bala bala  944 2011-09-17 21:53 .gtk-recordmydesktop
[B]dr-x------  2 bala bala    0 2011-09-26 09:29 .gvfs
-rw-------  1 bala bala 116K 2011-09-26 09:29 .ICEauthority
drwxr-xr-x  2 bala bala 4.0K 2010-08-08 16:02 .icons
[/B]drwxr-xr-x  4 bala bala 4.0K 2011-04-14 06:36 .java
[B]drwxr-xr-x  2 bala bala 4.0K 2011-05-22 10:38 .kchmviewer
drwx------  3 bala bala 4.0K 2010-09-26 18:02 .kde
-rw-------  1 bala bala   46 2011-01-09 19:23 .lesshst
drwx------  3 bala bala 4.0K 2010-08-08 16:12 .local
drwx------  3 bala bala 4.0K 2010-08-08 17:03 .macromedia
drwx------  3 bala bala 4.0K 2010-08-10 18:51 .mission-control
[/B]drwx------  5 bala bala 4.0K 2011-09-25 15:11 .mozilla
drwxr-xr-x  2 bala bala 4.0K 2011-06-23 07:50 .mplayer
[B]drwxr-xr-x  2 bala bala 4.0K 2010-08-08 16:01 .nautilus
-rw-r--r--  1 bala bala  38K 2011-09-25 15:11 npatgpc.dl_
drwxr-xr-x  3 bala bala 4.0K 2010-08-08 16:22 .openoffice.org
drwx------  3 bala bala 4.0K 2011-05-08 09:00 .pki
-rw-r--r--  1 bala bala   37 2010-08-10 05:51 .printer-groups.xml
-rw-r--r--  1 bala bala  675 2010-08-08 15:54 .profile
drwx------  2 bala bala 4.0K 2011-09-26 09:29 .pulse
-rw-------  1 bala bala  256 2010-08-08 16:01 .pulse-cookie
-rw-------  1 bala bala 121K 2011-09-26 09:46 .recently-used.xbel
-rw-r--r--  1 bala bala 120K 2011-09-25 21:26 .recently-used.xbel.6MNC2V
-rw-r--r--  1 bala bala  99K 2011-09-22 08:03 .recently-used.xbel.WFMC2V
[/B]drwx------  2 bala bala 4.0K 2011-04-23 20:09 .ssh
-rw-r--r--  1 bala bala    0 2010-08-08 16:16 .sudo_as_admin_successful
[B]drwxr-xr-x  2 bala bala 4.0K 2010-08-08 16:02 .themes
drwx------  5 bala bala 4.0K 2010-08-08 16:25 .thumbnails
drwx------  2 bala bala 4.0K 2011-04-22 20:22 .tsclient
drwx------  2 bala bala 4.0K 2010-08-09 19:36 .update-notifier
-rw-r--r--  1 bala bala  39K 2010-09-22 22:04 .usbcreator.log
[/B]drwxr-xr-x  5 bala bala 4.0K 2011-09-26 09:32 .VirtualBox
drwxr-xr-x  2 bala bala 4.0K 2011-09-22 08:01 .vmware
drwxr-xr-x  2 bala bala 4.0K 2011-04-22 20:29 .vnc
[B]-rw-r--r--  1 bala bala  757 2011-05-21 11:56 .Wammu
[/B]drwxr-xr-x  5 bala bala 4.0K 2011-04-14 06:32 .webex
drwxr-xr-x  2 bala bala 4.0K 2011-05-14 22:20 .winff
drwxr-xr-x  2 bala bala 4.0K 2010-09-26 06:02 .wireshark
[B]-rw-------  1 bala bala 4.6K 2011-09-26 10:46 .xsession-errors
-rw-------  1 bala bala  44K 2011-09-25 21:26 .xsession-errors.old
[/B]drwxr-xr-x  2 bala bala 4.0K 2011-09-18 16:37 .zenmap
bala@bala-laptop:~$

---

### Post by .... on 2011-09-26
They're per-user configuration files. Don't worry about them.

---

### Post by squenson on 2011-09-26
The names of the files already are an indication. I see that you are using Virtualbox, a vnc software, the e-mail evolution, etc. Usually, the hidden files in your home folder are created by the software you have installed on your machine and there is nothing to worry about, I think.

---

### Post by papibe on 2011-09-26
They store applications settings, For example:
[LIST]
[*].bashrc stores the initial settings of the interpreter of the terminal window (called bash).
[*].gconf stores settings of your desktop.
[*].compiz store settings of the desktop's effects.
[/LIST]
I would recommend do not modify or erase any of them, unless you research and understand pretty well what they are for.

I hope this helps to answer your concern,
Regards.

---

### Post by bala150985 on 2011-09-26
Thank you :-)

---

### Post by raja.genupula on 2011-09-26
please mark the thread as solved and remember this for every time if your issue as solved.

---

