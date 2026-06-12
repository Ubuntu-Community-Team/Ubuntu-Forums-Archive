---
title: "Wine"
date: 2010-02-14
forum: General Help
---

### Post by cdawley4 on 2010-02-14
Hi,

I am not sure if this is where Wine would fit in, but here goes.  I purchased a Garmin Nuvi and was trying to register it so I can add more POIs.  I read another thread where someone got Wine to work.  When I installed it, it installed 1.1.38.  The problem I am having is when I try to run programs from it, such as Internet Explorer or try to install programs, I get a zip error.

```
Archive:  /home/chris/Downloads/CommunicatorPlugin_291.exe
[/home/chris/Downloads/CommunicatorPlugin_291.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/chris/Downloads/CommunicatorPlugin_291.exe or
          /home/chris/Downloads/CommunicatorPlugin_291.exe.zip, and cannot find /home/chris/Downloads/CommunicatorPlugin_291.exe.ZIP, period.

```

This is what I get when I try to run Internet Explorer.

```
Archive:  /home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe
[/home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe or
          /home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe.zip, and cannot find /home/chris/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe.ZIP, period.

```

---

### Post by LoneWolfJack on 2010-02-14
you're probably trying to double-click exe files. per default, exe files are associated with zip in ubuntu.

instead, right click the file and choose "open with wine".

---

### Post by Richard1979 on 2010-02-14
You can easily change this behaviour with Ubuntu Tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

