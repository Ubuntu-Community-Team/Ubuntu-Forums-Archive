---
title: "Installing Tablet"
date: 2009-11-19
forum: General Help
---

### Post by donjorge22 on 2009-11-19
I've been trying to install a Trust 5300 tablet using this guide [https://help.ubuntu.com/community/TabletSetupWizardpen;](https://help.ubuntu.com/community/TabletSetupWizardpen;) however, after the line

```
sudo ./configure --with-xorg-module-dir=/usr/lib/xorg/modules && make
&& make install
```all I get is an error:

```
make[1]: Leaving directory `/home/eldon/wizardpen-0.6.0.2/wizardpen-0.6.0.2'
make[1]: Entering directory `/home/eldon/wizardpen-0.6.0.2/wizardpen-0.6.0.2'
Making all in src
make[2]: Entering directory `/home/eldon/wizardpen-0.6.0.2/wizardpen-0.6.0.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
wizardpen.c:212: warning: initializer-string for array of chars is too long
wizardpen.c: In function 'DeviceInit':
wizardpen.c:648: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected 'int' but argument is of type 'int (*)(struct _DeviceIntRec *, struct xTimecoord *, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)'
wizardpen.c:648: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/eldon/wizardpen-0.6.0.2/wizardpen-0.6.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eldon/wizardpen-0.6.0.2/wizardpen-0.6.0.2'
make: *** [all] Error 2

```Help much appreciated :)

---

### Post by donjorge22 on 2009-11-20
Anyone? I really need it for my coursework (I need to be able to pen in Chinese Characters), and currently I'm having to do it on another, Windows based machine :(

---

### Post by donjorge22 on 2009-11-20
Sorry, posted wrong link, was using the most up-to-date guide in there (for Ibis 8.10). Using Karmic and still can't get it to work.

---

### Post by Styx on 2009-11-23
Hi
I have the same problem. If i finde out how to get it done i will let you know.

---

### Post by donjorge22 on 2009-11-23
Cool, cheers :) still haven't had any luck over here :(

---

### Post by donjorge22 on 2009-11-23
Ok, I changed the pre-compiled file as in here [http://code.google.com/p/linuxgenius/issues/detail?id=1](http://code.google.com/p/linuxgenius/issues/detail?id=1) and got a little further.  At this point though,
```
sudo /etc/init.d/udev restart
```

I get a fresh new error telling me to use a different command :(

---

### Post by drpjkurian on 2009-11-26
> **donjorge22 said:**
> Ok, I changed the pre-compiled file as in here [http://code.google.com/p/linuxgenius/issues/detail?id=1](http://code.google.com/p/linuxgenius/issues/detail?id=1) and got a little further.  At this point though,
```
sudo /etc/init.d/udev restart
```

I get a fresh new error telling me to use a different command :(

Hi 
Please visit my thread

[http://ubuntuforums.org/search.php?searchid=67415926](http://ubuntuforums.org/search.php?searchid=67415926)

---

### Post by donjorge22 on 2009-11-26
I certainly did!  And it worked!  Thanks drjkurian :D  The problem was that there's more automated stuff in later versions, rendering procedures like the udev stuff irrelevant... the other problem was also that missing line that you put in.  The howto that Favux linked to in your thread did put the line in, but not 'til the end which was misleading (as I think he says it ought to work beforehand).  Any ways you look at it though, it's solved now so thanks :D

---

### Post by drpjkurian on 2009-11-26
> **donjorge22 said:**
> I certainly did!  And it worked!  Thanks drjkurian :D  The problem was that there's more automated stuff in later versions, rendering procedures like the udev stuff irrelevant... the other problem was also that missing line that you put in.  The howto that Favux linked to in your thread did put the line in, but not 'til the end which was misleading (as I think he says it ought to work beforehand).  Any ways you look at it though, it's solved now so thanks :D

Hi
You are most welcome

With regards
Dr Kurian

---

