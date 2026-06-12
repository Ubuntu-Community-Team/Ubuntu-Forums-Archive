---
title: "PS3 Media Server and the Java Temp Directory"
date: 2009-10-19
forum: General Help
---

### Post by thebrandon on 2009-10-19
In order to get the PS3 media center to function properly I have to move everything to /tmp/javaps3media/ the problem with that is whenever I log out it deletes all of the stuff in that directory but I cant get it to work properly in another directory without getting the error :

[linux/tsMuxeR] INFO 23:49:45.816 Starting linux/tsMuxeR /tmp/javaps3media/pms-tsmuxer.meta /tmp/javaps3media/1255405785132tsmuxerout.ts
[linux/tsMuxeR] 23:49:45.841 Fatal error in process starting: : Cannot run program "linux/tsMuxeR": java.io.IOException: error=2, No such file or directory

How can I change it to look for tsMusxeR in a different directory?

---

### Post by thebrandon on 2009-10-20
I added the path of the directory where I keep PSM to my bashrc but that didnt help either, I still get the error msg :

[linux/tsMuxeR] TRACE 00:23:45.793 [linux/tsMuxeR] 00:23:45.711 Fatal error in process starting: : Cannot run program "linux/tsMuxeR": java.io.IOException: error=2, No such file or directory
[Thread-307] TRACE 00:23:50.734 Starting transcode/remux of Archer.S01E01.720p.HDTV.X264-DIMENSION.mkv
[linux/tsMuxeR] 00:23:51.581 Fatal error in process starting: : Cannot run program "linux/tsMuxeR": java.io.IOException: error=2, No such file or directory
[linux/tsMuxeR] TRACE 00:23:51.619 java.io.IOException: Cannot run program "linux/tsMuxeR": java.io.IOException: error=2, No such file or directory
[linux/tsMuxeR] TRACE 00:23:51.623 	at java.lang.ProcessBuilder.start(ProcessBuilder.java:459)
[linux/tsMuxeR] TRACE 00:23:51.659 	at net.pms.io.ProcessWrapperImpl.run(ProcessWrapperImpl.java:83)
[linux/tsMuxeR] TRACE 00:23:51.660 Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
[linux/tsMuxeR] TRACE 00:23:51.660 	at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
[linux/tsMuxeR] TRACE 00:23:51.660 	at java.lang.ProcessImpl.start(ProcessImpl.java:65)
[linux/tsMuxeR] TRACE 00:23:51.661 	at java.lang.ProcessBuilder.start(ProcessBuilder.java:452)
[linux/tsMuxeR] TRACE 00:23:51.661 	... 1 more

Can I redirect java to look or even install somewhere else?

---

