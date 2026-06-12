---
title: "Kbuildsycoca closed unexpectedly"
date: 2010-09-01
forum: General Help
---

### Post by Idanwin on 2010-09-01
whenever I start a KDE program (eg Konquerer or Konversation) I get multiple error messages.
When I run it in a terminal, I get this:
```
:~$ konqueror 
kbuildsycoca4 running...
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "." 
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "." 
KCrash: Application 'kbuildsycoca4' crashing...
sock_file=/home/idanwin/.kde/socket-Astraea/kdeinit4__0
ERROR: Running KSycoca failed.
kbuildsycoca4 running...
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "." 
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "." 
KCrash: Application 'kbuildsycoca4' crashing...
sock_file=/home/idanwin/.kde/socket-Astraea/kdeinit4__0
ERROR: Running KSycoca failed.
KCrash: Application 'konqueror' crashing...
sock_file=/home/idanwin/.kde/socket-Astraea/kdeinit4__0
:~$

```

And multiple KDE crash handler windows saying:
```

**General** | Developer Information
We are sorry, KBuildSycoca closed unexpectedly.
You can help us improve KDE by reporting this error.
Learn more about bug repoting.

*note*: it is sage to this dialog if you do noy want to report this bug.
[B]
Details:[/B]
Executable: kbuildsycoca4 PID: 6638 Signal: 11 (Segmentation fault)

```
```

General | **Developer Information**
This crash information is useful ***

[INDENT]Application: KBuildSycoca (kbuildsycoca4), signal: Segmentation fault
The current source language is "auto; currently c".
[KCrash Handler]
#5  KSycocaEntry::offset (this=0x0) at ../../kdecore/sycoca/ksycocaentry.cpp:133
#6  0x00007f9ff10575dd in KBuildMimeTypeFactory::savePatternLists (this=0x16ac510, str=<value optimized out>) at ../../kded/kbuildmimetypefactory.cpp:361
#7  0x00007f9ff1057a93 in KBuildMimeTypeFactory::save (this=0x16ac510, str=...) at ../../kded/kbuildmimetypefactory.cpp:307
#8  0x00007f9ff1050da9 in KBuildSycoca::save (this=0x169f7e0, str=0x169f000) at ../../kded/kbuildsycoca.cpp:525
#9  0x00007f9ff1053ab3 in KBuildSycoca::recreate (this=0x169f7e0) at ../../kded/kbuildsycoca.cpp:433
#10 0x00007f9ff1054ee6 in kdemain (argc=<value optimized out>, argv=<value optimized out>) at ../../kded/kbuildsycoca.cpp:829
#11 0x00007f9ff0cf3abd in __libc_start_main (main=<value optimized out>, argc=<value optimized out>, ubp_av=<value optimized out>, init=<value optimized out>, fini=<value optimized out>, 
    rtld_fini=<value optimized out>, stack_end=0x7fff2199c6e8) at libc-start.c:220
#12 0x0000000000400689 in _start () at ../sysdeps/x86_64/elf/start.S:113[/INDENT]


```

---

