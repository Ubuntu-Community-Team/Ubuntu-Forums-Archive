---
title: "Redirect LD_PRELOAD"
date: 2012-02-17
forum: General Help
---

### Post by Seddy on 2012-02-17
I wanted to use the tool alltray, but i don't have admin rights to install it. My idea was to download the deb from the repos and extract the files i need to my home dir. What i currently have is:
```
ls -1 ~/alltray
alltray
alltray.sh
liballtray.la
liballtray.so
liballtray.so.0
liballtray.so.0.0.0

```What works is ~/alltray/alltray to just start alltray. This enables me to click a window and it is minimzed to tray as expected.

What I want to have working is ~/alltray/alltray someprogramm to have alltray start someprogramm minimized.

And now it begins:
```
~/alltray/alltray.sh gedit
ERROR: ld.so: object '/usr/lib/liballtray.so.0.0.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/liballtray.so.0.0.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/liballtray.so.0.0.0' from LD_PRELOAD cannot be preloaded: ignored.
[and so on]

```With alltray.sh:
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH\:~/alltray
~/alltray/alltray $1
```So obviously setting LD_LIBRARY_PATH is not enough to redirect the library loading to my home dir.
Is there a way to redirect the files LD_PRELOAD needs to my home dir or is there a better way to use alltray?
Compiling alltray from source would probably work but I want to avoid that because ./configure found missing libraries and I don't want to end up in spending the day for compiling all dependencies.

Any ideas are apprechiated.

Remark: in all tests i didn't use ~ but the full path to my home dir. I just replaced that in this post for privacy reasons ;)

---

