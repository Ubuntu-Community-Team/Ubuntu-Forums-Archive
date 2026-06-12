---
title: "Lucid 10.04 Problems and Comments With Fresh Install"
date: 2010-05-03
forum: General Help
---

### Post by redrockts on 2010-05-03
I have encountered a few problems with Lucid Lynx 10.04 with a fresh install. I decided not to install via an upgrade since I have read about problems with the upgrade route in prior versions. These are the problems I have encountered so far:

*1. A samba (network) share does not mount automatically from /etc/fstab during startup*.
This configuration worked fine in 9.10 without any intervention. I can manually use the terminal to issue the "sudo mount -a" command and it mounts without a problem.

*2. Keyboard shortcuts with many modifier keys do not work.*
I tried to assign "super-t" for opening a fresh terminal, but I get no response. This arrangement worked fine in 9.10. I have noticed a number of other complaints about this in the forums but have not found the definitive solution yet.

*3. Rhythmbox closes immediately upon launch.*
I get the following error messages when I try to start Rhythmbox from the command line:
[INDENT]"** (rhythmbox:1847): DEBUG: Loading the real store page

** (rhythmbox:1847): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DOzVOhGBIgaM8i047ZWQn%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1272931138%26oauth_token%3DnJttL20Mpb9WD1Mrrp5r%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&5L8gk671MD2M8l5gxfNDl978DCb9fq1Wd9KZbknXBzjhlKHJh9k2rhBhH7C4QrkXklRQ9DvXpWq9qtTn'

** (rhythmbox:1847): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=OzVOhGBIgaM8i047ZWQn&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1272931138&oauth_token=nJttL20Mpb9WD1Mrrp5r&oauth_verifier=None&oauth_version=1.0&oauth_signature=SaTYlKmO%2B3CZnSGP5VghLnSsnBY%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=OzVOhGBIgaM8i047ZWQn&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1272931138&oauth_token=nJttL20Mpb9WD1Mrrp5r&oauth_verifier=None&oauth_version=1.0&oauth_signature=SaTYlKmO%2B3CZnSGP5VghLnSsnBY%3D)
Segmentation fault>"
[/INDENT]The main window for Rhythmbox flashes on the screen for a moment before it closes with the error.

Has anyone else encountered these issues and knows the definitive solution?

Also, as a comment, I was not overly impressed with the default screen colors and arrangements. I quickly changed the theme to something more palatable... I am surprised to say that the brown from 9.10 may not have been so bad.

I hope your experiences with 10.04 have been successful, and I appreciate any thoughts or help on these issues.

---

### Post by redrockts on 2010-05-08
It does not appear this post has generated much interest or response. Well, I have found solutions for two of the problems, so I will post those in hopes someone finds them useful.

[I]"1. A samba (network) share does not mount automatically from /etc/fstab during startup.
This configuration worked fine in 9.10 without any intervention. I can manually use the terminal to issue the "sudo mount -a" command and it mounts without a problem."[/I]

SOLUTION: Add the option "_netdev" to the options section. This notifies the mounting service that this a network device and must wait for the network connection to be established before attempting to mount the share.

[I]"2. Keyboard shortcuts with many modifier keys do not work.
I tried to assign "super-t" for opening a fresh terminal, but I get no response. This arrangement worked fine in 9.10. I have noticed a number of other complaints about this in the forums but have not found the definitive solution yet."[/I]

NO SOLUTION YET.

*"3. Rhythmbox closes immediately upon launch."*

SOLUTION: I uninstall the Ubuntu One Store Rhythmbox plug-in from Synaptic and it works fine. (Sorry Ubuntu One...)

---

### Post by Noraphalem on 2010-05-08
I have the following problem with Rhythmbox:

After the start Rhythmbox closes immediately.

