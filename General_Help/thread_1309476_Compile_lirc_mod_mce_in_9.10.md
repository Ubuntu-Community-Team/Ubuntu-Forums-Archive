---
title: "Compile lirc_mod_mce in 9.10"
date: 2009-11-01
forum: General Help
---

### Post by leeko on 2009-11-01
Hi all, I found this thread in the archive for Karmic testing. It's the exact same issue I have, and was posted by Ryanolf. That forum is now closed since the release of Karmic, so I'm reposting here instead. Thanks for any help you can offer.

Lee

---

...I'm trying to compile lirc_mod_mce in 9.10 Karmic
Following the how-to at [http://ubuntuforums.org/showpost.php...7&postcount=16](http://ubuntuforums.org/showpost.php...7&postcount=16), none of the versions of lirc_mod_mce compile:

make -C /lib/modules/2.6.31-13-generic/build SUBDIRS=/home/hotel63/Downloads/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-generic'
CC [M] /home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.o
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c: In function ‘unregister_from_lirc’:
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:612: error: implicit declaration of function ‘lirc_unregister_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:612: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:614: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:624: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:637: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:638: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c: In function ‘send_packet_to_lirc’:
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:686: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:688: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c: In function ‘usb_remote_probe’:
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1033: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1045: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1047: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1048: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1049: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1052: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1053: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1054: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1055: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1056: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1057: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1058: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1059: error: dereferencing pointer to incomplete type
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1064: error: implicit declaration of function ‘lirc_register_plugin’
/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.c:1089: error: dereferencing pointer to incomplete type
make[2]: *** [/home/hotel63/Downloads/lirc_mod_mce/lirc_mod_mce.o] Error 1
make[1]: *** [_module_/home/hotel63/Downloads/lirc_mod_mce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
make: *** [default] Error 2

This is with the lirc_dev.h that comes with 9.10. Have changes in LIRC broken lirc_mod_mce, which seems to be without development for some time. Anyone have any ideas? Do others experience this problem in Karmic? In Jaunty, I had no problems with compiling.

---

### Post by jon47 on 2010-07-23
I've solved this :-)

see [http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326](http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326)

Cheers
Jon

---

