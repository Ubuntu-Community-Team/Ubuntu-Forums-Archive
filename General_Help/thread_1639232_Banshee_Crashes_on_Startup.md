---
title: "Banshee Crashes on Startup"
date: 2010-12-06
forum: General Help
---

### Post by Vaxon on 2010-12-06
I install Banshee 1.8 on Kubuntu 10.04 from a PPA
but it will not start up now
I've ran it from a terminal and this is the output

```
[Info  14:04:45.208] Running Banshee 1.8.0: [Ubuntu 10.04.1 LTS (linux-gnu, i486) @ 2010-09-30 23:38:39 UTC]
[Info  14:04:46.711] Starting collection of anonymous usage data
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
[Warn  14:04:51.148] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  14:04:51.148] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:04:51.155] Updating web proxy from GConf
[Warn  14:04:51.289] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  14:04:51.289] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:04:51.291] All services are started 4.778386
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 335 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by Gyoja on 2010-12-12
i had the same problem and found the solution here:

[http://ubuntuforums.org/showthread.php?p=10228972#post10228972](http://ubuntuforums.org/showthread.php?p=10228972#post10228972)

hope it helps.

---

