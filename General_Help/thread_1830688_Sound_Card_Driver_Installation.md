---
title: "Sound Card Driver Installation"
date: 2011-08-22
forum: General Help
---

### Post by Rebecca_D on 2011-08-22
Please help someone completely new to Linux. Having got it up and running the one problem I have is with siound reproduction. Sounds like an old 78 record. Decided to see if there are any Linux drivers for my sound card C-Media 8738. Yes there was so downloaded with assistance of Archive Manager and then extrated .exe file. I tried double clicking on this setup file but just get message:

Archive:  /home/rebecca/.gvfs/cmpci-5.68.tar.zip/DriverUpdaterSetup-1.2.3.2267_multilang.exe
[/home/rebecca/.gvfs/cmpci-5.68.tar.zip/DriverUpdaterSetup-1.2.3.2267_multilang.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/rebecca/.gvfs/cmpci-5.68.tar.zip/DriverUpdaterSetup-1.2.3.2267_multilang.exe or
          /home/rebecca/.gvfs/cmpci-5.68.tar.zip/DriverUpdaterSetup-1.2.3.2267_multilang.exe.zip, and cannot find /home/rebecca/.gvfs/cmpci-5.68.tar.zip/DriverUpdaterSetup-1.2.3.2267_multilang.exe.ZIP, period.

How do I install this driver. Can anyone explain in SIMPLE terms how Ubuntu does this. I am a very little bear with a very small brain!!! :(

---

### Post by realzippy on 2011-08-22
Which ubuntu version do you use (assume it is not dapper)?
You try to install a windows driver,this will not work...
run
```
lspci
```
and post the output for your card,maybe someone else has an idea...

---

