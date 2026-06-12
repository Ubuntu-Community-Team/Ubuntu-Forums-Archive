---
title: "Skype: no video for some contact since 10.10"
date: 2010-11-07
forum: General Help
---

### Post by jesuisbenjamin on 2010-11-07
Hello there,

Since i migrated from 10.04 to 10.10, video input from some of my contacts does not work (i get a blank / transparent areas instead). The funny thing is that it's not the case for all of my contacts. I know from experience that their video output is working fine since i could see them in 10.04.

Any ideas as to what can cause this? Could it be conflict with Compiz?

Thanks.
Benjamin

---

### Post by sean.bailey00 on 2011-03-31
I am actually having this same issue running 64-bit 10.10.  Skype worked fine in 10.04, and sending video works fine, but for some reason whenever a contact tries to send me video, I get a white translucent background.  I haven't had time to play around with it that much yet, but any advice would be appreciated.

---

### Post by TaffyDownUnder on 2011-04-24
I'm having the same problem; Contacts can see my video but I can't see there's.
If I use skype on windows 7 machine Skype works fine.

I'm currently using the following to launch skype:
  LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
If I don't specify the .so library video doesn't work in skype at all.

I'm using the following:
Ubuntu 10.10 (64bit)
Logitech WebCam Pro 9000
Skype version 2.2.0.25

I've also tried using the above with v4l2convert.so  from the command line and the results were the same here is what was output after I started skype:
522:/usr/bin> LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

(<unknown>:24172): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:24172): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:24172): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:24172): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:24172): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:24172): Gtk-WARNING **: Loading IM context type 'ibus' failed
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
libv4l2: error dequeuing buf: Device or resource busy
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!

---

### Post by TaffyDownUnder on 2011-04-24
OK the following fixed it for me. I created a file (skype_fix.sh) with the following in it:

#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
export LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so 
skype &
exit 0

I made this script file executable (chmod a+x skype_fix.sh) and I run this rather than skype directly and now both my contacts and I can see each other.

NOTE: this is for 64 bit Ubuntu (10.10) your mileage may vary.

see also: [http://imyy.net/no-video-with-skype-in-ubuntu/](http://imyy.net/no-video-with-skype-in-ubuntu/)

---

