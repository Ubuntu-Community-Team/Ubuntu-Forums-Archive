---
title: "Permission on /home/username"
date: 2009-12-12
forum: General Help
---

### Post by ludydoo on 2009-12-12
Hi

I think I messed up permissions on my /home/ludovic/ folder. 

Each time I open the terminal, I receive this code :

```


bash: /home/ludovic/.bashrc: Permission denied


```I think I did something like

```


sudo chmod 700 /home/ludovic/


```Any idea how to restore this?

---

### Post by mikewhatever on 2009-12-12
sudo chmod 755 /home/ludovic/

Be careful in the future.

---

### Post by ludydoo on 2009-12-12
Thanks for the answer

When I type

```

sudo chmod -R 755 /home/ludovic

```I receive 

```

chmod: cannot access '/home/ludovic/.gvfs': Permission denied

```And my whole desktop is messed up. The regular launcher's icons are gone, their name has changed..

---

### Post by mikewhatever on 2009-12-12
You shouldn't need '-R', the recursive switch if you didn't use it before.
Let's see the output of 'ls -la'.

---

### Post by ludydoo on 2009-12-12
Very weird. I can't access any of my desktop launchers. 

```

root@ludovic-laptop:/home/ludovic# ls -l
total 4052
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 22:06 Desktop
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Documents
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 08:23 Downloads
-rwxr-xr-x  1 ludovic ludovic     167 2009-12-09 22:23 examples.desktop
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Music
drwxr-xr-x 12 ludovic ludovic    4096 2009-11-18 12:28 passenger-2.2.7
-rwxr-xr-x  1 ludovic ludovic 2041344 2009-11-18 15:37 passenger-2.2.7.gem
-rwxr-xr-x  1 ludovic ludovic       0 2009-12-10 23:50 passenger-2.2.7.tar.gz
-rwxr-xr-x  1 ludovic ludovic 2045572 2009-11-18 12:32 passenger-2.2.7.tar.gz.1
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Pictures
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-11 08:44 Programmation
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Public
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Templates
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-10 09:28 untitled folder
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Videos
drwxr-xr-x  5 ludovic ludovic    4096 2009-12-10 02:23 Web
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 02:14 workspace
root@ludovic-laptop:/home/ludovic# 


```

---

### Post by ludydoo on 2009-12-12
look at that : 

```


oot@ludovic-laptop:/home/ludovic# ls -al
ls: cannot access .gvfs: Permission denied
total 4340
drwxr-xr-x 45 ludovic ludovic    4096 2009-12-11 23:59 .
drwx------  3 root    root       4096 2009-12-10 04:39 ..
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-11 08:21 .adobe
-rwxr-xr-x  1 ludovic ludovic     139 2009-12-11 02:31 .bash_aliases
-rwxr-xr-x  1 ludovic ludovic     136 2009-12-11 02:31 .bash_aliases~
-rwxr-xr-x  1 ludovic ludovic   11525 2009-12-11 20:49 .bash_history
-rwxr-xr-x  1 ludovic ludovic     220 2009-12-09 22:23 .bash_logout
-rwxr-xr-x  1 ludovic ludovic    3180 2009-12-09 22:23 .bashrc
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-11 20:49 .cache
drwxr-xr-x  7 ludovic ludovic    4096 2009-12-11 19:52 .config
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-09 22:34 .dbus
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 22:06 Desktop
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Documents
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 08:23 Downloads
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 02:14 .eclipse
-rwxr-xr-x  1 ludovic ludovic      16 2009-12-09 22:34 .esd_auth
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-09 23:19 .evolution
-rwxr-xr-x  1 ludovic ludovic     167 2009-12-09 22:23 examples.desktop
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-10 01:34 .fontconfig
drwxr-xr-x  4 ludovic ludovic    4096 2009-12-11 00:18 .gconf
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-12 07:02 .gconfd
drwxr-xr-x  4 ludovic ludovic    4096 2009-12-10 10:33 .gem
-rwxr-xr-x  1 ludovic ludovic       0 2009-12-12 06:54 .gksu.lock
drwxr-xr-x  9 ludovic ludovic    4096 2009-12-11 20:48 .gnome2
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 .gnome2_private
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 00:13 .gnupg
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:56 .gstreamer-0.10
-rwxr-xr-x  1 ludovic ludovic     199 2009-12-11 08:23 .gtk-bookmarks
d?????????  ? ?       ?             ?                ? .gvfs
-rwxr-xr-x  1 ludovic ludovic    2450 2009-12-11 00:13 .ICEauthority
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 23:06 .icons
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 01:35 .java
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-09 23:14 .local
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-11 08:21 .macromedia
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 05:20 .mission-control
drwxr-xr-x  5 ludovic ludovic    4096 2009-12-10 02:26 .mozilla
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Music
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 .nautilus
drwxr-xr-x 12 ludovic ludovic    4096 2009-11-18 12:28 passenger-2.2.7
-rwxr-xr-x  1 ludovic ludovic 2041344 2009-11-18 15:37 passenger-2.2.7.gem
-rwxr-xr-x  1 ludovic ludovic       0 2009-12-10 23:50 passenger-2.2.7.tar.gz
-rwxr-xr-x  1 ludovic ludovic 2045572 2009-11-18 12:32 passenger-2.2.7.tar.gz.1
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Pictures
-rwxr-xr-x  1 ludovic ludovic     675 2009-12-09 22:23 .profile
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-11 08:44 Programmation
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Public
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 00:13 .pulse
-rwxr-xr-x  1 ludovic ludovic     256 2009-12-09 22:34 .pulse-cookie
-rwxr-xr-x  1 ludovic ludovic   32119 2009-12-11 23:59 .recently-used.xbel
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 10:35 .ri1.9.1
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 .ssh
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-11 09:13 .subversion
-rwxr-xr-x  1 ludovic ludovic       0 2009-12-09 22:35 .sudo_as_admin_successful
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Templates
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 23:06 .themes
drwxr-xr-x  4 ludovic ludovic    4096 2009-12-09 23:06 .thumbnails
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-10 09:28 untitled folder
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:36 .update-manager-core
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 .update-notifier
-rwxr-xr-x  1 ludovic ludovic       5 2009-12-11 00:13 .vboxclient-clipboard.pid
-rwxr-xr-x  1 ludovic ludovic       5 2009-12-11 00:13 .vboxclient-display.pid
-rwxr-xr-x  1 ludovic ludovic       5 2009-12-11 00:13 .vboxclient-seamless.pid
drwxr-xr-x  2 ludovic ludovic    4096 2009-12-09 22:34 Videos
drwxr-xr-x  5 ludovic ludovic    4096 2009-12-10 02:23 Web
drwxr-xr-x  3 ludovic ludovic    4096 2009-12-10 02:14 workspace
-rwxr-xr-x  1 ludovic ludovic   38341 2009-12-12 08:27 .xsession-errors
-rwxr-xr-x  1 ludovic ludovic   21589 2009-12-11 00:12 .xsession-errors.old



```

