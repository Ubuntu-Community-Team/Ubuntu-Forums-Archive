---
title: "Why can't I install &quot;Gettext&quot;?"
date: 2009-12-15
forum: General Help
---

### Post by Alpyre on 2009-12-15
Hi,
Actually I want to install aMSN with video/voice chat feature (which is dependant on the farsight framework).

I have taken this wiki as installation guide: [http://www.amsn-project.net/wiki/Farsight](http://www.amsn-project.net/wiki/Farsight)

Well it shortly says, firstly install all dependancies in the right order. 
First I have to update glib at least to 2.16
The only version I could find on the net is 2.22.3 (which is newer and that should not be a problem).

After ./configure it reports that I have to install gettext first.

I have downloaded gettext-0.17. 
./configure (ended without any errors)
make (ends with the following:

```
In function 'open',
    inlined from 'msgdomain_list_print' at write-catalog.c:223:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [write-catalog.lo] Error 1
make[4]: `/home/alper/Desktop/gettext-0.17/gettext-tools/src' dizininden ç&#305;k&#305;l&#305;yor
make[3]: *** [all] Error 2
make[3]: `/home/alper/Desktop/gettext-0.17/gettext-tools/src' dizininden ç&#305;k&#305;l&#305;yor
make[2]: *** [all-recursive] Error 1
make[2]: `/home/alper/Desktop/gettext-0.17/gettext-tools' dizininden ç&#305;k&#305;l&#305;yor
make[1]: *** [all] Error 2
make[1]: `/home/alper/Desktop/gettext-0.17/gettext-tools' dizininden ç&#305;k&#305;l&#305;yor
make: *** [all-recursive] Error 1
```)

What should I do now!?
Thanks in advance
Alper

---

### Post by llamabr on 2009-12-15
how about:

```
sudo apt-get install gettext
```

---

### Post by llamabr on 2009-12-15
you know, empathy comes with video and voice, without having to bother with these extremely complicated instructions:

[https://wiki.ubuntu.com/EmpathyVsPidginUsability](https://wiki.ubuntu.com/EmpathyVsPidginUsability)

---

### Post by Alpyre on 2009-12-15
Thanks for the extemely fast replies...

I have Empathy preinstalled (as normal). I enjoy using it very much. It is fairly simple and friendly.
But when I want to videochat with an MSN contact (e.g.) the voice and video chat commands in the right click menu are (always) inactive.

I'm installing gettext now thanks.

---

### Post by Alpyre on 2009-12-15
This time I cannot install gstreamer-0.10.25 :S
./configure fails with the following:

```
checking for XML... no
no
configure: error: Need libxml2 for glib2 builds -- you should be able to do without it -- this needs fixing

```libxml2 looks to be installed and upto date on my system. ??

EDIT:

Ok, I've downloaded the latest "libxml2" from [ftp://xmlsoft.org/libxml2](ftp://xmlsoft.org/libxml2) and installed it. No problems now. 

Alper

---

