---
title: "hoary problems with xorg and fglrx"
date: 2005-02-02
forum: General Help
---

### Post by snowcrash on 2005-02-02
Hello,

this is my first post here :). Yesterday i've installed Ubuntu hoary (i was happily using warty in another two computers) in my laptop (Dell Inspiron 8500 with ATI Mobility 9000). All gone fine until I've tried to enable 3D acceleration through fglrx  #-o .

I make the steps told in:
[http://www.ubuntuforums.org/showthread.php?t=13342&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=13342&highlight=fglrx)

X doesn't start and output this log error :

...
(II) Initializing built-in extension XEVIE

Fatal server error:
__glXExtensionInit: AddExtensions failed

Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org) for help.

I think this is a problem related with xmesa-gl but i don't know what happens exactly.

I've also read that fglrx must use its own libGL* files and with dpkg I see this:
/usr/lib
/usr/X11R6/lib/libGL.so.1
el paquete desvía otros a: /usr/X11R6/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib/libGL.so.1
el paquete desvía otros a: /usr/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib/libGL.so.1.2
el paquete desvía otros a: /usr/lib/fglrx/libGL.so.1.2.xlibmesa


It's is ok ?

Thanks :P. 

Note: If I comment line "GLCore" in xorg.conf  the server starts fine but with no 3D acceleration.

---

### Post by xophos on 2005-02-28
Hello, 
as far as i know, anything below radeon 9200 is not supported by fglrx, but ought to work using the open source dri-drivers which ought to be used by default. if not try to put "radeon" instead of "fglrx" as driver into your xorg.conf and remove (if any) the options added especially for fglrx.

---

