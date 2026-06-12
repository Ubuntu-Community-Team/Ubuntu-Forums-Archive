---
title: "Ubuntu problem - files gone, email gone, etc, gone"
date: 2011-01-29
forum: General Help
---

### Post by tokunbo on 2011-01-29
good day people,

I have been using Ubuntu for about a month now(dual boot with Windows XP professional), and things have been going ok, until this morning. I first booted into Ubuntu, then later(after like an hour) did a restart and booted into windows to do something(which didnt take 20-minutes) and then back into Ubuntu.

I logged in as usual(same uusername and pass as before), but I noticed that my desktop(all the files there were gone). I had also installed and been using Evolution mail as my client, but now, clicking evolution prompts me with the new email account / setup screen. All the softwares i had installed in ubuntu are still there, but my files(desktop, mail, even my downloaded files in my download DIR and those in the documents DIR) are all gone. Even the former IP settings on my NICs(static) are gone.

Please can someone help with this problem. It looks as if I am loggin into a clean install of ubuntu for the first ttime. How do I get my former login/session and files back.

Pls assist
thanks
Toks

---

### Post by ajgreeny on 2011-01-29
Can we see the output of commands ```
ls -la /home
```then assuming that your expected username appears, ```
ls -la /home/username
```That will hopefully show that your home folders are still there.  We then have to figure out why they are not showing and why all your configurations appear to have vanished.

You can also possibly find everything if you use nautilus as root with ```
gksu nautilus
```and search in **File System/home/user**, but again we need to figure out why your home is not being used.

---

### Post by tokunbo on 2011-01-29
hello sir,

1st command:
[HTML]tokunbo@ubuntu:~$ ls -la /home
total 12
drwxr-xr-x  3 root    root    4096 2011-01-29 07:10 .
drwxr-xr-x 23 root    root    4096 2011-01-29 08:35 ..
drwxr-xr-x 33 tokunbo tokunbo 4096 2011-01-29 09:09 tokunbo
tokunbo@ubuntu:~$ 
[/HTML]2nd command
[HTML]
drwxr-xr-x 33 tokunbo tokunbo  4096 2011-01-29 09:09 .
drwxr-xr-x  3 root    root     4096 2011-01-29 07:10 ..
drwx------  3 tokunbo tokunbo  4096 2011-01-29 07:15 .adobe
-rw-------  1 tokunbo tokunbo   777 2011-01-29 09:12 .bash_history
drwx------  4 tokunbo tokunbo  4096 2011-01-29 08:35 .cache
drwxr-xr-x  7 tokunbo tokunbo  4096 2011-01-29 08:41 .config
drwx------  3 tokunbo tokunbo  4096 2011-01-29 07:20 .dbus
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 09:29 Desktop
-rw-r--r--  1 tokunbo tokunbo    41 2011-01-29 08:35 .dmrc
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Documents
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Downloads
-rw-------  1 tokunbo tokunbo    16 2011-01-29 07:18 .esd_auth
drwxr-xr-x  7 tokunbo tokunbo  4096 2011-01-29 07:34 .evolution
drwx------  5 tokunbo tokunbo  4096 2011-01-29 08:35 .gconf
drwx------  2 tokunbo tokunbo  4096 2011-01-29 09:09 .gconfd
-rw-r-----  1 tokunbo tokunbo     0 2011-01-29 07:37 .gksu.lock
drwx------  6 tokunbo tokunbo  4096 2011-01-29 08:30 .gnome2
drwx------  2 tokunbo tokunbo  4096 2011-01-29 07:20 .gnome2_private
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 08:42 .gstreamer-0.10
-rw-r--r--  1 tokunbo tokunbo   147 2011-01-29 08:35 .gtk-bookmarks
dr-x------  2 tokunbo tokunbo     0 2011-01-29 08:35 .gvfs
-rw-------  1 tokunbo tokunbo   954 2011-01-29 08:35 .ICEauthority
drwx------  3 tokunbo tokunbo  4096 2011-01-29 07:22 .local
drwx------  3 tokunbo tokunbo  4096 2011-01-29 07:15 .macromedia
drwx------  4 tokunbo tokunbo  4096 2011-01-29 07:21 .mozilla
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Music
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 .nautilus
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:48 nokia
drwxr-xr-x  3 tokunbo tokunbo  4096 2011-01-29 09:09 .openoffice.org
drwxr-xr--  2 tokunbo tokunbo  4096 2011-01-29 07:46 output
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Pictures
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Public
drwx------  2 tokunbo tokunbo  4096 2011-01-29 08:35 .pulse
-rw-------  1 tokunbo tokunbo   256 2011-01-29 07:14 .pulse-cookie
-rw-------  1 tokunbo tokunbo   909 2011-01-29 09:09 .recently-used.xbel
-rw-r--r--  1 tokunbo tokunbo     0 2011-01-29 07:13 .sudo_as_admin_successful
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Templates
drwx------  3 tokunbo tokunbo  4096 2011-01-29 09:09 .thumbnails
drwx------  2 tokunbo tokunbo  4096 2011-01-29 07:21 .update-notifier
drwxr-xr-x  2 tokunbo tokunbo  4096 2011-01-29 07:20 Videos
drwxr-xr--  2 tokunbo tokunbo  4096 2011-01-29 07:46 xls
-rw-------  1 tokunbo tokunbo 12231 2011-01-29 09:27 .xsession-errors
-rw-------  1 tokunbo tokunbo 22048 2011-01-29 08:30 .xsession-errors.old
tokunbo@ubuntu:~$ 

[/HTML]3rd command: this error message is displayed many times
[HTML]
nautilus:2322): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

[/HTML]Pls note that the Desktop DIR is empty.

I even checked the my firefox bookmarks, they are gone too. Pls note that besides root, I am the only user on the desktop and im logged in with the same username/pass I had used when things were working fine.

thanks
Toks

---

### Post by TheHackOps on 2011-01-29
See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)

---

### Post by tokunbo on 2011-01-29
@TheHackerOps
please how am I supposed to use GCONF to recover my lost files?

---

### Post by ajgreeny on 2011-01-29
This is baffling, but try booting into the recovery mode from grub, then run ```
sudo chown -R tokunbo:tokunbo /home/tokunbo
```then ```
reboot
``` and try logging in as user again.

It looks as if all your folders are still in your old home, but at the moment I can't tell about the files in those folders, so try 
```
ls -la /home/tokunbo/Documents
```to see if you can see any named files you recognise.

---

