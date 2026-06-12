---
title: "Error on editing .bashrc"
date: 2010-12-28
forum: General Help
---

### Post by karthick87 on 2010-12-28
I get the following error on editing my .bashrc file.How to fix it??
```
karthick@Ubuntu-desktop:~$ gedit .bashrc

(gedit:3934): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

(gedit:3934): Gtk-WARNING **: Attempting to store changes into `/home/karthick/.recently-used.xbel', but failed: Failed to rename file '/home/karthick/.recently-used.xbel.HUL4NV' to '/home/karthick/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3934): Gtk-WARNING **: Attempting to set the permissions of `/home/karthick/.recently-used.xbel', but failed: Operation not permitted

```

---

### Post by lungten on 2010-12-28
Most probably, the files mentioned in the earning messages are not owned by your user.
```
ls -la ~
```

---

### Post by karthick87 on 2010-12-28
Here is the output:
```
karthick@Ubuntu-desktop:~$ ls -la ~
total 856
drwxr-xr-x 92 karthick karthick  12288 2010-12-28 23:43 .
drwxr-xr-x  3 karthick root       4096 2010-12-24 16:54 ..
drwxr-xr-x  4 karthick karthick   4096 2010-06-16 12:58 .adobe
drwx------  2 karthick karthick   4096 2010-12-27 02:06 .aptitude
-rwxr-xr-x  1 karthick karthick      0 2010-11-06 02:14 .autoreg
-rw-r--r--  1 root     root         49 2010-12-25 21:30 .bash_aliases
-rwxr-xr-x  1 karthick karthick  31307 2010-12-28 23:47 .bash_history
-rwxr-xr-x  1 karthick karthick    253 2010-12-24 15:43 .bash_logout
-rwxr-xr-x  1 karthick karthick   3215 2010-12-26 20:15 .bashrc
drwxr-xr-x  2 karthick karthick   4096 2010-11-17 02:04 .bazaar
drwxr-xr-x  4 karthick karthick   4096 2010-12-04 02:46 bodweb
drwxr-xr-x  2 karthick karthick   4096 2010-12-02 15:56 Books
-rw-r--r--  1 karthick karthick  46891 2010-12-01 02:14 .bzr.log
drwx------ 24 karthick karthick   4096 2010-12-28 22:41 .cache
drwxr-xr-x  2 karthick karthick   4096 2010-06-06 00:11 .camel_certs
drwxr-xr-x  4 karthick karthick   4096 2010-12-13 17:13 .chmsee
drwxr-xr-x  3 karthick karthick   4096 2010-05-19 19:11 .compiz
drwxr-xr-x 31 karthick karthick   4096 2010-12-16 00:37 .config
drwxr-xr-x  6 karthick karthick   4096 2010-06-12 16:08 .conkycolors
-rw-r--r--  1 karthick karthick    637 2010-12-17 14:27 .conkyForecast.config
-rwxr-xr-x  1 root     root       3866 2010-12-18 10:00 .conkyrc
-rwxr-xr-x  1 root     root         31 2010-12-28 01:34 .conky-startup.sh
drwxr-xr-x  4 karthick karthick   4096 2010-06-16 23:32 .ConkyWizardTheme
drwxr-xr-x  5 root     root       4096 2010-11-08 20:40 .cpan
drwxr-xr-x  3 karthick karthick   4096 2010-05-19 19:10 .dbus
drwxr-xr-x  2 karthick karthick   4096 2010-12-27 02:06 .debtags
drwxr-xr-x  3 karthick karthick   4096 2010-12-28 22:58 Desktop
drwxr-xr-x  2 karthick karthick   4096 2010-06-16 20:39 .Devilspie
drwxr-xr-x  5 karthick karthick   4096 2010-12-16 22:23 Documents
drwxr-xr-x  6 karthick karthick   4096 2010-12-25 02:40 Downloads
drwxr-xr-x 22 karthick karthick   4096 2010-10-19 23:44 DUMPS
drwxr-xr-x  2 karthick karthick   4096 2010-06-19 22:05 .easytag
drwx------  2 karthick karthick   4096 2010-11-23 15:41 .elinks
-rwxr-xr-x  1 karthick karthick     16 2010-05-19 19:10 .esd_auth
drwxr-xr-x  8 karthick karthick   4096 2010-11-29 01:26 .evolution
-rwxr-xr-x  1 karthick karthick   2281 2010-01-10 10:43 .face
-rwxr-xr-x  1 karthick karthick  53843 2010-11-02 06:13 file.html
drwxr-xr-x  4 karthick karthick   4096 2010-12-24 12:02 .fltk
drwxr-xr-x  2 karthick karthick   4096 2010-12-23 20:39 .fontconfig
drwxr-xr-x  3 karthick karthick   4096 2010-12-19 12:35 .fonts
drwxr-xr-x  5 karthick karthick   4096 2010-12-28 22:41 .gconf
drwxr-xr-x  2 karthick karthick   4096 2010-12-28 23:48 .gconfd
drwxr-xr-x  4 karthick karthick   4096 2010-06-05 18:43 .gegl-0.0
drwxr-xr-x 22 karthick karthick   4096 2010-12-28 12:24 .gimp-2.6
-rwxr-xr-x  1 karthick karthick      0 2010-05-19 14:29 .gksu.lock
drwxr-xr-x 13 karthick karthick   4096 2010-12-28 20:53 .gnome2
drwxr-xr-x  2 karthick karthick   4096 2010-05-19 19:11 .gnome2_private
-rwxr-xr-x  1 karthick karthick   7168 2010-10-07 07:29 .gnome-rdp.db
drwxr-xr-x  2 karthick karthick   4096 2010-12-20 19:11 .gnupg
drwxr-xr-x  2 karthick karthick   4096 2010-12-22 14:40 .gstreamer-0.10
-rw-r--r--  1 karthick karthick    123 2010-12-28 22:41 .gtk-bookmarks
-rw-r--r--  1 karthick karthick    971 2010-12-14 15:53 .gtk-recordmydesktop
drwxr-xr-x 79 karthick karthick  16384 2010-11-07 17:58 Guides
dr-x------  2 karthick karthick      0 2010-12-28 22:41 .gvfs
drwxr--r--  2 karthick karthick   4096 2010-11-09 13:45 .hardinfo
-rw-------  1 karthick karthick  12288 2010-11-16 01:28 .helloworld.py.swo
-rw-------  1 karthick karthick  12288 2010-11-15 02:28 .helloworld.py.swp
-rw-r--r--  1 karthick karthick     32 2010-12-24 16:51 .hidden
-rwxr-xr-x  1 karthick karthick 136860 2010-12-28 22:41 .ICEauthority
drwxr-xr-x  3 karthick karthick   4096 2010-11-08 18:51 .icedteaplugin
drwxr-xr-x  3 karthick karthick   4096 2010-12-22 10:35 .icons
drwx------  2 karthick karthick   4096 2010-11-11 01:08 .irssi
drwx------  3 karthick karthick   4096 2010-11-11 02:50 .kde
drwxr--r--  2 karthick karthick   4096 2010-11-07 02:21 .linuxcounter
drwxr-xr-x  3 karthick karthick   4096 2010-05-19 19:11 .local
drwxr-xr-x  3 karthick karthick   4096 2010-06-16 12:58 .macromedia
drwxr-xr-x  3 karthick karthick   4096 2010-05-19 14:08 .mission-control
drwxr-xr-x  3 karthick karthick   4096 2010-10-03 11:20 .Mix
drwxr-xr-x  4 karthick karthick   4096 2010-05-19 13:56 .mozilla
lrwxrwxrwx  1 karthick karthick     27 2010-11-07 19:17 .mozilla-thunderbird -> /home/karthick/.thunderbird
drwxr-xr-x  2 karthick karthick   4096 2010-11-04 12:51 .mplayer
drwxr-xr-x 21 karthick karthick  12288 2010-12-22 21:22 Music
drwxr-xr-x  3 karthick karthick   4096 2010-10-03 05:00 .mutt
-rwxr-xr-x  1 karthick karthick   2489 2010-10-29 22:01 .muttrc
drwxr-xr-x  2 karthick karthick   4096 2010-05-19 19:10 .nautilus
drwxr-xr-x  3 karthick karthick   4096 2010-11-08 11:37 .netx
drwxr-xr-x  2 karthick karthick   4096 2010-11-08 00:18 .ntrc_2
drwxr-xr-x  3 karthick karthick   4096 2010-05-19 14:12 .openoffice.org
drwxr-xr-x 17 karthick karthick   4096 2010-12-26 13:22 .opera
drwxr-xr-x  9 karthick karthick   4096 2010-12-13 02:44 .opera_widget_manager
-rwxr-xr-x  1 karthick karthick      0 2010-11-06 01:54 .parentlock
drwxr-xr-x  3 karthick karthick   4096 2010-12-07 03:34 Perl
drwxr-xr-x  3 karthick karthick   4096 2010-12-09 02:27 Perll
drwxr-xr-x  6 karthick karthick   4096 2005-01-01 00:46 PHP MAIL
drwxr-xr-x  7 karthick karthick   4096 2010-12-24 22:56 Pictures
drwxr-xr-x  3 karthick karthick   4096 2010-10-01 20:34 .pki
drwxr-xr-x 10 karthick karthick   4096 2010-09-25 10:35 .PlayOnLinux
drwxr-xr-x 23 karthick karthick   4096 2010-10-28 22:38 POSTFIX
-rwxr-xr-x  1 karthick karthick     37 2010-05-20 00:26 .printer-groups.xml
-rwxr-xr-x  1 karthick karthick    675 2010-05-19 19:05 .profile
drwxr-xr-x  5 karthick karthick   4096 2010-06-06 12:00 Programming
drwxr-xr-x  3 karthick karthick   4096 2010-12-28 14:35 Public
drwx------  2 karthick karthick   4096 2010-12-28 22:41 .pulse
-rwxr-xr-x  1 karthick karthick    256 2010-05-19 19:10 .pulse-cookie
drwxr-xr-x  8 karthick karthick   4096 2010-12-27 15:07 .purple
-rw-r--r--  1 karthick karthick   1056 2010-12-06 01:06 Q
drwxr-xr-x  5 karthick karthick   4096 2010-10-02 05:01 .qmmp
drwxr-xr-x  2 karthick karthick   4096 2010-11-11 23:36 .qt
-rw-r--r--  1 karthick karthick      0 2010-05-19 14:14 .recently-used.xbel
-rwxr-xr-x  1 root     root       1024 2010-10-27 14:11 .rnd
drwxr-xr-x  3 karthick karthick   4096 2010-06-10 05:20 .scim
drwxr-xr-x  2 karthick karthick   4096 2010-06-16 15:13 .Scripts
-rw-r--r--  1 karthick karthick     66 2010-11-22 18:50 .selected_editor
drwxr-xr-x  3 karthick karthick   4096 2010-12-28 12:25 .shutter
-rw-------  1 karthick karthick    475 2010-11-22 15:29 .sqlite_history
drwxr-xr-x  2 karthick karthick   4096 2010-11-10 01:01 .ssh
drwxr-xr-x  3 karthick karthick   4096 2010-12-01 01:19 .stackapplet
-rwxr-xr-x  1 karthick karthick     70 2010-12-07 00:28 .stackapplet-start.sh
drwxr-xr-x  3 karthick karthick   4096 2010-12-04 18:07 .subversion
-rwxr-xr-x  1 karthick karthick      0 2010-05-19 14:02 .sudo_as_admin_successful
drwxr-xr-x  4 karthick karthick   4096 2010-05-22 19:36 .sudoku
drwxr-xr-x  6 karthick karthick   4096 2010-11-28 17:04 SUPY
drwxr-xr-x  9 karthick karthick   4096 2010-12-12 16:26 supybot
-rw-------  1 karthick karthick  12288 2010-11-30 02:23 .swp
-rw-r--r--  1 karthick karthick   3268 2010-12-04 15:03 .tagtoolrc
drwxr-xr-x  3 karthick karthick   4096 2010-12-23 15:48 .teamviewer
drwxr-xr-x  2 karthick karthick   4096 2010-12-05 02:40 Templates
drwxr-xr-x  2 karthick karthick   4096 2010-10-05 03:27 .themes
drwxr-xr-x  5 karthick karthick   4096 2010-12-25 15:06 .thumbnails
drwxr-xr-x  4 karthick root       4096 2010-11-03 12:59 .thunderbird
drwxr-xr-x  2 karthick karthick   4096 2010-05-20 00:12 .tsclient
drwxr-xr-x  3 karthick karthick   4096 2010-08-22 23:27 .tucan
-rw-r--r--  1 karthick karthick      0 2010-12-27 11:27 .tzlist
drwxr-xr-x  2 karthick karthick   4096 2010-05-19 19:11 .update-notifier
-rwxr-xr-x  1 karthick karthick   2820 2010-05-20 23:38 .usbcreator.log
-rw-------  1 karthick karthick   4395 2010-12-10 01:25 .viminfo
-rw-r--r--  1 karthick karthick      0 2010-12-06 18:23 .vimrc
drwxr-xr-x  4 karthick karthick   4096 2010-12-24 13:03 .VirtualBox
drwxr-xr-x  2 karthick karthick   4096 2010-10-03 05:07 .w3m
-rwxr-xr-x  1 karthick karthick    335 2010-06-25 02:51 .wcalc_history
drwxr-xr-x  2 karthick karthick   4096 2010-11-06 02:21 .wireshark
-rw-------  1 karthick karthick      0 2010-12-19 00:52 .Xauthority
-rw-r--r--  1 karthick karthick     67 2010-12-12 15:36 .xbindkeysrc
drwxr-xr-x  5 karthick karthick   4096 2010-12-28 00:40 .xchat2
-rwxr-xr-x  1 karthick karthick    448 2010-06-10 22:47 .xchm
-rwxr-xr-x  1 karthick karthick    559 2010-05-20 00:22 .xscreensaver-getimage.cache
-rw-------  1 karthick karthick      0 2010-12-10 01:45 .xsel.log
-rw-------  1 karthick karthick  14509 2010-12-28 23:49 .xsession-errors
-rw-------  1 karthick karthick   6654 2010-12-28 20:53 .xsession-errors.old
```

