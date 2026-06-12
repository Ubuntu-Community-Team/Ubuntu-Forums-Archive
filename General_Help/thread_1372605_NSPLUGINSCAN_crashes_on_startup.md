---
title: "NSPLUGINSCAN crashes on startup"
date: 2010-01-04
forum: General Help
---

### Post by stefanmuc2k on 2010-01-04
When I log in to my system I always get two KCrash windows telling me that: 

```
The application nspluginscan crashed with signal 11 (SIGSEV).
```

System "history": I installed first kubuntu with KDE4, upgraded to ubuntu 9.10 and then switched to KDE3 (though KDE4 is still on the drive). I've installed the 64 bit version of the distribution.


In the archives there is a post by another user who had the [same]("http://ubuntuforums.org/showthread.php?t=745747") problem with an earlier version of Ubuntu. (It's archived so I couldn't add there.)

nspluginscan produces this output on the command line:
```
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
KCrash: Application 'nspluginscan' crashing...
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
KCrash: Application 'nspluginscan' crashing...

```

For the life of me, I can't figure out where the "/opt/kde3/$LIB/*" entries are being set. :confused: It seems clear that the value of $LIB should be "lib", but I can't find the file from which LD_PRELOAD gets it's value. When I type ```
echo $LD_PRELOAD
``` I just get an empty string.


Also nspluginscan is located at /opt/kde3/bin/nspluginscan - there is another version available at /usr/bin/nspluginscan however. So I tried simply ```
mv /opt/kde3/bin/nspluginscan /opt/kde3/bin/nspluginscan.old
```

This doesn't change a lot but the two "KCrash" lines disappear in the output, and the corresponding KCrash windows are gone:

```
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/kde3/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

```

So far I've observed no ill effects from that move (might happen later ...) but that doesn't seem like a clean solution, and I'm still wondering about the "/opt/kde3/$LIB/*" entries.

Can anyone give me some insight in the underlying problem?

---

### Post by mikerobinson on 2010-02-01
I'm having the same problem. Also KDE4 doesn't load at all. It just crashes. I upgraded from 8.04 to 9.10.

---

### Post by anuszka on 2010-07-23
[http://chakra-project.org/bbs/viewtopic.php?pid=8078#p8078](http://chakra-project.org/bbs/viewtopic.php?pid=8078#p8078) 
Remove the kopete package.

---

