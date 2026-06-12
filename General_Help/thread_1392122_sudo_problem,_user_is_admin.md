---
title: "sudo problem, user is admin"
date: 2010-01-27
forum: General Help
---

### Post by stonehinge03 on 2010-01-27
I have an ubuntu 9.10 machine that had one user created during the install and two new users made afterwards.  The original user can sudo, but the other two can't.  I researched the problem and found that most people just added the non-sudo users to the admin group.  I did that but it didn't help.  I did not fool with the /etc/sudoers file.  It looks just the way it should with "%admin (ALL) ALL" in there.

What could the problem be?  I did notice that the original user that can sudo has a file ~/.ssh/known_hosts which the ones that can't sudo don't have.  I don't know why that is but it is the only difference that I can see between the original user and the new ones.

---

### Post by stonehinge03 on 2010-01-27
bump

---

### Post by sisco311 on 2010-01-27
Please post th eoutput of:
```
cat /etc/group | grep ^admin
```
and
```
sudo cat /etc/sudoers
```

---

### Post by stonehinge03 on 2010-01-27
server@server:~$ cat /etc/group | grep ^admin
admin:x:121:server,ericg
server@server:~$ sudo cat /etc/sudoers
[sudo] password for server:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

****************************************************************

ericg is the username that will not sudo when it gives the correct password while server can.

---

### Post by sisco311 on 2010-01-27
Did you log out & log back in ericg after adding it to the admin group?

Can you use pkexec as ericg:
```
pkexec echo "pkexec works"
```?

---

### Post by stonehinge03 on 2010-01-27
login as: ericg
ericg@server's password:
Linux server 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Wed Jan 27 17:57:24 2010 from home
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ericg@server:~$ sudo cat /etc/sudoers
[sudo] password for ericg:
Sorry, try again.
[sudo] password for ericg:
Sorry, try again.
[sudo] password for ericg:
Sorry, try again.
sudo: 3 incorrect password attempts
ericg@server:~$

*****************************************************************
I can get different output about the sudoers file but this way it acts like I'm giving it the wrong password.

---

### Post by stonehinge03 on 2010-01-27
> **sisco311 said:**
> Did you log out ericg after adding it to the admin group?

Can you use pkexec as ericg:
```
pkexec echo "pkexec works"
```?

*****************************************************************
ericg@server:~$ pkexec echo "pkexec works"
Authorization requires authentication but no authentication was found.
ericg@server:~$
***************************************************************

---

### Post by sisco311 on 2010-01-27
sudo prompts for the user's password. Are you sure that the password you enter is correct? Did you try to change the user's password?

---

### Post by stonehinge03 on 2010-01-27
> **sisco311 said:**
> sudo prompts for the user's password. Are you sure that the password you enter is correct? Did you try to change the user's password?