---

### Post by lungten on 2010-12-28
As you can see, those files are owned by root. That's why the error. Your user does not have permissions to modify those files.
```
sudo chown -R karthick:karthick /home/karthick/.*
```
should fix the problem assuming /home/karthick is your home directory. Or simply run ```
sudo chown -R karthick:karthick ~/.*
``` if you are logged in as karthick instead of root.

---

### Post by karthick87 on 2010-12-28
> sudo chown -R karthick:karthick /home/karthick/.*
```
karthick@Ubuntu-desktop:~$ sudo chown -R karthick:karthick /home/karthick/.*
chown: cannot access `/home/karthick/./.gvfs': Permission denied
chown: changing ownership of `/home/karthick/./.recently-used.xbel': Operation not permitted
chown: cannot access `/home/karthick/.gvfs': Permission denied
chown: changing ownership of `/home/karthick/.recently-used.xbel': Operation not permitted
```
> sudo chown -R karthick:karthick ~/.*
```
karthick@Ubuntu-desktop:~$ sudo chown -R karthick:karthick ~/.*
chown: cannot access `/home/karthick/./.gvfs': Permission denied
chown: changing ownership of `/home/karthick/./.recently-used.xbel': Operation not permitted
chown: cannot access `/home/karthick/.gvfs': Permission denied
chown: changing ownership of `/home/karthick/.recently-used.xbel': Operation not permitted

```

---

