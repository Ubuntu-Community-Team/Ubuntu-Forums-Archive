---
title: "Nautilus Hanging"
date: 2012-07-10
forum: General Help
---

### Post by balasankarc on 2012-07-10
Hi all,
My problem is that my nautilus hangs often... the icons in desktop will disappear and right click menu in desktop will not work. It comes back to normal if i somehow open a nautilus window (either through Cairo Dock or through terminal (by command - nautilus).

Please help me.

---

### Post by hal8000 on 2012-07-10
From the terminal, start nautilus with this command:

nautilus


The terminal will output extra information that can be used to find
the problem

---

### Post by balasankarc on 2012-07-11
The output of nautilus in terminal is 

> ** Message: Initializing gksu extension...

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:11287): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed


---

### Post by Syndacate on 2012-07-18
I'm having similar issues, although mine isn't under the same conditions.  It may or may not be related.

```
:~$ nautilus &
[1] 8355
:~$ Nautilus-Share-Message: Called "net usershare info" but it failed: 'net 
usershare' returned error 255: net usershare: cannot open usershare directory 
/var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:8355): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed
```

Not sure why it's talking about samba shares, I have/use none.

This just happens sometimes and nautilus shuts off, it'll open back up if I open my home folder, (all icons come back), but sometimes it'll just close again.  Not sure why.

---

