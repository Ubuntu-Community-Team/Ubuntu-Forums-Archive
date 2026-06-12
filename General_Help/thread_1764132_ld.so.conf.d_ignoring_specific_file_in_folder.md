---
title: "ld.so.conf.d ignoring specific file in folder"
date: 2011-05-21
forum: General Help
---

### Post by WitchCraft on 2011-05-21
Question:

I had a little problem installing google earth.

So afterwards, I needed to add a directory to the LD_Library path.

I created the file
```

/etc/ld.so.conf.d/googleearth.conf

```

And filled it with
```

# Google-Earth needs you
/opt/google/earth/free

```

Now the problem is there are also some QT libraries in
/opt/google/earth/free

Unfortunately, when I add the path to ld.so.conf.d, every other program, such as skype and VLC, use the google qt file, which is a custom compilation, and thus misses a few symbols skype and vlc need...

How can I add the path
/opt/google/earth/free
and tell the linker to ignore certain files, such as
```

libQtCore.so.4
libQtNetwork.so.4

```


Edit:
Or better:
How can I tell ldd to only use the google-earth version for google earth ?
Because I just tried removing everything qt*.so.* from that directory, and that results in google-earth crashing after 15 seconds.

---

### Post by Toz on 2011-05-21
> **WitchCraft said:**
> Edit:
Or better:
How can I tell ldd to only use the google-earth version for google earth ?
Because I just tried removing everything qt*.so.* from that directory, and that results in google-earth crashing after 15 seconds.

How about using the LD_LIBRARY_PATH environment variable to start google earth. Have a look at this link: [http://www.wiredrevolution.com/system-administration/how-to-correctly-use-ld_library_path](http://www.wiredrevolution.com/system-administration/how-to-correctly-use-ld_library_path)

Something like:```
$ export LD_LIBRARY_PATH="/opt/google/earth/free:$LD_LIBRARY_PATH"
$ google-earth
```

---

