---
title: "Reinstalling Emacs Problems"
date: 2010-03-14
forum: General Help
---

### Post by cognizant-cog on 2010-03-14
Hey, guys. New to linux. I don't really know what I am doing when it comes to Emacs. I successfully set it up for java development (Which I have to use for class all the time). Then I successfully got SBCL working with it. Then I tried to get Clojure working with it, but never got it working (Where I could choose SBCL or Clojure with swank/slime(?)). After many attempts, I apparently screwed something up. When I had to do my next homework assignment in java, it wouldn't compile. Tried to use make to compile java. After many fruitless attempts, I decided to start from scratch. I deleted everything I could find pertaining to emacs. Now I can't reinstall it properly. When I try to through apt-get I get this message.

```

Setting up emacs-snapshot-bin-common (1:20090909-1) ...

Setting up emacs-snapshot (1:20090909-1) ...
update-alternatives: using /usr/bin/emacs-snapshot-gtk to provide /usr/bin/emacs-snapshot (emacs-snapshot) in auto mode.
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.3xOG0H
dpkg: error processing emacs-snapshot (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs22-gtk
 emacs-snapshot
E: Sub-process /usr/bin/dpkg returned an error code (1)


```What should I do? I don't know what these add-on packages are. Let me know if you guys need anymore info. Thanks.

---

### Post by Brandon Williams on 2010-03-16
Have you followed the instructions in the error message? Filing a bug report is a good idea when it tells you to do it.

In the mean time, you could also attach the specified file, /tmp/emacs-snapshot.3xOG0H, to this post so that we can try to figure out which add-on is causing trouble for you.

---

