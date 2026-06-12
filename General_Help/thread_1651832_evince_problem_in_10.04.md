---
title: "evince problem in 10.04"
date: 2010-12-23
forum: General Help
---

### Post by apexofservice on 2010-12-23
evince fails to open pdfs or dvis or other files.  
```

apexofservice@mycomputer$ evince file.pdf &
[1] 2052
 
(evince:2052): EvinceDocument-WARNING **: libstdc++.so.6: failed to map segment from shared object: Permission denied

(evince:2052): EvinceDocument-WARNING **: Cannot load backend 'pdfdocument' since file '/usr/lib/evince/2/backends/libpdfdocument.so' cannot be read.

(evince:2052): EvinceDocument-WARNING **: libstdc++.so.6: failed to map segment from shared object: Permission denied

(evince:2052): EvinceDocument-WARNING **: Cannot load backend 'pdfdocument' since file '/usr/lib/evince/2/backends/libpdfdocument.so' cannot be read.

[1]+  Done                    evince thesis_bib.pdf
```

I can get evince to run if I'm root, but of course I don't want to have to do this normally.  I guess this means that permissions are wrong on libpdfdocument.so and some other .so files in that directory.  How would this have happened?  Should I change the permissions "by hand" or reinstall something?

Also, running evince as root yields some other warnings and gconf errors (which maybe are related):

```

apexofservice@mycomputer$ sudo evince file.pdf

** (evince:2132): WARNING **: Failed to connect to the session bus: /bin/dbus-launch terminated abnormally without any error message

** (evince:2132): WARNING **: Error connection to DBus: /bin/dbus-launch terminated abnormally without any error message


** (evince:2132): WARNING **: Error connecting to D-Bus: /bin/dbus-launch terminated abnormally without any error message

** (evince:2132): WARNING **: Setting attribute metadata::evince::sidebar_visibility not supported
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)

```


What I'm experiencing seems to be the same issue reported here: 

[http://ubuntuforums.org/showthread.php?t=1171394](http://ubuntuforums.org/showthread.php?t=1171394)

That thread is 'closed', so I can't post there, but I don't see any solution listed. 

Can anyone help?

---

### Post by gordintoronto on 2010-12-23
You could install acroread (Adobe's PDF reader) using synaptic.

---

### Post by apexofservice on 2011-01-03
Thanks for the suggestion about installing adobe software, but this thread is about fixing an issue with evince.

This issue is especially disheartening because evince seems to work okay from the gui.  That is, on one of the gnome panels I can click "Places >> Documents >> Some_Folder >> some_pdf_file.pdf" and evince opens and displays the file.  But typing "evince filename" in a gnome-terminal produces the errors I reported above.

Anybody have any ideas about how to fix this issue with Ubuntu 10.04 and evince?


Edit: 

Some further information about permissions on those library files:
```

$ls -la /usr/lib/evince/2/backends/
total 400
drwxr-xr-x 2 root root   4096 2011-01-03 18:29 .
drwxr-xr-x 3 root root   4096 2011-01-03 18:29 ..
-rw-r--r-- 1 root root   3412 2010-07-07 07:37 comicsdocument.evince-backend
-rw-r--r-- 1 root root   1779 2010-07-07 07:37 djvudocument.evince-backend
-rw-r--r-- 1 root root   3320 2010-07-07 07:37 dvidocument.evince-backend
-rw-r--r-- 1 root root   3632 2010-07-07 07:37 impressdocument.evince-backend
-rw-r--r-- 1 root root  17668 2010-07-07 07:38 libcomicsdocument.so
-rw-r--r-- 1 root root  25804 2010-07-07 07:38 libdjvudocument.so
-rw-r--r-- 1 root root 117672 2010-07-07 07:38 libdvidocument.so
-rw-r--r-- 1 root root  54532 2010-07-07 07:38 libimpressdocument.so
-rw-r--r-- 1 root root  54532 2010-07-07 07:38 libpdfdocument.so
-rw-r--r-- 1 root root   9424 2010-07-07 07:38 libpixbufdocument.so
-rw-r--r-- 1 root root  13516 2010-07-07 07:38 libpsdocument.so
-rw-r--r-- 1 root root  39404 2010-07-07 07:38 libtiffdocument.so
-rw-r--r-- 1 root root   3457 2010-07-07 07:37 pdfdocument.evince-backend
-rw-r--r-- 1 root root    409 2010-07-07 07:37 pixbufdocument.evince-backend
-rw-r--r-- 1 root root   4401 2010-07-07 07:37 psdocument.evince-backend
-rw-r--r-- 1 root root     88 2010-07-07 07:37 tiffdocument.evince-backend

```

To me, these seem like the expected permissions: rw for root, r for everyone else.  Can anyone help?

---

### Post by tomkro on 2011-02-28
Recently I got problems printing with evince and it was a simple AppArmor restriction. Never found someone with the same bug, but i found similar bugs solved by the same fix.

Try to make a link under /etc/apparmor.d/disable for the usr.bin.evince file that is located at /etc/apparmor.d/usr.bin.evince . Don't know if it will solve anything, but don't hurt trying.

---

### Post by mabinty on 2011-04-13
Hi!

had exactly the same problem. the following did the trick for me:

```

sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable
sudo /etc/init.d/apparmor restart

```aram

---

### Post by hardik.soni on 2011-09-17
Thanks buddy,
it also solved my problem.
As such i was facing the same problem that wont able to open the Evince as the root user.


Thanks thanks man...

:guitar:

---

