---
title: "error while loading shared libraries: libmms.so.0: wrong ELF class: ELFCLASS64"
date: 2012-09-04
forum: General Help
---

### Post by BlackoutWorm on 2012-09-04
Hello. I'm trying to install and older version of boxee, and errors are of course expected since it hasn't been touched in awhile (linux version that is).
So do any of you guys know how to solve this problem?
```
error while loading shared libraries: libmms.so.0: wrong ELF class: ELFCLASS64

```

---

### Post by drmrgd on 2012-09-04
The error looks like the library is for the wrong architecture (i.e. the library is 64-bit and you need a 32-bit library).  Having a quick look around the web for that library, I came across this:

[http://forums.boxee.tv/showthread.php?t=50664&](http://forums.boxee.tv/showthread.php?t=50664&)

I don't know if it helps or not, but it does seem like you need to set up a 32-bit chroot environment to get it working on your 64-bit system.  Having never played with Boxee, though, I can't really confirm, though.

EDIT:  Just found this.  It's quite an old post, but it still seems potentially relevant, if for nothing else than pointing you in the right direction to making sure you have the right architecture libraries (might just be sure there's not a more updated way to go about it):

[http://ubuntuforums.org/showpost.php?p=7943304&postcount=9](http://ubuntuforums.org/showpost.php?p=7943304&postcount=9)

---

### Post by BlackoutWorm on 2012-09-04
Thanks, but none of them worked.
Old dependencies and packages, and dead download links.
Downloaded the 32bit packages of boxee as I couldn't find any 64 bit debs.
Replaced the dependencies libmysqlclient16 to libmysqlclient18 and libxmlrpc-c3 with libxmlrpc-core-c3. This is probably why I get this error. Not sure though. But these were the only alternatives I could find in synaptic.

For the libmms0 error, I though php5 and libmm would fix it, but no.
I really wish ubuntu would stop changing and removing old packages from the packages for each release and repository.
Just because they are outdated, they're pretty useful in these cases.
Okay, so do any of you guys have any idea how to fix this?
And don't give me that "use xbmc".
I need bocee for slingbox and netflix streaming

---

### Post by drmrgd on 2012-09-05
Just had another quick look around the web as I'm a bit curious about this software and its applications.  Unfortunately, it looks like you're stuck as there is no 64-bit version of the software, and it does not look like they're planning on developing it anytime soon.  That leaves you with two options as I see it:

1. Set up a 32-bit chroot environment where you can install the 32-libraries needed for the Boxee install.  I've never done this, and the best info I have is from the first link I posted above.  Seems like it's doable, although a bit of a hassle.

2.  Just a guess and this is riddled with some potential problems too, but maybe you can install it in a VM running a 32-bit version of Ubuntu?  I'm not sure how the hardware resources will be handled and it may end up that you don't get very good quality or some other issues pop up.  But, this (in theory) should work.

3.  Go with XBMC.  I know you seem opposed to it (and this is another bit of software I lack experience with - although I may play around with it tonight as it seems interesting!), but looking around the web, it does seem like there's support for both Netflix streaming and using Slingbox.  Have you tried it and found that it won't work for you?  It seems that XBMC is at least in development and new updates seem to bring new functionality, and to me this seems like the most straightforward way to go (again without knowing the limitations of the package and what you need to do).

At any rate, I don't think setting up Boxee in your 64-bit environment is going to be a cake walk.  Sorry no better solutions!

---

### Post by BlackoutWorm on 2012-09-05
I actually found a copy of the getlibs package, but unforgettably it wouldn't solve the problem like chroot environment guide said it will. And no surprise there actually, since this mod is for 11.10.
I've tried 2 different versions of boxee which have been modded for ubuntu 11.10. They both depend on i386 dependencies that is not in the rop and not even in the getlibs fix.

So for now I'm completely stuck here,
If anyone who know how this works can help me with this, please do.

---

### Post by BlackoutWorm on 2012-09-08
**[size="4"][color="blue"]bump[/color][/size]**

---

