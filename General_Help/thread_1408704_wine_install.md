---
title: "wine install"
date: 2010-02-16
forum: General Help
---

### Post by metadrop on 2010-02-16
I am not getting an error while installing WINE but after install it will not start... It is in the menu, first is the error after install.. second is the install.. I have tried to install the package aevery way possible what am I doing wrong! :(

```
metadrop@metabox:/tmp$ wine
bash: /usr/bin/wine: Input/output error
metadrop@metabox:/tmp$ 
``````

metadrop@metabox:/tmp$ sudo dpkg -i --force-all wine1.2_1.1.31-0ubuntu3_amd64.deb
Selecting previously deselected package wine1.2.
(Reading database ... 155687 files and directories currently installed.)
Unpacking wine1.2 (from wine1.2_1.1.31-0ubuntu3_amd64.deb) ...
Setting up wine1.2 (1.1.31-0ubuntu3) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0

Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /lib/ld-linux.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libpthread.so.0 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_dns-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/ld-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_hesiod-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libresolv.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libcidn.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_files-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libanl-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_nisplus.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libthread_db.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libdl.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_nis-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libpthread-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/librt-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_nisplus-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libBrokenLocale-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libanl.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libpcprofile.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libcidn-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libm.so.6 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libthread_db-1.0.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_files.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/librt.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnsl.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libcrypt-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libc.so.6 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libm-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_nis.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_dns.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libcrypt.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_compat.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libdl-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libc-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libmemusage.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_hesiod.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libresolv-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libutil-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/ld-linux.so.2 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnsl-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libnss_compat-2.10.1.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libSegFault.so is empty, not checked.
/sbin/ldconfig.real: File /lib32/libBrokenLocale.so.1 is empty, not checked.
/sbin/ldconfig.real: File /lib32/libutil.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libxvidcore.so.4.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libavutil.so.49.15.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libavutil.so.49 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libfaac.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp4.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp3lame.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libfaac.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp4.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp4v2.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp4v2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmp3lame.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libxvidcore.so.4 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libgsm.so.1.0.12 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libgsm.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib32/libgcc_s.so.1 is empty, not checked.
metadrop@metabox:/tmp$ 


```

---

### Post by mechro on 2010-02-16
The "wine" command is applied to the application you want to run e.g. wine closedsourcethingy.exe

If you've just installed wine you can configure it with winecfg. If wine is in your menu then there should be a configure wine item.

---

### Post by metadrop on 2010-02-16
It is in the menu but will not launch..

```

metadrop@metabox:~$ winecfg
exec: 29: /usr/bin/wine: Input/output error
metadrop@metabox:~$ 

```

any other suggestions?

---

### Post by mechro on 2010-02-16
... a couple of wild guesses... 

64-bit isn't working, try 32-bit?

You have compiz enabled and it's causing a conflict?

Sorry for being so unhelpful.

Has the .wine folder been installed in your home directory? Notepad.exe should be in there in /drive_c/windows... try running that in wine.

---

### Post by metadrop on 2010-02-16
I have tried both and I cannot find notepad anywhere on the system... giving up now :D

---

