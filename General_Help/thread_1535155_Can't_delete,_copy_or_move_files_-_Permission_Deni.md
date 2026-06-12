---
title: "Can't delete, copy or move files - Permission Denied"
date: 2010-07-20
forum: General Help
---

### Post by shokkapic on 2010-07-20
As the title says, I can't perform any of those.

Except from the Terminal.

I didn't edit any permission... nor installed anything.

Don't know what to do.

Also, "Move to Trash" appears grayed out, in the right-click menu (for all the files/folders).


Any help would be highly appreciated.


Ubuntu 10.04 x64

---

### Post by bodhi.zazen on 2010-07-20
Normally you can only modify things in your /home directory.

Outside of home you need to use root, sudo or for graphical application gksu

See:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by endotherm on 2010-07-20
right click on a file that you can't modify, and select Properties. then go to the permissions tab. what account is the owner and what group owns it?  alternatively, show us an 
```
ls -al
```
on an affected directory.

---

### Post by shokkapic on 2010-07-20
I'm talking of my Desktop folder, or an external drive.

---

### Post by shokkapic on 2010-07-20
drwxrwxrwx 43 pedro pedro   4096 2010-07-20 19:20 .
drwxr-xr-x  3 root  root    4096 2010-04-30 23:34 ..
drwxrwxrwx  3 pedro root    4096 2010-06-28 20:56 .adobe
-rw----rw-  1 pedro pedro   9934 2010-07-20 19:05 .bash_history
-rw-r--rw-  1 pedro pedro    220 2010-04-30 23:34 .bash_logout
-rwxr-xrwx  1 pedro pedro   3218 2010-07-15 17:17 .bashrc
drwxrwxrwx  2 pedro root    4096 2010-07-18 18:42 bin
drwx------  8 pedro pedro   4096 2010-07-20 19:17 .cache
drwxrwxrwx  3 pedro root    4096 2010-05-01 18:17 .compiz
drwxrwxrwx 14 pedro pedro   4096 2010-07-20 18:37 .config
drwxrwxrwx  3 pedro pedro   4096 2010-05-01 00:08 .dbus
drwxr-xr-x  3 root  root    4096 2010-07-20 18:44 Desktop
-rw-r--r--  1 pedro admin     41 2010-07-20 19:17 .dmrc
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Documents
drwxrwxrwx  2 pedro pedro   4096 2010-07-20 17:54 Downloads
-rw----rw-  1 pedro pedro     16 2010-05-01 00:09 .esd_auth
drwxrwxrwx  8 pedro pedro   4096 2010-05-05 13:22 .evolution
-rw-r--rw-  1 pedro pedro    179 2010-04-30 23:34 examples.desktop
-rw-r--rw-  1 pedro root    2041 2010-05-01 17:54 .face
drwxrwxrwx  2 pedro root    4096 2010-07-14 23:57 .fontconfig
drwxrwxrwx  5 pedro pedro   4096 2010-07-20 19:19 .gconf
drwxrwxrwx  2 pedro pedro   4096 2010-07-20 19:23 .gconfd
drwxrwxrwx  4 pedro root    4096 2010-07-14 23:57 .gegl-0.0
drwxrwxrwx 22 pedro root    4096 2010-07-14 23:58 .gimp-2.6
-rw-r--rw-  1 pedro root      19 2010-07-18 18:46 .gitconfig
-rw-r--rw-  1 pedro pedro      0 2010-07-20 19:05 .gksu.lock
drwxrwxrwx 10 pedro pedro   4096 2010-07-20 19:18 .gnome2
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:09 .gnome2_private
drwxrwxrwx  2 pedro pedro   4096 2010-07-11 11:04 .gstreamer-0.10
-rw-r--r--  1 pedro admin    137 2010-07-20 19:17 .gtk-bookmarks
dr-x------  2 pedro admin      0 2010-07-20 19:17 .gvfs
-rw----rw-  1 pedro pedro   8554 2010-07-20 19:17 .ICEauthority
drwxrwxrwx  3 pedro root    4096 2010-07-11 10:38 .kde
-rwxr-xr-x  1 root  root  247036 2010-07-20 17:37 lib
drwxrwxrwx  3 pedro pedro   4096 2010-05-01 00:09 .local
drwxrwxrwx  3 pedro root    4096 2010-06-28 20:56 .macromedia
drwxrwxrwx  3 pedro pedro   4096 2010-05-01 00:13 .mission-control
drwxrwxrwx  4 pedro pedro   4096 2010-05-01 14:22 .mozilla
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Music
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:09 .nautilus
-rw-r--rw-  1 pedro root    1200 2010-05-01 17:58 .nvidia-settings-rc
drwxrwxrwx  3 pedro root    4096 2010-07-14 23:49 .openoffice.org
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Pictures
drwxrwxrwx  3 pedro root    4096 2010-07-11 10:38 .pki
-rw-r--rw-  1 pedro pedro    675 2010-04-30 23:34 .profile
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Public
drwx------  2 pedro admin   4096 2010-07-20 18:54 .pulse
-rw----rw-  1 pedro pedro    256 2010-05-01 00:08 .pulse-cookie
drwx------  5 pedro admin   4096 2010-07-20 19:29 .purple
-rw-------  1 pedro root   53380 2010-07-20 19:17 .recently-used.xbel
drwxrwxrwx  5 pedro root    4096 2010-07-18 19:13 .repo
drwxrwxrwx  3 pedro root    4096 2010-07-18 18:46 .repoconfig
-rw-r--rw-  1 pedro root      31 2010-07-18 18:47 .repopickle_.gitconfig
drwxrwxrwx  3 pedro root    4096 2010-07-11 18:42 .subversion
-rw-r--rw-  1 pedro pedro      0 2010-05-01 00:19 .sudo_as_admin_successful
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Templates
drwxrwxrwx  3 pedro pedro   4096 2010-05-01 00:12 .thumbnails
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:10 .update-notifier
drwxrwxrwx  2 pedro pedro   4096 2010-05-01 00:08 Videos
drwxrwxrwx  4 pedro root    4096 2010-07-14 23:33 .wine
drwxrwxrwx  2 pedro root    4096 2010-05-04 23:52 .winetrickscache
-rw-------  1 pedro admin   3458 2010-07-20 19:31 .xsession-errors
-rw----rw-  1 pedro root    5274 2010-07-20 19:17 .xsession-errors.old

