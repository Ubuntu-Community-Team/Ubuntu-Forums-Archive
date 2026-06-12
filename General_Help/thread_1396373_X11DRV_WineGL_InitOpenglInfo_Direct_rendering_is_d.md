---
title: "X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled"
date: 2010-02-02
forum: General Help
---

### Post by industrai on 2010-02-02
Hi All,

I'm trying to run Mavis Beacon Teaches Typing 20 on my Ubuntu 9.10 64 bit with wine 1.1.37, but it is extremely laggy. The mouse stutters ever 2 seconds or so, making it difficult to click on anything.

Running it from command line, I noticed this error message:

```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
```

I am using the ATI open source driver, and from what I can tell DRI is working. glxinfo says:


```
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
```


I've searched the error using the search function, but the search doesn't seem to bring back anything relevant. Using google found this forum thread,

[http://forum.winehq.org/viewtopic.php?t=7370&sid=446054b5899e48d75f706a500416ccfd](http://forum.winehq.org/viewtopic.php?t=7370&sid=446054b5899e48d75f706a500416ccfd)

The solution appears to be installing the 32bit DRI drivers, which I believe are ia32-libs. The version installed on my system is 2.7ubuntu17.

I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/506320](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/506320)

Which appears to be specific to nvidia (and doesn't fix my problem). I also tried LD_PRELOAD=/usr/lib32/libGL.so wine Mavis.exe, and that made it even slower.

I've also registered an account on the wine forums and posted there, but this might be ubuntu specific so hopefully the double post isn't a bad thing.

---

