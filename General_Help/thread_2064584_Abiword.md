---
title: "Abiword"
date: 2012-09-29
forum: General Help
---

### Post by skywalk on 2012-09-29
Hello:
In a laptop five or six years old I instaled 12.04 Alternate with LXDE desktop. It's running flawlesly with little amount of  RAM.
I installed Abiword but, in the repositories there is the 2.9.2 version, a development version that doesn't work well.
Now, I want to install the 2.8.6. stable version from the tarball I downloaded from Abiword's page. Afeter many work with dependencies I finally  got *configure*  but *make* is giving me errors. This is the end of * make*:
> ribidi -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 -lexpat -ljpeg -lpng -lgsf-1 -lxml2 -lenchant -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 -lfreetype -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 -lcairo -lgobject-2.0 -lglib-2.0   -ljpeg 
libtool: link: g++ -g -O2 --no-undefined -o .libs/abiword abiword-UnixMain.o -pthread -Wl,--export-dynamic  ./.libs/libabiword-2.8.so /usr/lib/libfribidi.so -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 /usr/lib/i386-linux-gnu/libexpat.so -lpng -lgsf-1 /usr/lib/i386-linux-gnu/libxml2.so /usr/lib/libenchant.so -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 /usr/lib/i386-linux-gnu/libfreetype.so -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 /usr/lib/i386-linux-gnu/libcairo.so -lgobject-2.0 -lglib-2.0 -ljpeg -pthread
g++: error: unrecognized option '--no-undefined'
make[3]: *** [abiword] Error 1
make[3]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6'
make: *** [all] Error 2
jordi@ubuntu:~/Downloads/abiword-2.8.6$ 


I try to find solutions but I'm lost in the dark.
If anyone can help me I'm grateful for your support.
Sorry for my bad english.

---

### Post by elliotn on 2012-09-29
> sudo apt-get install abiword
it is better that going through hell of tarballs

---

### Post by Statia on 2012-09-29
> **elliotn said:**
> it is better that going through hell of tarballs

Did you even read his post?
The repositories hold an unstable development version that should have never been included in the release.

OP: My make fails with the same error and I recently saw someone else describe exactly the same error here. We're not doing anything wrong. I'm afraid this is just the nature of Open Source. Sometimes it doesn't work.

(No, I am not trolling. Just venting frustration with lack of QA/QC in OSS)

---

### Post by jerrrys on 2012-09-29
A better way to go back in post 18 & 19.

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

---

### Post by spjackson on 2012-09-29
@OP According to this [bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628267"), it is a bug in 2.8.6-0.3 and fixed in 2.8.6-0.4. Unfortunately, the download on the Abiword website predates this fix.

The flag is supposed to be "-Wl,--no-undefined".

You can get the corrected source here. [https://launchpad.net/ubuntu/+source/abiword/2.8.6-0.4ubuntu1](https://launchpad.net/ubuntu/+source/abiword/2.8.6-0.4ubuntu1) and there are pre-built binaries:
[https://launchpad.net/ubuntu/precise/i386/abiword/2.8.6-0.4ubuntu1](https://launchpad.net/ubuntu/precise/i386/abiword/2.8.6-0.4ubuntu1)
[https://launchpad.net/ubuntu/precise/amd64/abiword/2.8.6-0.4ubuntu1](https://launchpad.net/ubuntu/precise/amd64/abiword/2.8.6-0.4ubuntu1)

---

### Post by skywalk on 2012-09-30
**spjackson, jerrrys** thanks for your information.
I mark the post as Solved.

---

