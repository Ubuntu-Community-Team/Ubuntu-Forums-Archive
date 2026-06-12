---
title: "booting issues"
date: 2010-06-09
forum: General Help
---

### Post by SeriousName on 2010-06-09
So for some unknown reason now, when I try to boot my computer, after the splash screen, I get a series of error message popups followed by being dumped to an empty desktop (just a cursor and background). Here are the error messages:

> Could not update ICEauthority file /home/*/.ICEauthority

> There is a problem with the config server.
(/usr/lib/gconf2-4/gconf-sanity-check exited with status 256)

> Nautilus could not create the following required folders: /home/*/Desktop, /home/*/.nautilus
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

Now, I've found that on the empty desktop, I can open a terminal with ctrl+alt+t. From there I run gnome-system-monitor, and kill process on gnome-session. After doing this, I get the normal login screen, and can get to my desktop. However, I'd really like to fix whatever went wrong so that I don't have to go through this process every time I turn on the computer.

Anyone have any ideas?

---

### Post by pytheas22 on 2010-06-09
Are you sure you're not out of disk space?  That could possibly be the problem.

I'd also suspect an issue with permissions.  What is the output of:
```

ls -la ~
```

EDIT: also take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1455109").  Chances are the solution there will apply for you.

---

### Post by SeriousName on 2010-06-09
The solution in that thread didn't work for me. Got the same error messages, only difference was when I got to my desktop it was reset to Ubuntu standard. Luckily I backed it up, so I have my configuration back again. I notice that the person in that thread got the error messages when logging in, while mine come before the login screen ever shows up.

Here's "ls -la ~":

```
total 624
drwx------ 63 user user 20480 2010-06-09 16:01 .
drwxr-xr-x  4 root root  4096 2010-04-30 09:14 ..
drwx------  3 user user  4096 2010-04-30 15:22 .adobe
drwxr-xr-x  4 user user  4096 2010-05-09 10:34 .audacity-data
-rw-------  1 user user  4832 2010-06-09 15:45 .bash_history
-rw-r--r--  1 user user   220 2010-04-30 09:14 .bash_logout
-rw-r--r--  1 user user  3103 2010-04-30 09:14 .bashrc
drwxr-xr-x  3 user user  4096 2010-05-14 11:46 beast
drwxr-xr-x  2 user user  4096 2010-05-14 12:00 .beast
drwxr-xr-x  5 user user  4096 2010-05-12 16:36 .blender
-rw-r--r--  1 user user    58 2010-05-04 13:59 .Blog
-rw-r--r--  1 user user   505 2010-05-14 12:00 .bserc
drwxr-xr-x  2 user user  4096 2010-05-13 12:27 .bsnes
drwx------ 12 user user  4096 2010-06-09 16:01 .cache
drwx------  3 user user  4096 2010-04-30 19:03 .compiz
drwxr-xr-x 24 user user  4096 2010-06-06 13:16 .config
drwx------  3 user user  4096 2010-06-09 15:59 .dbus
drwxr-xr-x  2 user user  4096 2010-06-03 21:48 Desktop
-rw-r--r--  1 user user    41 2010-06-09 16:01 .dmrc
drwxr-xr-x  2 user user  4096 2010-04-30 09:18 Documents
drwxr-xr-x  2 user user  4096 2010-05-05 16:42 Downloads
lrwxrwxrwx  1 user user   104 2010-04-30 09:14 .ecryptfs -> /home/.ecryptfs/user/.ecryptfs
drwxr-xr-x  2 user user 28672 2010-05-07 22:14 .electricsheep
drwxr-xr-x  3 user user  4096 2010-06-06 13:16 .emerald
-rw-------  1 user user    16 2010-04-30 09:18 .esd_auth
drwxr-xr-x  8 user user  4096 2010-06-06 22:46 .evolution
-rw-r--r--  1 user user   179 2010-04-30 09:14 examples.desktop
-rw-r--r--  1 user user  2627 2010-06-04 12:31 .face
drwxr-xr-x  2 user user  4096 2010-05-19 18:43 .fontconfig
drwx------  5 user user  4096 2010-06-09 16:01 .gconf
drwx------  2 user user  4096 2010-06-09 16:07 .gconfd
drwx------  4 user user  4096 2010-05-19 18:43 .gegl-0.0
drwxr-xr-x  2 user user  4096 2010-05-13 14:22 .gens
drwxr-xr-x 22 user user  4096 2010-06-05 16:31 .gimp-2.6
-rw-r-----  1 user user     0 2010-06-05 13:44 .gksu.lock
drwxr-xr-x  2 user user  4096 2010-05-13 10:56 .gnaural
drwxr-xr-x  2 user user  4096 2010-05-07 12:19 gnaural2
drwx------ 13 user user  4096 2010-06-09 16:00 .gnome2
drwx------  2 user user  4096 2010-06-09 16:00 .gnome2_private
drwxr-xr-x  2 user user  4096 2010-05-07 12:27 .gnomenu
drwxr-xr-x  2 user user  4096 2010-06-04 12:35 .gstreamer-0.10
-rw-r--r--  1 user user   132 2010-06-09 16:01 .gtk-bookmarks
-rw-r--r--  1 user user   261 2010-05-16 23:40 .gtkrc-2.0
dr-x------  2 user user     0 2010-06-09 16:01 .gvfs
-rw-------  1 user user 17784 2010-06-09 16:01 .ICEauthority
drwxr-xr-x  3 user user  4096 2010-04-30 20:00 .icedteaplugin
drwxr-xr-x  3 user user  4096 2010-05-17 00:11 .icons
drwxr-xr-x  2 user user  4096 2010-05-13 12:09 .Kega Fusion
-rw-r--r--  1 user user   527 2010-05-15 23:15 .krankcfg.yaml
drwxr-xr-x  2 user user  4096 2010-05-17 14:32 .lince
drwxr-xr-x  3 user user  4096 2010-04-30 09:24 .local
drwx------  3 user user  4096 2010-04-30 19:47 .macromedia
drwx------  3 user user  4096 2010-04-30 14:32 .mission-control
drwx------  4 user user  4096 2010-04-30 09:28 .mozilla
drwxr-xr-x  2 user user  4096 2010-04-30 19:39 .mplayer
drwxr-xr-x  3 user user  4096 2010-05-07 11:40 Music
drwxr-xr-x  2 user user  4096 2010-04-30 09:18 .nautilus
drwxr-xr-x  3 user user  4096 2010-04-30 19:57 .netx
drwxr-xr-x  3 user user  4096 2010-05-26 15:39 .openoffice.org
drwxr-x---  7 user user  4096 2010-05-20 00:48 .pcsx
-rw-r--r--  1 user user   360 2010-05-18 11:17 .pdsettings
-rw-r--r--  1 user user  3072 2010-05-19 18:17 photos-20100519-0.db
drwxr-xr-x  3 user user  4096 2010-04-30 17:51 Pictures
-rw-r--r--  1 user user  1222 2010-05-05 18:19 player.txt
lrwxrwxrwx  1 user user   104 2010-04-30 09:14 .Private -> /home/.ecryptfs/user/.Private
-rw-r--r--  1 user user   675 2010-04-30 09:14 .profile
drwxr-xr-x  2 user user  4096 2010-04-30 09:18 Public
drwx------  2 user user  4096 2010-06-09 15:59 .pulse
-rw-------  1 user user   256 2010-04-30 09:18 .pulse-cookie
drwxr-xr-x  2 user user  4096 2010-05-18 19:40 puredata
drw-------  2 user user  4096 2010-05-07 11:29 .recently-used.xbel
drwxr-xr-x  3 user user  4096 2010-05-27 21:07 .snes9x
-rw-r--r--  1 user user     0 2010-04-30 15:28 .sudo_as_admin_successful
drwxr-xr-x  4 user user  4096 2010-05-13 23:34 .sudoku
drwx------  2 user user  4096 2010-05-16 10:11 .synaptic
drwxr-xr-x  2 user user  4096 2010-04-30 09:18 Templates
drwxr-xr-x  2 user user  4096 2010-04-30 09:27 .themes
drwx------  5 user user  4096 2010-04-30 17:51 .thumbnails
drwx------  2 user user  4096 2010-05-01 22:25 .TrueCrypt
drwxr-xr-x  4 user user  4096 2010-05-07 11:29 .ubuntu-tweak
-rw-r--r--  1 user user   573 2010-05-16 11:09 Untitled-1.pd
drwx------  2 user user  4096 2010-04-30 09:22 .update-notifier
drwxr-xr-x  2 user user  4096 2010-05-13 11:40 .vbam
drwxr-xr-x  2 user user  4096 2010-04-30 09:18 Videos
drwxr-xr-x  3 user user  4096 2010-06-06 13:16 .wallpapers
-rw-------  1 user user     0 2010-06-07 14:46 .Xauthority
-rw-r--r--  1 user user   559 2010-04-30 17:50 .xscreensaver-getimage.cache
-rw-------  1 user user  2543 2010-06-09 16:07 .xsession-errors
-rw-------  1 user user  4039 2010-06-09 16:00 .xsession-errors.old
drwxr-xr-x  2 user user  4096 2010-05-13 13:31 .zsnes
```

---

### Post by pytheas22 on 2010-06-09
Is your username actually "user"?  If not, that's likely the problem and you will need to chown the files in your home directory to your account name.

If your account really is named "user", then I'm still not positive what's wrong, because the permissions look alright.  I wonder if removing your ~/.nautilus directory to force a fresh configuration might help:
```

mv ~/.nautilus ~/.nautilus-old
```

---

### Post by SeriousName on 2010-06-10
My username isn't user, I just replaced all instances of my actual username. Sorry for the confusion.

Tried removing ~/.nautilus, it didn't help. In fact, both the backup and the new folder it automatically created (after killing gnome-session and logging in) are empty, no config files or anything.

---

### Post by pytheas22 on 2010-06-10
hmmm, I'm still not sure what could be wrong.  Does renaming your .gnome2 directory and then rebooting solve anything:
```

mv ~/.gnome2 ~/.gnome2-old
```

That will set you back to default Gnome settings, but at least it will help narrow down the possible sources of the problem.

Also, is your account configured to log into Gnome automatically and bypass the login screen?

---

### Post by SeriousName on 2010-06-10
I already tried removing ~/.gnome2 as a part of the solution of that other thread, and no, my system isn't set up to bypass the login screen.

I'm thinking this has something to do with Ubuntu bringing up GDM. Does it maybe start up a Gnome session before bringing up the login screen? And if that's the case, where would the config files for that session be located?

Also, thanks for your persistence.

---

### Post by pytheas22 on 2010-06-11
> I'm thinking this has something to do with Ubuntu bringing up GDM. Does it maybe start up a Gnome session before bringing up the login screen? And if that's the case, where would the config files for that session be located?

Something like that could be happening.  The gdm configuration files are all in /etc/gdm.  Most of Gnome's relevant files are in ~/.gnome2, but changing that folder apparently didn't help you.

When you get dumped to the empty desktop, which user are you logged in as?  You can find out by typing "whoami" in a terminal.

If you go to System>Administration>Login Screen and set the system to log you in automatically, does the problem persist?

---

### Post by SeriousName on 2010-06-11
Apparently when I get dumped to the empty desktop, I'm logged in to my account. Very strange.

For some reason, I can't set myself to login automatically. The box where you're supposed to be able to select a user to auto-login is grayed out and empty.

This might be relevant: I tried going to System>Administration>Users and Groups, and set my account to not require a login. After doing this and restarting, it got to the login screen, but when I clicked my account it gave the error messages and an empty desktop. Killing gnome-session would only bring me back to the login screen, and the same thing would happen if I tried to login again. I used the command "users-admin" to get the Users and Groups controls up and set my account back to requiring a login, which set it back to the way it was, letting me kill gnome-session and login as before.

---

### Post by pytheas22 on 2010-06-11
What does your /etc/X11/Xsession.d directory look like?  I think these are the scripts that get run, in numeric order, when gdm starts.  If something is out of order, that could be screwing things up.  It does kind of seem like gnome-session might be getting called before it's supposed to be.  This is what /etc/X11/Xsession.d looks like for me:

```
$ ls
20x11-common_process-args                    60xdg-user-dirs-update
30x11-common_xresources                      70gconfd_path-on-session
40x11-common_xsessionrc                      75dbus_dbus-launch
50x11-common_determine-startup               80im-switch
52libcanberra-gtk-module_add-to-gtk-modules  90consolekit
55gnome-session_gnomerc                      90x11-common_ssh-agent
60x11-common_localhost                       99x11-common_start
60xdg_path-on-session

```

You could also try creating a different user account, setting it to auto-log in, and see if that behaves any differently.  The results would at least let us know whether the problem lies with your system-wide configuration files (mostly stored in /etc) or with a user-specific file in your home directory.

---

### Post by SeriousName on 2010-06-12
Uh, well, the problem seems to have fixed itself. Just booted fine, no error messages, no empty desktop. Maybe the update I did yesterday fixed it?

Anyway, thanks again for your help.

---

### Post by pytheas22 on 2010-06-12
That's strange, but I'm glad to hear it's sorted out.  Sorry we couldn't get to the bottom of it sooner. Computers are so confusing sometimes :)

---

