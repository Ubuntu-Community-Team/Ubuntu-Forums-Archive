---
title: "Files missing"
date: 2011-03-17
forum: General Help
---

### Post by bacon_user on 2011-03-17
I updated my pc and now all my files are missing.

```
house@house:~$ ls -al
total 160
drwxr-xr-x 26 house house  4096 2011-03-17 14:54 .
drwxr-xr-x  5 root  root   4096 2010-11-30 00:45 ..
lrwxrwxrwx  1 house house    56 2010-07-29 12:18 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------  3 house house  4096 2011-03-16 23:39 .adobe
-rw-------  1 house house  1553 2011-03-17 14:54 .bash_history
drwx------  9 house house  4096 2011-03-17 14:40 .cache
drwx------  3 house house  4096 2011-03-17 12:17 .compiz
drwxr-xr-x  9 house house  4096 2011-03-17 12:11 .config
drwx------  3 house house  4096 2011-03-16 23:38 .dbus
drwxr-xr-x  2 house house  4096 2011-03-17 12:06 Desktop
-rw-r--r--  1 house house    41 2011-03-17 14:40 .dmrc
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Documents
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Downloads
lrwxrwxrwx  1 house house    31 2010-07-29 12:18 .ecryptfs -> /home/.ecryptfs/house/.ecryptfs
-rw-------  1 house house    16 2011-03-17 12:06 .esd_auth
drwx------  4 house house  4096 2011-03-17 14:40 .gconf
drwx------  2 house house  4096 2011-03-17 14:54 .gconfd
drwx------  7 house house  4096 2011-03-17 12:12 .gnome2
drwx------  2 house house  4096 2011-03-17 12:08 .gnome2_private
drwxr-xr-x  2 house house  4096 2011-03-17 12:11 .gstreamer-0.10
-rw-r--r--  1 house house   137 2011-03-17 14:40 .gtk-bookmarks
dr-x------  2 house root      0 2011-03-17 14:40 .gvfs
-rw-------  1 house house  1888 2011-03-17 14:40 .ICEauthority
drwxr-xr-x  3 house house  4096 2011-03-17 12:07 .local
drwx------  3 house house  4096 2011-03-16 23:39 .macromedia
drwx------  4 house house  4096 2011-03-16 23:38 .mozilla
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Music
drwxr-xr-x  2 house house  4096 2011-03-17 14:54 .nautilus
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Pictures
lrwxrwxrwx  1 house house    30 2010-07-29 12:18 .Private -> /home/.ecryptfs/house/.Private
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Public
drwx------  2 house house  4096 2011-03-17 14:47 .pulse
-rw-------  1 house house   256 2011-03-16 23:39 .pulse-cookie
lrwxrwxrwx  1 house house    52 2010-07-29 12:18 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
-rw-------  1 house house  2101 2011-03-17 14:44 .recently-used.xbel
-rw-r--r--  1 house house     0 2011-03-17 12:12 .sudo_as_admin_successful
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Templates
drwxr-xr-x  2 house house  4096 2011-03-17 12:07 Videos
-rw-------  1 house house  7559 2011-03-17 14:54 .xsession-errors
-rw-------  1 house house 17000 2011-03-17 12:40 .xsession-errors.old

```

---

### Post by lithopsian on 2011-03-17
> I updated my pc
I have no idea what that means.  You bought a new computer?  You installed a new operating system?  You flashed your BIOS?

> now all my files are missing
Again, we're not psychic.  Which files?

---

### Post by bacon_user on 2011-03-17
I used system update, after that I had a nautilus sanity error and no task bar.

I did a few commands in the task bar to try fix it and it worked, but now I don't have my files.

---

### Post by mimor on 2011-03-17
I can see you had an encrypted filesystem:
.ecryptfs -> /home/.ecryptfs/house/.ecryptfs

Did you read the README.txt in your home directory?

---

### Post by bacon_user on 2011-03-17
Yes and it says to run  ecryptfs-mount-private

But it asks for a login passphrase and I didn't set one

---

### Post by mimor on 2011-03-17
It should've asked one when you've encrypted it (prolly during setup)
Just your root password?

You might also want to consult their irc channel: irc://irc.oftc.net/#ecryptfs

---

