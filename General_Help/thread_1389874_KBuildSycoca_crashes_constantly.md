---
title: "KBuildSycoca crashes constantly?"
date: 2010-01-24
forum: General Help
---

### Post by VirusCollector on 2010-01-24
I have no idea what's going on. 

The KDE Crash Handler comes up many, many times a day. Twice at boot, twice if I install anything, and once whenever it feels like it. It complains constantly about KBuildSycoca crashing, but I've run an apt-file search for everything that contains it and removed it (except for kde-libs, I need some stuff in it)

I've tried following its instructions about reporting bugs and installed the massive amounts of *-dbg packages, but I'm not even sure that anything is done about this. I'm using GNOME, why is this happening even on boot?

Help please, this thing is so annoying)


(Here is the debug information it gives me, if this is any help.)

```
  p, li { white-space: pre-wrap; }  Application: KBuildSycoca (kdeinit4), signal: Segmentation fault
 The current source language is "auto; currently c".
 [KCrash Handler]
 #5  KSycocaEntry::offset (this=0x0) at ../../kdecore/sycoca/ksycocaentry.cpp:133
 #6  0x00007f55465465dd in KBuildMimeTypeFactory::savePatternLists (this=0xccb210, str=<value optimized out>) at ../../kded/kbuildmimetypefactory.cpp:361
 #7  0x00007f5546546a93 in KBuildMimeTypeFactory::save (this=0xccb210, str=...) at ../../kded/kbuildmimetypefactory.cpp:307
 #8  0x00007f554653fda9 in KBuildSycoca::save (this=0x11372e0, str=0xcbad30) at ../../kded/kbuildsycoca.cpp:525
 #9  0x00007f5546542ab3 in KBuildSycoca::recreate (this=0x11372e0) at ../../kded/kbuildsycoca.cpp:433
 #10 0x00007f5546543ee6 in kdemain (argc=<value optimized out>, argv=<value optimized out>) at ../../kded/kbuildsycoca.cpp:829
 #11 0x0000000000406da8 in launch (argc=2, _name=<value optimized out>, args=<value optimized out>, cwd=<value optimized out>, envc=16, envs=<value optimized out>, reset_env=false, tty=0x0, 
     avoid_loops=false, startup_id_str=0xc06dfd "") at ../../kinit/kinit.cpp:677
 #12 0x0000000000407aa0 in handle_launcher_request (sock=7, who=<value optimized out>) at ../../kinit/kinit.cpp:1169
 #13 0x0000000000407f51 in handle_requests (waitForPid=0) at ../../kinit/kinit.cpp:1362
 #14 0x0000000000408bb2 in main (argc=2, argv=<value optimized out>, envp=<value optimized out>) at ../../kinit/kinit.cpp:1793

```

---

### Post by VirusCollector on 2010-01-26
bump please?

---

