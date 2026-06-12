---
title: "Nautilus errors"
date: 2010-06-06
forum: General Help
---

### Post by fndtn357 on 2010-06-06
I am using Ubuntu 9.10 and these errors always show up in the terminal window when I open and run Nautilus (I use the command "sudo nautilus").

Can someone tell me how to decipher and possibly solve this?


(nautilus:32273): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-dropbox 0.6.2

** (nautilus:32273): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:32273): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:32273): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:32273): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:32273): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:32273): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (nautilus:32273): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files
Shutting down nautilus-gdu extension

--- Hash table keys for warning below:
--> user #1080
--> staff
--> James R Stone
--> 1080
--> www-data
--> james
--> root
--> l2049
--> inode/directory

(nautilus:32273): Eel-WARNING **: "unique eel_ref_str" hash table still has 9 elements at quit time (keys above)

(nautilus:32273): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 17 elements at quit time



BTW Thanks for a fantastic operating system.

---

### Post by stderr on 2010-06-06
Hi fndtn357!

Not sure about your messages, but if you're going to launch nautilus as root, because it's a graphical application, you need to launch it with gksudo

```
gksudo nautilus
```

Secondly, it's not normally a good idea to launch nautilus as root (I ***never*** do it), but I won't preach on about that.

---

### Post by fndtn357 on 2010-06-06
> **stderr said:**
> Hi fndtn357!

Not sure about your messages, but if you're going to launch nautilus as root, because it's a graphical application, you need to launch it with gksudo

```
gksudo nautilus
```

Secondly, it's not normally a good idea to launch nautilus as root (I ***never*** do it), but I won't preach on about that.



Thanks, even with your suggestion this is the latest crop of errors that is returned:


gksudo nautilus
Initializing nautilus-dropbox 0.6.2

** (nautilus:2871): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2871): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2871): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Shutting down nautilus-gdu extension
Shutting down dropbox extension

(nautilus:2871): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:2871): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time


And, in regard to your comment about logging in as root, I haven't found the best way to have complete control while developing applications on my machine. I came from the windows camp recently and have much to learn. Between drush not being compliant in non-administrative mode and not wanting to ftp into my own machine I have resorted to copying certain files into protected directories and then closing nautilus down immediately. Other suggestions are welcome.
James

---

