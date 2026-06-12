---
title: "Cannot Open Folders Normally"
date: 2011-08-11
forum: General Help
---

### Post by DWXTG on 2011-08-11
When I try to open my home folder, the file browser (Nautilus, I believe) freezes and refuses to respond. This also happens if I attempt to open any folders in my home folder (indirectly, using shortcuts), and any folder in my desktop.
However, if I go to my console and type "sudo nautilus", it opens up my root folder, from which I can find my home folder and access anything, and it never freezes. Does anyone know what is causing this, and how to fix it?
I don't think it's anything to do with nautilus itself, because I can browse files using the roundabout console way, but I really don't know. I am a linux and ubuntu newbie, so any help is appreciated.

---

### Post by papibe on 2011-08-11
Maybe if you launch Nautilus from the CLI, it would display more information or errors:
```
$ nautilus
```
Regards.

---

### Post by DWXTG on 2011-08-12
When I type in nautilus by itself, nothing happens. It just accepts the line then displays nothing. Is it supposed to do that if it's working?
**EDIT**
I tried opening it as the super user (sudo) at got this as a reply:
```

Initializing nautilus-gdu extension

** (nautilus:4468): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '4468'

(nautilus:4468): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```
It then opened my root folder like before and is for some reason working smoothly.
I can't actually open it any other way though.

---

### Post by papibe on 2011-08-12
Could you post the result of these commands:
```
$ ls -l /usr/bin/nautilus

$ ls -l .gnome2/nautilus-scripts
```
Regards.

---

### Post by DWXTG on 2011-08-12
The results were as follows :

```
-rwxr-xr-x 1 root root 1697372 2011-04-08 16:40 /usr/bin/nautilus

```

and 

```
total 0
```

---

