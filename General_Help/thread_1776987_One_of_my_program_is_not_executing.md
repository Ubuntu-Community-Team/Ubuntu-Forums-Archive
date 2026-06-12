---
title: "One of my program is not executing"
date: 2011-06-07
forum: General Help
---

### Post by SharjeelHKh on 2011-06-07
Hi all,

I m new in community. I m using ubuntu 10.04.
I have install flightgear Scenery designer(fgsd) and it executed successfully, but during working on it I selected any option of it and fgsd crashed. After that it is not getting execute. Throwing following error on console.

buffer overflow detected ***: fgsd terminated

What possibly cause of this problem??, Any suggestion

---

### Post by SharjeelHKh on 2011-06-07
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0xed2390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0xed12ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0xed0a08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0xe59afe]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xe24)[0xe2da34]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0xed0abd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xed09fd]
/usr/local/lib/libflu.so(_ZN12Flu_Progress4drawEv+0xd1)[0xbe5a01]
/usr/lib/libfltk.so.1.1(_ZNK8Fl_Group10draw_childER9Fl_Widget+0x64)[0x2cfd04]
/usr/lib/libfltk.so.1.1(_ZN8Fl_Group13draw_childrenEv+0x5f)[0x2cfdef]
/usr/lib/libfltk.so.1.1(_ZN8Fl_Group4drawEv+0x3a)[0x2cff1a]
/usr/lib/libfltk.so.1.1(_ZN9Fl_Window4drawEv+0x5f)[0x3059af]
/usr/lib/libfltk.so.1.1(_ZN9Fl_Window5flushEv+0x42)[0x2b8192]
/usr/lib/libfltk.so.1.1(_ZN2Fl5flushEv+0xab)[0x2b98bb]
/usr/lib/libfltk.so.1.1(_ZN2Fl4waitEd+0x16c)[0x2b9b9c]
/usr/lib/libfltk.so.1.1(_ZN2Fl5checkEv+0x1c)[0x2b9c3c]
fgsd[0x8082033]
fgsd[0x80af4e1]
fgsd[0x8081e9e]
fgsd[0x8081fd9]
/usr/lib/libfltk.so.1.1(_ZN2Fl4waitEd+0x9e)[0x2b9ace]
/usr/lib/libfltk.so.1.1(_ZN2Fl3runEv+0x34)[0x2b9ce4]
fgsd[0x80725c9]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xe06bd6]
fgsd[0x8053051]

---

