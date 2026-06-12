---
title: "Help with Error Message"
date: 2010-02-17
forum: General Help
---

### Post by strange_cathect on 2010-02-17
Can anyone help me figure out what this means? When trying to open nautilus as root, I get the following message:

> xxx@xxx-desktop:~$ sudo nautillus
[sudo] password for xxx: 
sudo: nautillus: command not found
xxx@xxx-desktop:~$ sudo nautilus

(nautilus:3917): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3917): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3917): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3917): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-clamscan extension
Fontconfig error: Cannot load default config file

** (nautilus:3917): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

--- Hash table keys for warning below:
--> xxx
--> root
--> inode/directory
--> l2050
--> l2049
--> staff
--> xxx

(nautilus:3917): Eel-WARNING **: "unique eel_ref_str" hash table still has 7 elements at quit time (keys above)

(nautilus:3917): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 12 elements at quit time
Shutting down nautilus-gdu extension

---

### Post by philinux on 2010-02-17
> **strange_cathect said:**
> Can anyone help me figure out what this means? When trying to open nautilus as root, I get the following message:

```
gksudo nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by strange_cathect on 2010-02-17
Thanks for this.

I used gksudo to open nautilus and also receive an error:
> 
(nautilus:4195): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:4195): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4195): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4195): WARNING **: No marshaller for signature of signal 'ShareCreateError'

Have I messed up something by using sudo?

---

### Post by ajgreeny on 2010-02-17
That seems to be s common error showing in all attempts to get nautilus up and running, though it runs perfectly well as far as I can see.  There are many bugs in launchpad relating to this and other similar problems.  It is not a specific ubuntu problem, but a general gnome 2.28.1 error.  Hopefully it will disappear in lucid in a couple of months time.

If you look in your hidden ~/.xsession-errors file, you will probably find quite a lot of similar errors showing.  I have given up worrying about them for the time being, and just carry on using the system, which still works great.  Incidentally you will probably get the same "eel critical" error showing if you start nautilus as user with command **nautilus** in terminal; try it and see.

---

### Post by strange_cathect on 2010-02-17
Thanks for you sage wisdom; this yank appreciates it.

---