I added ericg (the one that can't sudo)to the admin group and restarted the machine.  He still couldn't sudo, I didn't change any passwords and I am sure I am typing it in right.  But the thing is that server was a user created during the install process and ericg was made after.  Look at the differences in their home directories.  *****************************************************************

root@server:/home/server# ls -lga /home/server
ls: cannot access /home/server/.gvfs: Permission denied
total 260
drwxr-xr-x 35 server  4096 2010-01-27 16:55 .
drwxr-xr-x  5 root    4096 2010-01-25 08:25 ..
-rw-r--r--  1 server    11 2010-01-27 15:10 1
-rw-r--r--  1 server    11 2010-01-27 15:10 2
drwx------  3 server  4096 2010-01-24 15:16 .adobe
-rw-------  1 server  8955 2010-01-27 16:53 .bash_history
-rw-r--r--  1 server   220 2010-01-22 13:52 .bash_logout
-rwxr-xr-x  1 server  3115 2010-01-25 17:02 .bashrc
-rw-r--r--  1 server  3179 2010-01-25 12:50 .bashrc~
drwxr-xr-x  4 server  4096 2010-01-25 08:01 .cache
drwxr-xr-x  6 server  4096 2010-01-25 01:28 .config
drwx------  3 server  4096 2010-01-22 08:57 .dbus
drwxr-xr-x  2 server  4096 2010-01-26 02:06 Desktop
-rw-------  1 server     2 2010-01-24 13:13 .dmrc
drwxr-xr-x  2 server  4096 2010-01-25 05:24 Documents
-rw-------  1 server    16 2010-01-22 08:57 .esd_auth
-rw-r--r--  1 server   357 2010-01-22 13:52 examples.desktop
drwxr-xr-x  2 server  4096 2010-01-24 15:15 .fontconfig
drwx------  5 server  4096 2010-01-27 16:55 .gconf
drwx------  2 server  4096 2010-01-27 17:15 .gconfd
-rw-r-----  1 server     0 2010-01-26 00:27 .gksu.lock
drwx------ 10 server  4096 2010-01-27 15:05 .gnome2
drwx------  2 server  4096 2010-01-22 08:57 .gnome2_private
drwx------  2 server  4096 2010-01-27 16:54 .gnupg
drwxr-xr-x  2 server  4096 2010-01-25 01:07 .gstreamer-0.10
-rw-r--r--  1 server   112 2010-01-27 16:55 .gtk-bookmarks
d?????????  ? ?          ?                ? .gvfs
-rw-------  1 server  5700 2010-01-27 16:54 .ICEauthority
drwxr-xr-x  2 server  4096 2010-01-27 14:57 .icons
drwx------  3 server  4096 2010-01-24 15:15 .local
-rw-r--r--  1 server   120 2010-01-25 12:06 logfile
drwx------  3 server  4096 2010-01-24 15:16 .macromedia
drwx------  4 server  4096 2010-01-22 18:58 .mozilla
drwxr-xr-x  2 server  4096 2010-01-22 08:57 Music
drwx------  4 server  4096 2010-01-26 15:32 .mysqlgui
drwxr-xr-x  3 server  4096 2010-01-22 08:58 .nautilus
drwxr-xr-x  3 server  4096 2010-01-26 02:10 .openoffice.org
-rw-r--r--  1 server  1522 2010-01-25 20:47 .pgadmin3
drwxr-xr-x  2 server  4096 2010-01-22 08:57 Pictures
-rwxr-xr-x  1 server   741 2010-01-25 13:33 .profile
drwxr-xr-x  2 server  4096 2010-01-22 08:57 Public
drwx------  2 server  4096 2010-01-27 16:54 .pulse
-rw-------  1 server   256 2010-01-22 08:57 .pulse-cookie
-rw-------  1 server   293 2010-01-26 02:10 .recently-used
-rw-------  1 server 30934 2010-01-27 14:58 .recently-used.xbel
drwx------  2 server  4096 2010-01-25 08:01 .ssh
-rw-r--r--  1 server     0 2010-01-22 18:59 .sudo_as_admin_successful
drwxr-xr-x  2 server  4096 2010-01-22 08:57 Templates
-rw-r--r--  1 server   464 2010-01-26 14:54 test.pgn
drwxr-xr-x  2 server  4096 2010-01-27 14:57 .themes
drwx------  4 server  4096 2010-01-27 14:57 .thumbnails
drwxr-xr-x  2 server  4096 2010-01-24 13:59 .update-manager-core
drwx------  2 server  4096 2010-01-22 08:58 .update-notifier
drwxr-xr-x  2 server  4096 2010-01-22 08:57 Videos
drwx------  2 server  4096 2010-01-25 05:11 .w3m
-rw-------  1 server  3184 2010-01-27 19:00 .xsession-errors
-rw-------  1 server  4455 2010-01-27 16:53 .xsession-errors.old
root@server:/home/server# ls -lga /home/ericg
total 48
drwxr-xr-x 5 ericg 4096 2010-01-27 16:14 .
drwxr-xr-x 5 root  4096 2010-01-25 08:25 ..
-rw------- 1 ericg 1732 2010-01-27 17:52 .bash_history
-rw-r--r-- 1 ericg  220 2010-01-25 08:25 .bash_logout
-rw-r--r-- 1 ericg 3180 2010-01-25 08:25 .bashrc
drwxr-xr-x 2 ericg 4096 2010-01-25 08:33 .cache
-rw-r--r-- 1 ericg  167 2010-01-25 08:25 examples.desktop
-rw------- 1 ericg   49 2010-01-27 16:10 .lesshst
-rw------- 1 ericg  505 2010-01-27 15:28 .mysql_history
-rw-r--r-- 1 ericg  709 2010-01-27 18:10 .profile
drwx------ 2 ericg 4096 2010-01-27 16:53 .ssh
drwxr-xr-x 4 ericg 4096 2010-01-25 09:57 Work
***************************************************************

---

### Post by stonehinge03 on 2010-01-27
I don't know what to say about .gvfs.  If root doesn't have permissions to see it who does?  Some of the differences are because of me but one that I thought might matter is that server has a .ssh directory with a couple of files.  ericg doesn't have that.

---

### Post by sisco311 on 2010-01-27
> **stonehinge03 said:**
> I don't know what to say about .gvfs.  If root doesn't have permissions to see it who does?  Some of the differences are because of me but one that I thought might matter is that server has a .ssh directory with a couple of files.  ericg doesn't have that.

.gvfs is a virtual filesystem, don't worry about it.

Well, the user is in the admin group & the sudoers file looks okay. I don't see why you can't use sudo. I would try to change the user's password (sorry, I have no other idea).

---

### Post by stonehinge03 on 2010-01-27
> **sisco311 said:**
> .gvfs is a virtual filesystem, don't worry about it.

Well, the user is in the admin group & the sudoers file looks okay. I don't see why you can't use sudo. I would try to change the user's password (sorry, I have no other idea).

You mean the one that can't sudo, right.  Now that won't affect the root password, the one that sudo wants.  Do you think I ought to change root's too?

This is that ssh file:

```

server@server:~$ ls -lga ~/.ssh
total 12
drwx------  2 server 4096 2010-01-25 08:01 .
drwxr-xr-x 35 server 4096 2010-01-27 16:55 ..
-rw-r--r--  1 server  884 2010-01-25 08:01 known_hosts

```

---

### Post by sisco311 on 2010-01-27
> **stonehinge03 said:**
> You mean the one that can't sudo, right.  Now that won't affect the root password, the one that sudo wants.  Do you think I ought to change root's too?


sudo needs YOUR USER (ericg) password, and not the root account password.

---

### Post by theozzlives on 2010-01-27
From personal experience, I created a user, then changed it to admin. It wasn't in the sudoers file. I had to delete the user, home directory and start from scratch.

---

### Post by stonehinge03 on 2010-01-27
> **sisco311 said:**
> .gvfs is a virtual filesystem, don't worry about it.

Well, the user is in the admin group & the sudoers file looks okay. I don't see why you can't use sudo. I would try to change the user's password (sorry, I have no other idea).


Well you got it!  Good unix instincts.  The account that has it's original password can't sudo but the other one can.
```


mikeu@server:~$ sudo su root
[sudo] password for mikeu:
mikeu is not in the sudoers file.  This incident will be reported.

ericg@server:~$ sudo su root
[sudo] password for ericg:

```

Now I guess I am a real idiot but I seem to remember using the root password for sudo, not one's own.  But one's own gave the bit about not being in the sudoers file....until changed!

That is amazing and weird.  I got the passwords confused because we used to  use "su root" instead of sudo and I have server and root's passwords being the same.

---

