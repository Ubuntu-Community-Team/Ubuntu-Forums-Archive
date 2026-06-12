---
title: "segfault  error 4 in libflashplayer.so"
date: 2009-12-16
forum: General Help
---

### Post by MountainX on 2009-12-16
Can anyone help with this? My browser crashes when loading gmail, etc. Here's some troubleshooting info:

```
$ uname -a
Linux MyBox 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
```I'm running Swiftweasel 3.5. I installed Flash 64 bit using these instructions:
[http://queleimporta.com/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

Everything was working until I attempted to install Sun Java. (I have since reinstalled java and I think that issue is resolved.) But Swiftweasel started crashing on me as soon as any site invokes libflashplayer.so. Even Chromium gives an error message that  libflashplayer.so crashed. Chromium stays open, but Swiftweasel just completely closes down. It even crashes with Gmail.

dmesg shows this:
```
[1006342.809123] exe[6251]: segfault at a018 ip 00007fd0eeb84cf2 sp 00007fff2aec4700 error 4 in libflashplayer.so[7fd0ee935000+8cf000]
```I have already reinstalled Swiftweasel and reinstalled flash.
What else can I do?

---

### Post by spleencheesemonkey on 2010-01-06
bump

---

### Post by MountainX on 2010-01-06
> **spleencheesemonkey said:**
> bump

upgrade xulrunner

---

### Post by ahmed.gaber on 2010-06-13
I have the same problem but with different symptoms. Xulrunner is installed and up to date "version 1.9.2".

This is the problem:
```
[ 3649.911066] npviewer.bin[2221]: segfault at f59cb04c ip 00000000f61ae057 sp 00000000ffe1ba70 error 4 in libflashplayer.so[f5e0f000+b04000]
```This is the symptoms:
I can't interact with any flash web content in Firefox and if I left the browser opened for a while the flash content crashes and the flash content is replaced in a light gray.

I am using Ubuntu 10.04 LTS the Lucid Lynx release.

---