Terminal output:
```
florian@florian-laptop:~$ rhythmbox
*** glibc detected *** rhythmbox: munmap_chunk(): invalid pointer: 0x00007f813a743dd0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f813a42f5b6]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0x10d)[0x7f8123bfa15d]
/lib/libusb-0.1.so.4(usb_free_dev+0x9)[0x7f8123bf98c9]
/lib/libusb-0.1.so.4(usb_find_devices+0xce)[0x7f8123bf9c9e]
/usr/lib/libmtp.so.8(+0x1caf5)[0x7f8123e1daf5]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x1f)[0x7f8123e1f47f]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x7a08)[0x7f812404fa08]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x98)[0x7f813f7c9e98]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f813b4f95de]
/usr/lib/libgobject-2.0.so.0(+0x21598)[0x7f813b50d598]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x639)[0x7f813b50e8b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f813b50f033]
/usr/lib/librhythmbox-core.so.0(+0x5975a)[0x7f813f74c75a]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x20d)[0x7f813f74c9dd]
/usr/lib/librhythmbox-core.so.0(+0x481f5)[0x7f813f73b1f5]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f813ae408c2]
/lib/libglib-2.0.so.0(+0x42748)[0x7f813ae44748]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f813ae44c55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f813e99faf7]
rhythmbox(main+0x3cb)[0x403e8b]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f813a3d6c4d]
rhythmbox[0x403919]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:01 7079119                            /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:01 7079119                            /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:01 7079119                            /usr/bin/rhythmbox
00620000-01566000 rw-p 00000000 00:00 0                                  [heap]
7f8122951000-7f8122990000 r-xp 00000000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122990000-7f8122b90000 ---p 0003f000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b90000-7f8122b92000 r--p 0003f000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b92000-7f8122b93000 rw-p 00041000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b93000-7f8122b94000 rw-p 00000000 00:00 0 
7f8122b94000-7f8122b99000 r-xp 00000000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122b99000-7f8122d99000 ---p 00005000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d99000-7f8122d9a000 r--p 00005000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d9a000-7f8122d9b000 rw-p 00006000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d9b000-7f8122da9000 r-xp 00000000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122da9000-7f8122fa8000 ---p 0000e000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122fa8000-7f8122fa9000 r--p 0000d000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122fa9000-7f8122faa000 rw-p 0000e000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122faa000-7f8122fb2000 r-xp 00000000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8122fb2000-7f81231b1000 ---p 00008000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b1000-7f81231b2000 r--p 00007000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b2000-7f81231b3000 rw-p 00008000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b3000-7f81231c8000 r-xp 00000000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81231c8000-7f81233c7000 ---p 00015000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c7000-7f81233c8000 r--p 00014000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c8000-7f81233c9000 rw-p 00015000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c9000-7f81233d3000 r-xp 00000000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81233d3000-7f81235d2000 ---p 0000a000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d2000-7f81235d3000 r--p 00009000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d3000-7f81235d4000 rw-p 0000a000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d4000-7f81235e2000 r-xp 00000000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81235e2000-7f81237e2000 ---p 0000e000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e2000-7f81237e3000 r--p 0000e000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e3000-7f81237e4000 rw-p 0000f000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e4000-7f81237ec000 r-xp 00000000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81237ec000-7f81239eb000 ---p 00008000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239eb000-7f81239ec000 r--p 00007000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239ec000-7f81239ed000 rw-p 00008000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239ed000-7f81239f6000 r-xp 00000000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f81239f6000-7f8123bf6000 ---p 00009000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf6000-7f8123bf7000 r--p 00009000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf7000-7f8123bf8000 rw-p 0000a000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf8000-7f8123bff000 r-xp 00000000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123bff000-7f8123dfe000 ---p 00007000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123dfe000-7f8123dff000 r--p 00006000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123dff000-7f8123e01000 rw-p 00007000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123e01000-7f8123e3f000 r-xp 00000000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f8123e3f000-7f812403e000 ---p 0003e000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f812403e000-7f8124046000 r--p 0003d000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f8124046000-7f8124048000 rw-p 00045000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2Aborted
florian@florian-laptop:~$ 

```

---

### Post by afrodeity on 2010-05-24
> **Noraphalem said:**
> I have the following problem with Rhythmbox:

After the start Rhythmbox closes immediately.