---

### Post by mikewhatever on 2009-12-12
You seem to be running as root, and applying permissions to /home/ludovic, no wonder it doesn't work.

---

### Post by ludydoo on 2009-12-12
I'm not sure I understand.. I'm a little new to all this. By the way, what should be the permissions for /home/ ?

---

### Post by mikewhatever on 2009-12-12
Permissions in /home are 755 with the ownership of the user, the same applies to most of the files and folders inside your home directory. The output of ls you posted above looks OK with the exception of .gvfs. Try to logout and then login.

As a matter of fact, chmod'ing your home to 700 should not have any bad affect. It makes it sort of more private, but nothing else. You may not be able to access launchers on the Desktop, cause you are not the owner of that home directory, perhaps another user.

---

### Post by ludydoo on 2009-12-12
Thank you very much man

I chmoded 755 /home/  and it worked, as you said

Thanks for the dedication and explanations

---

### Post by mikewhatever on 2009-12-13
I created a new account named guest, so that all permissions are the default ones. Here is the output, in case you'd like to fine tune permissions:
```
/home/guest
total 140
drwxr-xr-x 24 guest guest 4096 2009-11-17 17:39 .
drwxr-xr-x  4 root  root  4096 2009-11-11 12:25 ..
drwx------  3 guest guest 4096 2009-11-17 17:37 .adobe
-rw-r--r--  1 guest guest  220 2009-11-11 12:25 .bash_logout
-rw-r--r--  1 guest guest 3115 2009-11-11 12:25 .bashrc
drwxr-xr-x  5 guest guest 4096 2009-11-17 15:31 .config
drwx------  3 guest guest 4096 2009-11-17 15:31 .dbus
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Desktop
-rw-------  1 guest guest   28 2009-11-17 17:19 .dmrc
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Documents
-rw-------  1 guest guest   16 2009-11-17 15:31 .esd_auth
-rw-r--r--  1 guest guest  357 2009-11-11 12:25 examples.desktop
drwx------  4 guest guest 4096 2009-11-17 17:19 .gconf
drwx------  2 guest guest 4096 2009-11-17 17:39 .gconfd
drwx------  5 guest guest 4096 2009-11-17 17:39 .gnome2
drwx------  2 guest guest 4096 2009-11-17 15:31 .gnome2_private
drwx------  2 guest guest 4096 2009-11-17 15:31 .gnupg
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 .gstreamer-0.10
-rw-r--r--  1 guest guest  108 2009-11-17 17:19 .gtk-bookmarks
drwx------  2 guest guest 4096 2009-11-17 15:31 .gvfs
-rw-------  1 guest guest  322 2009-11-17 17:19 .ICEauthority
drwx------  3 guest guest 4096 2009-11-17 15:31 .local
drwx------  3 guest guest 4096 2009-11-17 17:37 .macromedia
drwx------  4 guest guest 4096 2009-11-17 17:37 .mozilla
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Music
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Pictures
-rw-r--r--  1 guest guest  675 2009-11-11 12:25 .profile
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Public
drwx------  2 guest guest 4096 2009-11-17 15:31 .pulse
-rw-------  1 guest guest  256 2009-11-17 15:31 .pulse-cookie
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Templates
drwx------  2 guest guest 4096 2009-11-17 15:31 .update-notifier
drwxr-xr-x  2 guest guest 4096 2009-11-17 15:31 Videos
-rw-r--r--  1 guest guest 6303 2009-11-17 17:39 .xsession-errors

```

---

