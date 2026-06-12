---
title: "I can't see HD videos in youtube with firefox ...."
date: 2010-07-22
forum: General Help
---

### Post by q8.legend on 2010-07-22
Hi Guys

I'm new to ubuntu, & of course I was coming from windows ;p... I faced some issues with ubuntu, some I solved them & some not.

I have a problem with firefox 3.6.6 and youtube. the problem is I can't change the resolution of the video(360p,470p,720p,1080p). when I try to choose one, it doesn't clicked, instead the player its the one that clicked (like it pass it away and don't see it). This only occur with the new design of youtube(the silky one), the old videos that have the old design(gray one) worked just fine.

Also, this only happen in firefox, I have google chrome and its works great without any problem...

So, do you think that the problem with the flash player(adobe) in the firefox .. ???

I'm currently running under ubuntu 10.04(64 bit), but the problem also occurred in the version 32bit (both of them have the problem, so not from the ubuntu version)..

Thanks alot....

---

### Post by q8.legend on 2010-07-22
Up up up
please

---

### Post by lovinglinux on 2010-07-22
Please don't bump your thread so fast. Wait a least 24 hours.

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

Also check my FlashVideoReplacer extension. It allows you to watch YouTube videos with a less CPU intensive plugin. Is great for HD video and you won't have the issue you are experiencing.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)

---

### Post by q8.legend on 2010-07-22
Thank you sooooooo much lovinglinux :)

it does works perfectly 100% without any problem , thanks alot ;)

but, why this problem happen also in the 32bit(ubuntu) architecture also !! ??

---

### Post by lovinglinux on 2010-07-22
> **q8.legend said:**
> Thank you sooooooo much lovinglinux :)

it does works perfectly 100% without any problem , thanks alot ;)

but, why this problem happen also in the 32bit(ubuntu) architecture also !! ??

As far as I know it only happens on 64bit. Why it happens...Adobe lack of support.

---

