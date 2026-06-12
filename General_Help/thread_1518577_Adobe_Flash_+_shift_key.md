---
title: "Adobe Flash + shift key"
date: 2010-06-26
forum: General Help
---

### Post by ene_dene on 2010-06-26
I'm having a problem with Ubuntu 10.04 x64. Whenever I want to use a flash application in browser I need to hold shift key and then click the mouse and than it works.
For example, play button on youtube, I have to press shift key and then mouse button on play button to pause or play. It's really annoying is there a way to fix this?

---

### Post by supergrav on 2010-06-26
Have you installed flash player via ubuntu software center? Because since you're using 64bit version, you should install different version of flash player in order to work smoothly.

---

### Post by ene_dene on 2010-06-27
> **supergrav said:**
> Have you installed flash player via ubuntu software center? Because since you're using 64bit version, you should install different version of flash player in order to work smoothly.
I've installed it through package ubuntu-restricted-extras. And it works fast and everything but I need to press the darn shft key to use the buttons.

---

### Post by supergrav on 2010-06-27
My system is running on 64bit version and I had similar problems. I uninstalled via ubuntu software center the installed (through restricted extras) version of flash player and followed this guide [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/"). No other problems after that... You can try it and if it doesn't solve your problem revert changes.

---

### Post by ene_dene on 2010-06-27
> **supergrav said:**
> My system is running on 64bit version and I had similar problems. I uninstalled via ubuntu software center the installed (through restricted extras) version of flash player and followed this guide [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/"). No other problems after that... You can try it and if it doesn't solve your problem revert changes.
Unfortunately that will not work for me. Adobe stopped the support for 64bit Linux flash so it's a security risk.
But thank you anyway.

---

### Post by lovinglinux on 2010-06-27
This usually happens when you are using the 32bit plugin on a 64bit system.

To fix that you need to edit the npviewer file. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by ene_dene on 2010-06-27
Thank you very much, that works.

---

