---
title: "libgdk_pixbuf-2.0.so.0 fails on Natty 64-bit"
date: 2011-07-10
forum: General Help
---

### Post by jimbobboy on 2011-07-10
All:
I seem to have a problem with the shared 32-bit libraries used by 64-bit 11.04.

Several applications fail with similar symptoms, for example System->Admin->Printing.
Clicking on the menu just gets a spinner icon, then nothing.  Invoking the command line results in:

$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 31, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_simple_async_result_take_error

Here are the dependencies:

/usr/lib$ ldd -r libgdk_pixbuf-2.0.so.0
    linux-vdso.so.1 =>  (0x00007fff1c482000)
    libgio-2.0.so.0 => /usr/local/lib/libgio-2.0.so.0 (0x00007f6491bd0000)
    libgobject-2.0.so.0 => /usr/local/lib/libgobject-2.0.so.0 (0x00007f6491983000)
    libgmodule-2.0.so.0 => /usr/local/lib/libgmodule-2.0.so.0 (0x00007f649177e000)
    libgthread-2.0.so.0 => /usr/local/lib/libgthread-2.0.so.0 (0x00007f6491579000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f6491371000)
    libglib-2.0.so.0 => /usr/local/lib/libglib-2.0.so.0 (0x00007f649106d000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f6490de8000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f6490bca000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6490835000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f6490631000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f6490416000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f64901fd000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f649213c000)

I see that I have some locally installed libraries, but I am not sure if that's relevant, or what to do if it is.  I have reinstalled libgtk, ia32-libs, everything I can think of, with no results.

I believe this is a known bug in 11.04, but I can't get back to the bug report.  Can anyone point me to a fix or workaround?  Many Thanks!

---

