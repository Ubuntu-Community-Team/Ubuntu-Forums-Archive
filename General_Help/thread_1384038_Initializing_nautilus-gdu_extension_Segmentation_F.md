---
title: "Initializing nautilus-gdu extension Segmentation Fault after using assogiate"
date: 2010-01-17
forum: General Help
---

### Post by patmalcolm91 on 2010-01-17
I'm running 9.10 and just installed assogiate and used it to change the icon of a filetype. Now, nautilus crashes every time I try to run it with:

```
(nautilus:22736): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:22736): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:22736): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:22736): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Segmentation fault

```

and here's a relevant part of the output of running "gdb nautilus":

```

Initializing nautilus-gdu extension
[New Thread 0x7fffebf72910 (LWP 24620)]
[New Thread 0x7fffe122c910 (LWP 24621)]
[New Thread 0x7fffdaf14910 (LWP 24622)]
[Thread 0x7fffe122c910 (LWP 24621) exited]
[New Thread 0x7fffe122c910 (LWP 24623)]
[New Thread 0x7fffd9e4a910 (LWP 24624)]
[New Thread 0x7fffd9649910 (LWP 24625)]

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff57ff821 in ?? () from /usr/lib/libgio-2.0.so.0
```

If I run "gksu nautilus", it opens fine, leading me to believe this is a preference file corruption or something.

I've tried the following:
*completely removing and re-istalling nautilus
*removing ~/.local/share/gvfs-metadata

---

### Post by Kismet on 2010-02-01
Try removing 
~/.local/share/gvfs-metadata
directory. 
It's kinda like file browser cache(I think) that can get corrupted.

---

### Post by jdsanchez473 on 2010-03-22
thank you!

i was having the same problem and removing this folder fixed it. For those of you who do not know how to fix this situation do the following:

**Press** ALT+F2


**Type** ```
gnome-terminal
```

**Type** ```
rm -rf ~/.local/share/gvfs-metadata
```

Restart your computer and you should be good to go, if not then this isn't your problem :)

---

### Post by jango4 on 2011-10-11
Hi!

I know, this is a rather old thread, but i wanted to thank you.

After upgrading to Ubuntu 11.10 my nautilus crashed randomly when clicking on items or opening folders, or even on just scrolling. 
I was frustrated - a computer does not work, if the file browser crashes all the time... 
In the logs i also found "Initializing nautilus-gdu extension Segmentation Fault" and Google brought me here.

And removing rm -rf ~/.local/share/gvfs-metadata worked great. No crash any more. Thanks!

---

### Post by nothingspecial on 2011-10-11
Glad it helped you. :)

But please don't bump it to the top.

Closed.

---

