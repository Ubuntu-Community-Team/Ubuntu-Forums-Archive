---
title: "Trying to get Palantir works"
date: 2009-11-13
forum: General Help
---

### Post by tunyawat on 2009-11-13
Palantir is a program that allow you to stream the video from your webcam over the internet. In my opinion, it is the simplest webcam-server program in the internet.  I personally use it to monitor my office in other locations.

Currently I use palantir on Puppy linux which can be easily installed through the pet package. However, I could not find any deb package of palantir.

I downloaded the binary package for i386 and extract it to /user/local/share/ using GUI frontend. I expected it to be executed whenever I type in the command as I do in Puppy Linux, however, it didn't work. It keeps reporting command not found.

Compiling from source is too advance for me and I could not do it. I get the errors like these.

```
x11mon.c:39: error: &#8216;id&#8217; undeclared (first use in this function)
x11mon.c:40: warning: implicit declaration of function &#8216;Imlib_paste_image&#8217;
x11mon.c:40: error: &#8216;win&#8217; undeclared (first use in this function)
x11mon.c:41: warning: implicit declaration of function &#8216;Imlib_kill_image&#8217;
x11mon.c:42: error: &#8216;disp&#8217; undeclared (first use in this function)
x11mon.c:42: error: &#8216;False&#8217; undeclared (first use in this function)
```

I really have no idea which library I should pre-install.

So, if you have any idea on
- where to find the deb package of palantir, or
- what I did wrong with the binary package, or
- how to compile the palantir

Please help!


[http://www.fastpath.it/products/palantir/download.html](http://www.fastpath.it/products/palantir/download.html)

---

