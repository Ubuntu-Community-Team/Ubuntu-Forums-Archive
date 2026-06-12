---
title: "Firefox 3.5 segmentation fault"
date: 2009-06-30
forum: General Help
---

### Post by ggtsu on 2009-06-30
I just tried installing firefox 3.5 (apt-get install firefox-3.5), but whenever I try starting it, I get a segmentation fault. I tried removing the package and then tried [these]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html") instructions, but no dice. Any ideas?

---

### Post by arglborps on 2009-07-07
This appears to be caused (at least on Jaunty 64bit) by the GNOME global menu applet that enables a unified menu bar on top of the screen (like Mac OS X).

If you remove it from the panel Firefox 3.5 should launch normally.

---

### Post by theApokalypsis on 2009-07-08
> **arglborps said:**
> This appears to be caused (at least on Jaunty 64bit) by the GNOME global menu applet that enables a unified menu bar on top of the screen (like Mac OS X).

If you remove it from the panel Firefox 3.5 should launch normally.

Gah!!

Way to point out the obvious. Holy hell I have been combing for some time. As if it was that little thing.

:D disabled it, works great, flash and everything!

Thanks!

:guitar:

---

### Post by Stormx on 2009-07-21
Just bumping to give this thread some attention. This issue needs to be looked at. I'ma submit a firefox bug report. I know there's already a globalmenu bug report.

---

### Post by Lukian on 2009-08-10
Is there a solution for this yet?

[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=401#makechanges](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=401#makechanges) (from [https://bugs.launchpad.net/firefox/+bug/347519](https://bugs.launchpad.net/firefox/+bug/347519) )
Seems to suggest removing any packages still using xulrunner-1.8, I have no idea what packages these would be under Ubuntu 9.04.

---

### Post by kylea on 2009-09-30
The fix for this is on the PPA

[https://edge.launchpad.net/~sushkov/+archive/personal](https://edge.launchpad.net/~sushkov/+archive/personal)



This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources. (Read about installing)

deb [http://ppa.launchpad.net/sushkov/personal/ubuntu](http://ppa.launchpad.net/sushkov/personal/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/sushkov/personal/ubuntu](http://ppa.launchpad.net/sushkov/personal/ubuntu) jaunty main 

Signing key:
    1024R/16C248F7 (What is this?) 
Fingerprint:
    9C550E7DF1A7C18E11CF6FA80845425716C248F7

Dependencies:

    * PPA for Vala Team (included on 2009-09-07)

---

### Post by crashedster on 2009-09-30
> **kylea said:**
> The fix for this is on the PPA

[https://edge.launchpad.net/~sushkov/+archive/personal](https://edge.launchpad.net/~sushkov/+archive/personal)



This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources. (Read about installing)

deb [http://ppa.launchpad.net/sushkov/personal/ubuntu](http://ppa.launchpad.net/sushkov/personal/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/sushkov/personal/ubuntu](http://ppa.launchpad.net/sushkov/personal/ubuntu) jaunty main 

Signing key:
    1024R/16C248F7 (What is this?) 
Fingerprint:
    9C550E7DF1A7C18E11CF6FA80845425716C248F7

Dependencies:

    * PPA for Vala Team (included on 2009-09-07)
kylea,

unfortunatelly your fix doesn't work for me.

here is the gdb bt output:
(gdb) bt
#0  0x00007fcb380a605b in raise () from /lib/libpthread.so.0
#1  0x00007fcb3521d488 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#2  <signal handler called>
#3  0x00007fcb32a06679 in g_object_ref () from /usr/lib/libgobject-2.0.so.0
#4  0x00007fcb2ae858ea in global_menu_gtk_changed_eh () from /usr/lib/gtk-2.0/modules/libglobalmenu-gnome.so
#5  0x00007fcb32a193d1 in ?? () from /usr/lib/libgobject-2.0.so.0
#6  0x00007fcb32a1ace9 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#7  0x00007fcb32a1b054 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#8  0x00007fcb2ae89d9b in ?? () from /usr/lib/gtk-2.0/modules/libglobalmenu-gnome.so
#9  0x00007fcb3276c2cb in ?? () from /lib/libglib-2.0.so.0
#10 0x00007fcb3276bbbe in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#11 0x00007fcb3276f588 in ?? () from /lib/libglib-2.0.so.0
#12 0x00007fcb3276f6b0 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#13 0x00007fcb3594c12b in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#14 0x00007fcb3594c289 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#15 0x00007fcb359f2d57 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#16 0x00007fcb359c8553 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#17 0x00007fcb3594c375 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#18 0x00007fcb35823448 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#19 0x00007fcb35218f5f in XRE_main () from /usr/lib/xulrunner-1.9.1.3/libxul.so
#20 0x000000000040271f in ?? ()
#21 0x00007fcb370b3abd in __libc_start_main () from /lib/libc.so.6
#22 0x0000000000401f99 in ?? ()
#23 0x00007fffc8987e68 in ?? ()
#24 0x000000000000001c in ?? ()
#25 0x0000000000000001 in ?? ()
#26 0x00007fffc8988506 in ?? ()
#27 0x0000000000000000 in ?? ()

---

### Post by kylea on 2009-09-30
Thats unfortunate - what are the details of your system:

Ubuntu Version
Kernel etc
64bit / 32 Bit
Firefox

Mine are 
Karmic 64bit 
2.6.31-11-generic 
Firefox 3.5.3

---

### Post by LavianoTS386 on 2009-10-01
I have this same problem in Karmic

---

### Post by Dellfan on 2009-10-25
sigh... does not resolve for me either.

System info:

Upgraded from 9.04 (64 Bit) to 9.10 RC

Uname: 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
Firefox: 3.5.3
Globalmenu: 0.7.7-0~stas3

Was at 0.7.5-0ubuntu1~ppa1 before I tried Stas's personal build. Get exactly the same error on both... instant segfault on starting Firefox or Fennec. Disabling globalmenu resolves the issue.

bj

---

### Post by Dellfan on 2009-10-25
It now works!

After upgrading to Stas's personal build. I reran update-manager which then picked up a newer version in PPA. Updating to this results in a Globalmenu that plays nicely with Firefox. Not sure if the repo was just updated or installing Stas's personal build triggers something.

bj

---

