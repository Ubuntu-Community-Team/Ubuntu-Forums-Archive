---
title: "problems with root"
date: 2010-01-21
forum: General Help
---

### Post by W.Y.N.F.S on 2010-01-21
system: superUbuntu
I edited /etc/fstab,
now my ntfs drive mounts automaticaly but with permissions rwxr-x--x owner:root.
I want to change it to rwxrwx-- or change owner,
I login as root and...
chmod 770 does nothing,
chown deniss also does nothing,
I try to start filebrowser to change permissions in GUI, but dolphin and nautilus return errors and refuse to start.
 
under user everything works, why I can`t do the same things but under root?

---

### Post by mcduck on 2010-01-21
You have to edit the /etc/fstb again to set the right permissions there. Chown/Chmod can't work on NTFS file systems because NTFS doesn't support ownerships/permissions as they are used on Linux/Unix systems.

What comes to Nautilus and Dolphin refusing to start as root, what exact command are you trying to use to start them? And what error do you get? (not that running the file browser would help you in this case anyway, for the reasons mentioned above.. ;))

---

### Post by W.Y.N.F.S on 2010-01-21
Thank you, now I see that filebrowsers will not help me to change permissions for that drive.
but anyway. I start them simply by typing names: nautilus or dolphin. 
now I can`t say what exact errors it was, i will copy them later and post here.

---

### Post by W.Y.N.F.S on 2010-01-22
Here it is
```

deniss@deniss-desktop:~$ su root
Password: 
root@deniss-desktop:/home/deniss# nautilus

(nautilus:4285): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


(nautilus:4285): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf warning: failure listing pairs in `/apps/nautilus/preferences': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/file_views': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/background': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/lockdown': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/desktop': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/icon_view': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/desktop-metadata': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:4285): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:4285): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

(nautilus:4285): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:4285): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.
root@deniss-desktop:/home/deniss# 

```

and for user it starts:

```

root@deniss-desktop:/home/deniss# su deniss
deniss@deniss-desktop:~$ nautilus
/home/deniss/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:48: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/deniss/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:49: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/deniss/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:50: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

(nautilus:4399): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
deniss@deniss-desktop:~$ 

```

---

### Post by mcduck on 2010-01-23
have you tried with "gksudo nautilus"?

---

### Post by W.Y.N.F.S on 2010-01-25
gksudo works under user.
does it give root privilegies?

---

### Post by D3V11 on 2010-01-25
> **W.Y.N.F.S said:**
> gksudo works under user.
does it give root privilegies?

yes, and it's recommended you only use gksudo when opening graphical applications as opposed to sudo. using sudo for graphical applications can cause file damage.

---

### Post by lisati on 2010-01-25
> **W.Y.N.F.S said:**
> gksudo works under user.
does it give root privilegies?

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by amsterdamharu on 2010-01-25
Ok, what's in the /etc/fstab? root is the only one that automount but users can write if you put the correct value in /etc/fstab

/dev/sda2    /media/backup    ntfs    nouser,noauto,noexec,ro    0    0

nouser means that normal users cannot mount or unmount it, change to user and normal users can mount and unmount it

noauto means that it is not automatically mounted but can be mounted manually see nouser/user who can mount/unmount it. auto means it's automatically mounted but can still be unmounted

noexec means that none of the files have execute permissions when mounted. (I see a pattern here what would exec mean?)

ro read only this is default so the partition is mounted read only that means you cannot write to it (not sure if even root can) change this to rw and you can read write to it.


Hope this helped.

---

### Post by W.Y.N.F.S on 2010-01-26
here is my fstab line:
/dev/sdb1       /media/LEVIATHAN  auto   rw,user,auto,exec,utf8 0       0

everything seems to be right, but...

```
deniss@deniss-desktop:~$ ls -l /media/LEVIATHAN/
total 32
drwxr-xr-x 5 root root 32768 2010-01-16 16:53 Docs
deniss@deniss-desktop:~$ 
```

---

### Post by amsterdamharu on 2010-01-26
I have the same setup here, but can mount, unmount and write without problem. As a normal user can you try this?

```

umount /media/LEVIATHAN
mount /media/LEVIATHAN
echo "write this to ntfs" >  /media/LEVIATHAN/testwrite
more  /media/LEVIATHAN/testwrite

```

[edit]You might get an error because windows has not been closed and there is an "unclean" log that causes linux not to mount. Change the fstab line to:
/dev/sdb1       /media/LEVIATHAN  auto   rw,user,auto,exec,utf8,**force** 0       0

And try again

---

### Post by mcduck on 2010-01-26
> **W.Y.N.F.S said:**
> here is my fstab line:
/dev/sdb1       /media/LEVIATHAN  auto   rw,user,auto,exec,utf8 0       0

everything seems to be right, but...

```
deniss@deniss-desktop:~$ ls -l /media/LEVIATHAN/
total 32
drwxr-xr-x 5 root root 32768 2010-01-16 16:53 Docs
deniss@deniss-desktop:~$ 
```

Try defining user & group ID's and file/directory masks in fstab as well.
```

/dev/sdb1       /media/LEVIATHAN  auto   rw,uid=1000,gid=100,dmask=027,fmask=137,user,auto,exec,utf8 0       0
```

(I think you could also use gid=46, since that's the plugdev group used to give usrs permissions to removable drives..)

---

### Post by W.Y.N.F.S on 2010-01-28
> **mcduck said:**
> Try defining user & group ID's and file/directory masks in fstab as well.
```

/dev/sdb1       /media/LEVIATHAN  auto   rw,uid=1000,gid=100,dmask=027,fmask=137,user,auto,exec,utf8 0       0
```

(I think you could also use gid=46, since that's the plugdev group used to give usrs permissions to removable drives..)

Thank you, this solved the problem.

```
deniss@deniss-desktop:~$ ls -l /media/LEVIATHAN/
total 32
drwxr-x--- 5 deniss users 32768 2010-01-16 16:53 Docs
deniss@deniss-desktop:~$ 
```

edit:
still only root can unmount this drive. this is ok for me, but interesting to know if it can be changed

---

