---
title: "Many standard utilities fall with &quot;Bus error&quot;"
date: 2009-11-05
forum: General Help
---

### Post by 0x656b694d on 2009-11-05
Hello,
i just installed 9.10. Everything worked fine from LiveCD. But after installing and updating i get 'Bus error' trying to do things like configure printer or menus.
Also, i got frozen desktop wallpaper. I mean it doesn't react on mouse events and doesn't load my wallpaper image (keeps the logon one). Nautilus works fine though.
> 
$ uname -a
Linux metallica 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

I also get tons of the following errors in dmesg:
> 
[  115.852455] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  115.852463] end_request: I/O error, dev sda, sector 133554689

(while fsck says there are no problems)

What can i do?

These are my pci devices:
> 
$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)


Thanks.

---

### Post by 0x656b694d on 2009-11-05
in addition, Lightning thunderbird addon doesn't work &#8212; it doesn't show the current date and is not able to create or import calendars (inactive menu items).

---

### Post by 0x656b694d on 2009-11-05
well, if i run nautilus from command line, i get the Bus error as well.
But folder browser works.

---

### Post by AubreyCTTX on 2009-11-05
I ran into this same problem last night with FireFox (it wouldn't start from the icon and running at the command line gave "Bus error").  I found someone else out there who had the same problem and in his case he replaced the xulrunner packages and it fixed the problem.  I tried it and it fixed the problem for me as well.  Might be worth a try.

---

### Post by 0x656b694d on 2009-11-05
firefox and other mozilla stuff work fine here. But i tried to reinstall them anyway with no success.

i tried to run nautilus under gdb, and got the following:
```

Program received signal SIGBUS, Bus error.
0x0100fe01 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
(gdb) bt
#0  0x0100fe01 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#1  0x0101016a in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#2  0x01017054 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#3  0x01018c8f in gtk_icon_theme_get_icon_sizes () from /usr/lib/libgtk-x11-2.0.so.0
#4  0x0117debe in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#5  0x0117e20f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x01181422 in gtk_window_set_icon_name () from /usr/lib/libgtk-x11-2.0.so.0
#7  0x080a6960 in ?? ()
#8  0x080a25b1 in ?? ()
#9  0x0815958d in ?? ()
#10 0x080b5458 in ?? ()
#11 0x08199834 in ?? ()
#12 0x080fa855 in ?? ()
#13 0x080fed84 in ?? ()
#14 0x003b70f1 in ?? () from /lib/libglib-2.0.so.0
#15 0x003b8e78 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#16 0x003bc720 in ?? () from /lib/libglib-2.0.so.0
#17 0x003bcb8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#18 0x010494a9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x0808185f in ?? ()
#20 0x01ac3b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0x0806c131 in ?? ()

```

---

### Post by 0x656b694d on 2009-11-05
with debug info:
```

Program received signal SIGBUS, Bus error.
find_image_offset (cache=<value optimized out>, 
    icon_name=<value optimized out>, directory_index=2)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkiconcache.c:246
246	/build/buildd/gtk+2.0-2.18.3/gtk/gtkiconcache.c: No such file or directory.
	in /build/buildd/gtk+2.0-2.18.3/gtk/gtkiconcache.c
(gdb) bt
#0  find_image_offset (cache=<value optimized out>, 
    icon_name=<value optimized out>, directory_index=2)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkiconcache.c:246
#1  0x00e4e16a in _gtk_icon_cache_get_icon_flags (cache=0x829b478, 
    icon_name=0x8500208 "user-desktop", directory_index=2)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkiconcache.c:283
#2  0x00e55054 in theme_dir_get_icon_suffix (dir=<value optimized out>, 
    icon_name=0x8500208 "user-desktop", has_icon_file=0x0)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkicontheme.c:2069
#3  0x00e56c8f in IA__gtk_icon_theme_get_icon_sizes (icon_theme=0x820ac40, 
    icon_name=0x8500208 "user-desktop")
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkicontheme.c:1679
#4  0x00fbbebe in icon_list_from_theme (widget=<value optimized out>, 
    name=<value optimized out>)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkwindow.c:3187
#5  0x00fbc20f in gtk_window_realize_icon (window=0x8295028)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkwindow.c:3247
#6  0x00fbf422 in IA__gtk_window_set_icon_name (window=0x8295028, 
    name=0x850e400 "user-desktop")
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkwindow.c:3525
#7  0x080a6960 in ?? ()
#8  0x080a25b1 in ?? ()
#9  0x0815958d in ?? ()
#10 0x080b5458 in ?? ()
#11 0x08199834 in ?? ()
#12 0x080fa855 in ?? ()
#13 0x080fed84 in ?? ()
#14 0x007750f1 in ?? () from /lib/libglib-2.0.so.0
#15 0x00776e78 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#16 0x0077a720 in ?? () from /lib/libglib-2.0.so.0
#17 0x0077ab8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#18 0x00e874a9 in IA__gtk_main ()
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkmain.c:1218
#19 0x0808185f in ?? ()
#20 0x05b73b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0x0806c131 in ?? ()

```

---

### Post by 0x656b694d on 2009-11-05
filed a bug on gtk+
[https://bugzilla.gnome.org/show_bug.cgi?id=600869](https://bugzilla.gnome.org/show_bug.cgi?id=600869)

---

### Post by 0x656b694d on 2009-11-06
fixed by reinstalling the system.
with all updates works fine now.

---

