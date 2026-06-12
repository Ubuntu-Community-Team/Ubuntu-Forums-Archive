---
title: "Upgraded to Karmic - rawstudio only works as root."
date: 2009-11-01
forum: General Help
---

### Post by musther on 2009-11-01
Just upgraded to Karmic and installed rawstudio.

Now if I run it, it crashes:
```
musther@dominus:~$ rawstudio
Segmentation fault (core dumped)

```

But it runs fine as root.

Any ideas?

----EDIT----
Odd, if I run rawstudio with any kind of switch:
rawstuido -l
for example, it will start, but upon opening any pictures, it crashes.

---

### Post by kintupS on 2010-01-09
Exactly same behavior here since i just did an update (but i was already on Karmic before and i remember having used it since upgrade to Karmic).

Starting rawstudio alone, segfault:
```
mXXXXn@HXX0:~$ rawstudio
Segmentation fault
```Starting with an invalid option, it starts until i try to load a directory, then segfaults:
```
mXXXXn@HXX0:~$ rawstudio --help
rawstudio: invalid option -- '-'
rawstudio: invalid option -- 'h'
rawstudio: invalid option -- 'e'
rawstudio: invalid option -- 'l'
rawstudio: invalid option -- 'p'

(rawstudio:2196): Gtk-CRITICAL **: gtk_tree_store_get_path: assertion `iter->stamp == tree_store->stamp' failed
Segmentation fault
mXXXXn@HXX0:~$ rawstudio -l
rawstudio: invalid option -- 'l'

(rawstudio:2208): Gtk-CRITICAL **: gtk_tree_store_get_path: assertion `iter->stamp == tree_store->stamp' failed
Segmentation fault
```Starting with a directory path, direct segfault:
```
mXXXXn@HXX0:~$ rawstudio /media/4XXXXX8/.../

(rawstudio:2188): Gtk-CRITICAL **: gtk_tree_store_get_path: assertion `iter->stamp == tree_store->stamp' failed
Segmentation fault
```Starting with an invalid option and a directory or filename, it starts but without opening the directory, and then segfaults when i load a directory:
```
mXXXXn@HXX0:~$ rawstudio -l /media/4XXXXX8/.../DSC_XXXX.NEF 
rawstudio: invalid option -- 'l'

(rawstudio:2254): Gtk-CRITICAL **: gtk_tree_store_get_path: assertion `iter->stamp == tree_store->stamp' failed
Segmentation fault
```The error on gtk_tree_store_get_path always happens before the segfault. Starting as root starts, untill i try to load a directory. So starting it with no options goes a little further with root:
```
mXXXXn@HXX0:~$ sudo rawstudio
[sudo] password for mXXXXn: 

(rawstudio:2278): Gtk-CRITICAL **: gtk_tree_store_get_path: assertion `iter->stamp == tree_store->stamp' failed
Segmentation fault
```

Starting under gdb:
```
mXXXXn@HXX0:~$ gdb rawstudio
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/rawstudio...(no debugging symbols found)...done.
(gdb) start
Function "main" not defined.
Make breakpoint pending on future shared library load? (y or [n])  

Starting program: /usr/bin/rawstudio 
[Thread debugging using libthread_db enabled]
[New Thread 0xb5a64b70 (LWP 2372)]
[New Thread 0xb5263b70 (LWP 2373)]
[New Thread 0xb4a62b70 (LWP 2374)]
[New Thread 0xb4261b70 (LWP 2375)]
[Thread 0xb5263b70 (LWP 2373) exited]
[Thread 0xb5a64b70 (LWP 2372) exited]
[New Thread 0xb5a64b70 (LWP 2376)]
[New Thread 0xb5263b70 (LWP 2377)]
[New Thread 0xb39bdb70 (LWP 2378)]

Program received signal SIGSEGV, Segmentation fault.
0x008620ac in ?? () from /usr/lib/libgtk-x11-2.0.so.0
(gdb) quit
A debugging session is active.

    Inferior 1 [process 2369] will be killed.

Quit anyway? (y or n) y
```

So it seems rawstudio has a problem with the updated libgtk... well possible that there is a bug in rawstudio that didn't appear on previous versions of libgtk-x11...

---

### Post by musther on 2010-01-09
It turns out it's a bug of some sort, open gconf-editor (run 'gconf-editor' in a terminal) and find the rawstudio entries, remove them, try again.

Worked for me!

---

### Post by davidmcq on 2010-03-21
Gconf-editor didn't work but re-install did work for me:

# apt-get remove --purge rawstudio
# apt-get install rawstudio


It seems a bit drastic, and I'm still getting the Gtk-CRITICAL message. Whatever works, I guess. Maybe I just haven't run into the bug yet, but I've restarted several times.

---