Terminal output:
```
florian@florian-laptop:~$ rhythmbox
*** glibc detected *** rhythmbox: munmap_chunk(): invalid pointer: 0x00007f813a743dd0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f813a42f5b6]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0x10d)[0x7f8123bfa15d]
/lib/libusb-0.1.so.4(usb_free_dev+0x9)[0x7f8123bf98c9]
/lib/libusb-0.1.so.4(usb_find_devices+0xce)[0x7f8123bf9c9e]
/usr/lib/libmtp.so.8(+0x1caf5)[0x7f8123e1daf5]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x1f)[0x7f8123e1f47f]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x7a08)[0x7f812404fa08]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x98)[0x7f813f7c9e98]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f813b4f95de]
/usr/lib/libgobject-2.0.so.0(+0x21598)[0x7f813b50d598]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x639)[0x7f813b50e8b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f813b50f033]
/usr/lib/librhythmbox-core.so.0(+0x5975a)[0x7f813f74c75a]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x20d)[0x7f813f74c9dd]
/usr/lib/librhythmbox-core.so.0(+0x481f5)[0x7f813f73b1f5]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f813ae408c2]
/lib/libglib-2.0.so.0(+0x42748)[0x7f813ae44748]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f813ae44c55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f813e99faf7]
rhythmbox(main+0x3cb)[0x403e8b]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f813a3d6c4d]
rhythmbox[0x403919]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:01 7079119                            /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:01 7079119                            /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:01 7079119                            /usr/bin/rhythmbox
00620000-01566000 rw-p 00000000 00:00 0                                  [heap]
7f8122951000-7f8122990000 r-xp 00000000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122990000-7f8122b90000 ---p 0003f000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b90000-7f8122b92000 r--p 0003f000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b92000-7f8122b93000 rw-p 00041000 08:01 7081298                    /usr/lib/libibus.so.1.0.0
7f8122b93000-7f8122b94000 rw-p 00000000 00:00 0 
7f8122b94000-7f8122b99000 r-xp 00000000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122b99000-7f8122d99000 ---p 00005000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d99000-7f8122d9a000 r--p 00005000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d9a000-7f8122d9b000 rw-p 00006000 08:01 7085061                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8122d9b000-7f8122da9000 r-xp 00000000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122da9000-7f8122fa8000 ---p 0000e000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122fa8000-7f8122fa9000 r--p 0000d000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122fa9000-7f8122faa000 rw-p 0000e000 08:01 7230547                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8122faa000-7f8122fb2000 r-xp 00000000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8122fb2000-7f81231b1000 ---p 00008000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b1000-7f81231b2000 r--p 00007000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b2000-7f81231b3000 rw-p 00008000 08:01 7080957                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f81231b3000-7f81231c8000 r-xp 00000000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81231c8000-7f81233c7000 ---p 00015000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c7000-7f81233c8000 r--p 00014000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c8000-7f81233c9000 rw-p 00015000 08:01 7081353                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f81233c9000-7f81233d3000 r-xp 00000000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81233d3000-7f81235d2000 ---p 0000a000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d2000-7f81235d3000 r--p 00009000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d3000-7f81235d4000 rw-p 0000a000 08:01 7081337                    /usr/lib/libindicator.so.0.0.0
7f81235d4000-7f81235e2000 r-xp 00000000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81235e2000-7f81237e2000 ---p 0000e000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e2000-7f81237e3000 r--p 0000e000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e3000-7f81237e4000 rw-p 0000f000 08:01 7080955                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f81237e4000-7f81237ec000 r-xp 00000000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81237ec000-7f81239eb000 ---p 00008000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239eb000-7f81239ec000 r--p 00007000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239ec000-7f81239ed000 rw-p 00008000 08:01 7080811                    /usr/lib/libappindicator.so.0.0.0
7f81239ed000-7f81239f6000 r-xp 00000000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f81239f6000-7f8123bf6000 ---p 00009000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf6000-7f8123bf7000 r--p 00009000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf7000-7f8123bf8000 rw-p 0000a000 08:01 7230421                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8123bf8000-7f8123bff000 r-xp 00000000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123bff000-7f8123dfe000 ---p 00007000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123dfe000-7f8123dff000 r--p 00006000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123dff000-7f8123e01000 rw-p 00007000 08:01 15466680                   /lib/libusb-0.1.so.4.4.4
7f8123e01000-7f8123e3f000 r-xp 00000000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f8123e3f000-7f812403e000 ---p 0003e000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f812403e000-7f8124046000 r--p 0003d000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2
7f8124046000-7f8124048000 rw-p 00045000 08:01 7081418                    /usr/lib/libmtp.so.8.3.2Aborted
florian@florian-laptop:~$ 

```

1. Nautilus seg faults
```

Program received signal SIGSEGV, Segmentation fault.
0x00ffc935 in gtk_range_set_value () from /usr/lib/libgtk-x11-2.0.so.0

```

2. X server fails to start in recovery mode.

---

### Post by newb85 on 2010-05-25
> **redrockts said:**
> 

*"3. Rhythmbox closes immediately upon launch."*

SOLUTION: I uninstall the Ubuntu One Store Rhythmbox plug-in from Synaptic and it works fine. (Sorry Ubuntu One...)

I believe one could also rectify this problem by simply disabling the umusicstore plugin for rhythmbox in gconf-editor, as well.

---

