---
title: "Help with liferea"
date: 2009-07-16
forum: General Help
---

### Post by junejune0605 on 2009-07-16
Hi, 

Im having issues running liferea, it will show that its starting, but then shuts down. I was able to get the log but I dont know how to decode it.

Please help,

Thanks!

junior@junior-laptop:~$ ulimite -c unlimited
bash: ulimite: command not found
junior@junior-laptop:~$ ulimite -c unlimited
bash: ulimite: command not found
junior@junior-laptop:~$ ulimit -c unlimited
junior@junior-laptop:~$ liferea
ls: cannot access /usr/lib/xulrunner-1.9*/libsqlite3.so.0: No such file or directory
dirname: missing operand
Try `dirname --help' for more information.

** ERROR **: Failure while preparing statement, (error=11, database disk image is malformed) SQL: "SELECT COUNT(*) FROM sqlite_master WHERE type = 'table' AND name = 'info';"
aborting...
Aborted (core dumped)
junior@junior-laptop:~$ gdb liferea-bin core
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)

warning: Can't read pathname for load map: Input/output error.
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libsqlite3.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsqlite3.so.0
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libglade-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglade-2.0.so.0
Reading symbols from /usr/lib/libgtk-x11-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgtk-x11-2.0.so.0.1600.1...done.
done.
Loaded symbols for /usr/lib/libgtk-x11-2.0.so.0
Reading symbols from /usr/lib/libxml2.so.2...Reading symbols from /usr/lib/debug/usr/lib/libxml2.so.2.6.32...done.
done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libgdk-x11-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgdk-x11-2.0.so.0.1600.1...done.
done.
Loaded symbols for /usr/lib/libgdk-x11-2.0.so.0
Reading symbols from /usr/lib/libatk-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libatk-1.0.so.0.2609.1...done.
done.
Loaded symbols for /usr/lib/libatk-1.0.so.0
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgdk_pixbuf-2.0.so.0.1600.1...done.
done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /lib/tls/i686/cmov/libm.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libpango-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpango-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgmodule-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libSM.so.6...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libX11.so.6...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libdbus-glib-1.so.2...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /usr/lib/libgobject-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgobject-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libglib-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgnutls.so.26...done.
Loaded symbols for /usr/lib/libgnutls.so.26
Reading symbols from /lib/libz.so.1...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /lib/libgcrypt.so.11...done.
Loaded symbols for /lib/libgcrypt.so.11
Reading symbols from /lib/tls/i686/cmov/libc.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libgthread-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgthread-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /usr/lib/libORBit-2.so.0...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /lib/libdbus-1.so.3...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangoft2-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangocairo-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libgio-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgio-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...Reading symbols from /usr/lib/debug/usr/lib/libfontconfig.so.1.3.0...done.
done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libXext.so.6...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libXrender.so.1...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libXinerama.so.1...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXi.so.6...done.
Loaded symbols for /usr/lib/libXi.so.6
Reading symbols from /usr/lib/libXrandr.so.2...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXcursor.so.1...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libXcomposite.so.1...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libpixman-1.so.0...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libdirectfb-1.0.so.0...done.
Loaded symbols for /usr/lib/libdirectfb-1.0.so.0
Reading symbols from /usr/lib/libfusion-1.0.so.0...done.
Loaded symbols for /usr/lib/libfusion-1.0.so.0
Reading symbols from /usr/lib/libdirect-1.0.so.0...done.
Loaded symbols for /usr/lib/libdirect-1.0.so.0
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /usr/lib/libxcb.so.1...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /lib/libpcre.so.3...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /lib/libuuid.so.1...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /usr/lib/libtasn1.so.3...done.
Loaded symbols for /usr/lib/libtasn1.so.3
Reading symbols from /lib/libgpg-error.so.0...done.
Loaded symbols for /lib/libgpg-error.so.0
Reading symbols from /lib/libselinux.so.1...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/libexpat.so.1...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so...done.
Loaded symbols for /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
Reading symbols from /usr/lib/libcanberra-gtk.so.0...done.
Loaded symbols for /usr/lib/libcanberra-gtk.so.0
Reading symbols from /usr/lib/libcanberra.so.0...done.
Loaded symbols for /usr/lib/libcanberra.so.0
Reading symbols from /usr/lib/libvorbisfile.so.3...done.
Loaded symbols for /usr/lib/libvorbisfile.so.3
Reading symbols from /usr/lib/libvorbis.so.0...done.
Loaded symbols for /usr/lib/libvorbis.so.0
Reading symbols from /usr/lib/libogg.so.0...done.
Loaded symbols for /usr/lib/libogg.so.0
Reading symbols from /usr/lib/libtdb.so.1...done.
Loaded symbols for /usr/lib/libtdb.so.1
Reading symbols from /usr/lib/libltdl.so.7...done.
Loaded symbols for /usr/lib/libltdl.so.7
Reading symbols from /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so...Reading symbols from /usr/lib/debug/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so...done.
done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
Core was generated by `/usr/bin/liferea-bin'.
Program terminated with signal 6, Aborted.
[New process 7301]
#0  0xb7fde430 in __kernel_vsyscall ()
(gdb) bt
#0  0xb7fde430 in __kernel_vsyscall ()
#1  0xb739f6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb73a1098 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7636eac in IA__g_logv (log_domain=0x0, log_level=G_LOG_LEVEL_ERROR, 
    format=0x809cdb0 "Failure while preparing statement, (error=%d, %s) SQL: \"%s\"", args1=0xbfcf991c "\v")
    at /build/buildd/glib2.0-2.20.1/glib/gmessages.c:506
#4  0xb7636ee6 in IA__g_log (log_domain=0x0, log_level=G_LOG_LEVEL_ERROR, 
    format=0x809cdb0 "Failure while preparing statement, (error=%d, %s) SQL: \"%s\"") at /build/buildd/glib2.0-2.20.1/glib/gmessages.c:526
#5  0x08061e9d in ?? ()
#6  0x080625e8 in ?? ()
#7  0x08062970 in db_init ()
#8  0x08075ebc in main ()
(gdb)

---

