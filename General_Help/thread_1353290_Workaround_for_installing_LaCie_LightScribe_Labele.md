---
title: "Workaround for installing LaCie LightScribe Labeler on amd64"
date: 2009-12-12
forum: General Help
---

### Post by youoneah on 2009-12-12
There are a large number of resources available to describe installing LightScribe software for Ubuntu:

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe) | Community doc
[http://ubuntuforums.org/showthread.php?t=999532](http://ubuntuforums.org/showthread.php?t=999532) | Dec 08
[http://ubuntuforums.org/showthread.php?t=809112](http://ubuntuforums.org/showthread.php?t=809112) | May 08
[http://ubuntuforums.org/showthread.php?t=106197](http://ubuntuforums.org/showthread.php?t=106197) | Dec 05 - Jul 08
[http://ubuntuforums.org/showthread.php?t=539749](http://ubuntuforums.org/showthread.php?t=539749) | Aug 07 (similar solution)
[http://ubuntuforums.org/showthread.php?t=404854](http://ubuntuforums.org/showthread.php?t=404854) | Apr 07

Since this is closed-source software, it is difficult for the community to remedy the inexistent support for the 64-bit architecture, so you expect a headache. Nevertheless, the LightScribe host software and SimpleLabeler work with little extra trouble after installing as in the guides. With the LaCie Labeler software--the useful one that lets you burn images and not simple labels--I ran into issues I couldn't solve by following just those guides, so now that I found a kind of solution I wanted to share it in case it might help someone else.

The main problem is that upon executing "sudo 4L-gui" or "gksudo 4L-gui", I got the infamous libstdc++.so.5 error:
```
4L-cli: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```
The GUI starts and I can use the software, but it does not detect the drive. Pretty useless.

Since the libstdc++5 package is installed, I didn't see any obvious reason why I was still getting this error. I tried removing and installing from a different source, but the error persisted. After a useful soul on IRC helped me poke around, I finally realized that libstdc++.so.5 exists in /usr/lib/ and in /usr/lib64, but the libstc++5 package apparently does not install anything in /usr/lib32. The following illustrates:
```
$ ls -l /usr/lib/libstdc++*
lrwxrwxrwx 1 root root      18 2008-12-06 22:58 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829424 2008-05-07 07:12 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      19 2009-12-05 17:08 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r-- 1 root root 1027760 2009-10-15 03:11 /usr/lib/libstdc++.so.6.0.13

$ ls -l /usr/lib64/libstdc++*
lrwxrwxrwx 1 root root      18 2008-12-06 22:58 /usr/lib64/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829424 2008-05-07 07:12 /usr/lib64/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      19 2009-12-05 17:08 /usr/lib64/libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r-- 1 root root 1027760 2009-10-15 03:11 /usr/lib64/libstdc++.so.6.0.13

$ ls -l /usr/lib32/libstdc++*
lrwxrwxrwx 1 root root     19 2009-12-05 17:19 /usr/lib32/libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r-- 1 root root 962800 2009-10-15 03:11 /usr/lib32/libstdc++.so.6.0.13
```

The "lightscribeApplications-1.x.x.x-linux-2.6-intel.deb" package does come with a libstdc++.so.5 file, however, and it makes sense that it would be an appropriate version. My simple-minded workaround is thus to place a softlink in /usr/lib32/:
```
ln -s /opt/lightscribeApplications/common/Qt/libstdc++.so.5 /usr/lib32/libstdc++.so.5
```

Now the drive is detected and I can burn images on the LightScribe media. Respect to LaCie for their innovation, but thumbs down on their making the software closed source. :?

---

### Post by smartmeister on 2010-08-28
thanks, that's a usefull tips

---

