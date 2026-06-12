---
title: "Mouse Clicks not working on Flash"
date: 2010-03-02
forum: General Help
---

### Post by Ignado on 2010-03-02
Whenever I try to watch a video on the internet half the buttons don't work. Some times i cant change the sound, sometimes i can't pause the video, sometimes i cant even play the video, etc. It is different for every video and different every time i refresh the page the video is on.

I found [THIS LINK](http://www.webupd8.org/2009/11/fix-mouse-clicks-not-working-in-flash.html) describing the exact problem I had. The first solution doesn't work because i am running 9.10 64 bit. When I tried to do the second solution this is the result:

```

ryan@ryan-desktop:~$ sh fix_flash.sh
Stopping any Firefox that might be running.
[sudo] password for ryan: 
firefox: no process found
Removing any other flash plugin previously installed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 ia32-libs libc6-i386 lib32gcc1
  lib32asound2 lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Installing Flash Player 10.
sudo: cd: command not found
--2010-03-02 15:25:38--  http://labs.adobe.com/downloads/flashplayer10.html
Resolving labs.adobe.com... 192.150.18.72
Connecting to labs.adobe.com|192.150.18.72|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `flashplayer10.html'

    [ <=>                         ] 21,672       110K/s   in 0.2s    

2010-03-02 15:25:38 (110 KB/s) - `flashplayer10.html' saved [21672]

wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
ls: cannot access libflashplayer-*.linux-x86_64.so.tar.gz: No such file or directory
Version is .
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
cp: cannot stat `libflashplayer.so': No such file or directory
Linking the libraries so Firefox and apps built on XULRunner can find it.

```

So clearly this was not the problem either. If anyone has more advice on how to fix the problem it would be greatly appreciated. 

Thanks

Ig

---

### Post by magnusk on 2010-03-02
Uninstall flashplayer and download flashplayer from ADOBE. Here is a link describing how to do it: [http://adammichaelroach.com/blog/110309-installing-adobe-flash-64-bit-ubuntu-910-karmic-koala]("http://adammichaelroach.com/blog/110309-installing-adobe-flash-64-bit-ubuntu-910-karmic-koala").
I don't now what's causing the problem but installing flashplayer downloaded from ADOBE fixed it.

---

