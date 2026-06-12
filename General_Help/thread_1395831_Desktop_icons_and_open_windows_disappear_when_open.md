---
title: "Desktop icons and open windows disappear when opening windows share"
date: 2010-02-01
forum: General Help
---

### Post by ubducted on 2010-02-01
On Ubuntu 9.04 when I click on my Places>bookmarks to open my windows share (smb://192.168.etc...), all of my open windows (nautilus, firefox, gimp, anything) will disappear along with my desktop icons.

I can open up new windows, even for those programs that disappeared.  (firefox, nautilus, etc.).

The problem seems similar to this thread: [http://ubuntuforums.org/showthread.php?t=1335306&highlight=icons+windows+disappear](http://ubuntuforums.org/showthread.php?t=1335306&highlight=icons+windows+disappear)

However, my programs are not crashing.  PS command still shows they are running.

I've also tried this solution, but it didn't help: [http://ubuntuforums.org/showpost.php?p=3585306&postcount=6](http://ubuntuforums.org/showpost.php?p=3585306&postcount=6)

This only happens when I browse to a windows share.

Please help!

---

### Post by ubducted on 2010-02-01
I spoke to soon.

Nautilus IS crashing.  And it's only Nautilus and my desktop icons that are now disappearing.

When I run Nautilus, it runs with the --no-desktop option.

I should also mention that I can browse media like external USB drives.  

Also, I just tested connecting to an FTP server.  That also crashes Nautilus.

GNOME Commander browses these filesystems without problem.

There is also no longer a context menu when right clicking on the desktop.

Compiz is not installed.

---

### Post by ubducted on 2010-02-01
Well, I've learned more about the problem:  

$nautilus 2> error.txt
Initializing nautilus-image-converter extension
Initializing nautilus-clamscan extension
Initializing nautilus-open-terminal extension
Segmentation fault
$

The error.txt reads:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10393): WARNING **: Unable to add monitor: Not supported

(nautilus:10393): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:10393): WARNING **: Got GFileInfo with NULL name in smb://192.168.15.17/volume_2/, ignoring. This shouldn't happen unless the gvfs backend is broken.

sys:1: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed

-----

There are plenty of threads and a bug report about the problem, but I haven't found any solution.

This supposed solution did not work: [http://forums.techarena.in/operating-systems/1267752.htm](http://forums.techarena.in/operating-systems/1267752.htm)

Nor did this one: [http://ubuntuforums.org/showthread.php?t=1394101&page=2](http://ubuntuforums.org/showthread.php?t=1394101&page=2)

This thread may be onto something: [http://ubuntuforums.org/showthread.php?t=825965](http://ubuntuforums.org/showthread.php?t=825965)

---