---

### Post by RiceMonster on 2010-07-20
You have a whole bunch of stuff owned by root in your home directory. Try this:
```
chmod -R pedro:pedro ~/*
```

---

### Post by endotherm on 2010-07-20
assuming you are logged in as pedro, you should already have most if not all the rights you need on everything except the desktop (notice, it is owned by root:root)

try this:
```
sudo chown -R pedro:pedro /home/pedro/Desktop
```

after that, you should own your desktop and all files/folders on it. 
after that you can use the RClick -> Properties -> Permissions to provide any additional privledges you require. 

let us know how it works out,.

---

### Post by shokkapic on 2010-07-20
> **endotherm said:**
> assuming you are logged in as pedro, you should already have most if not all the rights you need on everything except the desktop (notice, it is owned by root:root)

try this:
```
sudo chown -R pedro:pedro /home/pedro/Desktop
```

after that, you should own your desktop and all files/folders on it. 
after that you can use the RClick -> Properties -> Permissions to provide any additional privledges you require. 

let us know how it works out,.


Worked fantastically.

Very appreciated. :D

---

### Post by bodhi.zazen on 2010-07-20
> **shokkapic said:**
> Worked fantastically.

Very appreciated. :D

FYI, most likely this occurred as you are running graphical applications as root with sudo

```
sudo gedit
```

Use gksu for graphical applications.

```
gksu gedit
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

