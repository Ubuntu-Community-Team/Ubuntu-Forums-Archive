---
title: "nautilus errors in terminal"
date: 2010-02-08
forum: General Help
---

### Post by robembra on 2010-02-08
Hi,

Im running the following command from the terminal: **gksudo nautilus** and get the following error?

```
(nautilus:2796): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2796): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2796): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2796): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

When I run **gksu nautilus** i get this error:
```

(nautilus:2840): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```

Also can anyone help me make a desktop shortcut to run nautilus so I can drag and drop files with root perms and not have to auth all the time.

Many Thanks.... :p

---

### Post by audiomick on 2010-02-08
Hi,
I get the following errors from "gksu nautlius"
```
mick@ubuntu-desktop:~$ gksu nautilus

** (nautilus:4113): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4113): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4113): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Initializing nautilus-image-converter extension

```and I have seen a number of other people with the same or similar. It seems to be "normal".

Can't help with the shortcut, sorry.

---

### Post by robembra on 2010-02-08
Thanks audiomick,

Its strange didnt have this problem until i installed LAMP...well anyways aslong as everything is ok no worries.

Thanks again!!!

---

### Post by robembra on 2010-02-08
I have just notices that when I run **gksu nautilus** take me to root dir, it doesnt show up my hard drives and the default view and zoom is wrong....any ideas???

Thanks again

---

### Post by oldos2er on 2010-02-08
That happens because you're using the root account's settings, not your user settings.

---

### Post by afrodeity on 2010-02-08
My nautilus is totally unresponsive. Get the same errors. I've tried deleting .nautilus, .gconf and .gnome, but nothing. Any ideas what could be wrong?

---

### Post by robembra on 2010-02-08
> **oldos2er said:**
> That happens because you're using the root account's settings, not your user settings.

Thanks...i have changed to **gksu -u bert nautilus** i still get a error:

```
(nautilus:2568): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

Is this the correct command to be able to view & drag and drop files to any location?

Thanks again!

---

### Post by afrodeity on 2010-02-08
History of attempts to fix the problem [http://ubuntuforums.org/showthread.php?t=1399819](http://ubuntuforums.org/showthread.php?t=1399819)

---

