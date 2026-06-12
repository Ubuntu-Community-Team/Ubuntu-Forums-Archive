---
title: "How to set ubuntu to boot to runlevel 3?"
date: 2006-04-29
forum: General Help
---

### Post by johnpipe on 2006-04-29
Hi, due to lack of video driver support for the ATI Mach64 PCI (AGP only version is supported by X.org), I need to put ubuntu into runlevel 3, i.e., multi-user w/o X.

 I thought it would be adequate to change the default runlevel in /etc/inittab, but this isn't enough.  Ubuntu still tries to boot gdm,  and I haven't yet figured out where to make the necessary changes.  

One other thing with regard to X, is it possible/practical to change ubuntu to use XFree86 (which does support the older PCI video cards) instead of X.org? If so, any hints on how to go about this?

I also want to set 'dmesg n 1' on initialization to prevent constant kernel messages to the console complaining about " the cd drive seems confused", which continually happens  when there's no cd's in the drives, which is most of the time!  I don't see the equivalent of rc.local as in redhat, so where does one put one's own init commands in ubuntu/debian?

Thanks in advance,

Johnpipe

---

### Post by Ensnared on 2006-04-29
You'll first have to configure runlevel 3 to not use X, since all runlevels (except 0, 1 and 6) are initially configured alike in Ubuntu.

I wrote a full explanation on how to do this in [another thread](http://ubuntuforums.org/showthread.php?t=166390) - the post in question is [here](http://ubuntuforums.org/showpost.php?p=959527&postcount=3).

In addition to this you edit /etc/inittab to change the default, or course.

I doubt it's practical to install XFree86 on Ubuntu, but I suppose it's possible somehow. I wouldn't know where to begin though, but chances are deb-packages from Debian wouldn't work due to dependencies (though I may be wrong), but I suppose you could still install it manually following the [instructions](http://www.xfree86.org/4.5.0/Install.html) on [www.xfree86.org](www.xfree86.org).

As for rc.local, I don't really know where that is, but I'd like to know that too ;)

---

