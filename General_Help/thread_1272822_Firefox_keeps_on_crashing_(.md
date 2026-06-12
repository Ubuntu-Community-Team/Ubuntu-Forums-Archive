---
title: "Firefox keeps on crashing :("
date: 2009-09-22
forum: General Help
---

### Post by mahasmb on 2009-09-22
Can anyone possibly help me? Firefox keeps on crashing and I have no idea why. I've run it from the terminal and have pasted what the terminal outputted below. Please take a look.


```
maha@maha-desktop:~$ firefox
/home/maha/.themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/maha/.themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/maha/.themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/maha/.themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/maha/.themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
*** glibc detected *** /usr/lib/firefox-3.0.14/firefox: free(): invalid next size (fast): 0x0cdc33f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7db0604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7db25b6]
/usr/lib/xulrunner-1.9.0.14/libmozjs.so[0xb7d1eef3]
/usr/lib/xulrunner-1.9.0.14/libmozjs.so[0xb7cddb14]
/usr/lib/xulrunner-1.9.0.14/libmozjs.so(JS_GC+0x45)[0xb7cb975d]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb71eff18]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb79aaa6a]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb79aaba9]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb75a3032]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb75a3102]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb75a34b5]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb7979a14]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb7979ce2]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb74cb566]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb79a1b9e]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb79a1c13]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb799f6c8]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb796ff54]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb78f2e38]
/usr/lib/xulrunner-1.9.0.14/libxul.so[0xb77872b4]
/usr/lib/xulrunner-1.9.0.14/libxul.so(XRE_main+0x1d6b)[0xb71e4a8b]
/usr/lib/firefox-3.0.14/firefox[0x80491ab]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d57775]
/usr/lib/firefox-3.0.14/firefox[0x8048d11]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:12 2859867    /usr/lib/firefox-3.0.14/firefox
0804f000-08050000 r--p 00006000 08:12 2859867    /usr/lib/firefox-3.0.14/firefox
08050000-08051000 rw-p 00007000 08:12 2859867    /usr/lib/firefox-3.0.14/firefox
09aab000-0e838000 rw-p 09aab000 00:00 0          [heap]
a7200000-a7300000 rw-p a7200000 00:00 0 
a73e4000-a73e5000 ---p a73e4000 00:00 0 
a73e5000-a7be5000 rwxp a73e5000 00:00 0 
a83e6000-a83e7000 ---p a83e6000 00:00 0 
a83e7000-a8be7000 rwxp a83e7000 00:00 0 
a9ffc000-a9ffd000 r-xp 00000000 08:12 5423111    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
a9ffd000-a9ffe000 r--p 00000000 08:12 5423111    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
a9ffe000-a9fff000 rw-p 00001000 08:12 5423111    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
a9fff000-ac000000 rw-p a9fff000 00:00 0 
ac000000-ac058000 ---p ac000000 00:00 0 
ac058000-ac160000 rw-p ac058000 00:00 0 
ac160000-ad000000 rw-p ac160000 00:00 0 
ad000000-ad0ff000 rw-p ad000000 00:00 0 
ad0ff000-ad100000 ---p ad0ff000 00:00 0 
ad23b000-ad25e000 r--p 00000000 08:12 557169     /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ad2ff000-ad400000 rw-p ad2ff000 00:00 0 
ad400000-ad500000 rw-p ad400000 00:00 0 
ad5e8000-ad5e9000 ---p ad5e8000 00:00 0 
ad5e9000-adde9000 rwxp ad5e9000 00:00 0 
ade8f000-adf20000 rw-p ade8f000 00:00 0 
adf74000-adfba000 r--p 00000000 08:12 557151     /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
ae044000-ae0d0000 r--p 00000000 08:12 2508024    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
ae969000-ae96b000 r-xp 00000000 08:12 3211355    /lib/libnss_mdns4.so.2
ae96b000-ae96c000 rw-p 00001000 08:12 3211355    /lib/libnss_mdns4.so.2
ae987000-aea72000 rw-s 00000000 00:09 38764593   /SYSV00000000 (deleted)
aea72000-aea74000 r-xp 00000000 08:12 3211311    /lib/libkeyutils-1.2.so
aea74000-aea75000 r--p 00001000 08:12 3211311    /lib/libkeyutils-1.2.so
aea75000-aea76000 rw-p 00002000 08:12 3211311    /lib/libkeyutils-1.2.so
aea76000-aea7d000 r-xp 00000000 08:12 2378677    /usr/lib/libkrb5support.so.0.1
aea7d000-aea7e000 r--p 00006000 08:12 2378677    /usr/lib/libkrb5support.so.0.1
aea7e000-aea7f000 rw-p 00007000 08:12 2378677    /usr/lib/libkrb5support.so.0.1
aea7f000-aeaa1000 r-xp 00000000 08:12 2378669    /usr/lib/libk5crypto.so.3.1
aeaa1000-aeaa2000 r--p 00022000 08:12 2378669    /usr/lib/libk5crypto.so.3.1
aeaa2000-aeaa3000 rw-p 00023000 08:12 2378669    /usr/lib/libk5crypto.so.3.1
aeaa3000-aeb32000 r-xp 00000000 08:12 2378675    /usr/lib/libkrb5.so.3.3
aeb32000-aeb34000 r--p 0008e000 08:12 2378675    /usr/lib/libkrb5.so.3.3
aeb34000-aeb35000 rw-p 00090000 08:12 2378675    /usr/lib/libkrb5.so.3.3
aeb35000-aeb4b000 r-xp 00000000 08:12 2375817    /usr/lib/libsasl2.so.2.0.22
aeb4b000-aeb4c000 r--p 00015000 08:12 2375817    /usr/lib/libsasl2.so.2.0.22
aeb4c000-aeb4d000 rw-p 00016000 08:12 2375817    /usr/lib/libsasl2.so.2.0.22
aeb4d000-aec80000 r-xp 00000000 08:12 3222179    /lib/i686/cmov/libcrypto.so.0.9.8
aec80000-aec88000 r--p 00132000 08:12 3222179    /lib/i686/cmov/libcrypto.so.0.9.8
aec88000-aec95000 rw-p 0013a000 08:12 3222179    /lib/i686/cmov/libcrypto.so.0.9.8
aec95000-aec99000 rw-p aec95000 00:00 0 
aec99000-aecdb000 r-xp 00000000 08:12 3222181    /lib/i686/cmov/libssl.so.0.9.8
aecdb000-aecdc000 ---p 00042000 08:12 3222181    /lib/i686/cmov/libssl.so.0.9.8
aecdc000-aecdd000 r--p 00042000 08:12 3222181    /lib/i686/cmov/libssl.so.0.9.8
aecdd000-aece0000 rw-p 00043000 08:12 3222181    /lib/i686/cmov/libssl.so.0.9.8
aece0000-aed09000 r-xp 00000000 08:12 2378590    /usr/lib/libgssapi_krb5.so.2.2
aed09000-aed0a000 r--p 00028000 08:12 2378590    /usr/lib/libgssapi_krb5.so.2.2
aed0a000-aed0b000 rw-p 00029000 08:12 2378590    /usr/lib/libgssapi_krb5.so.2.2
aed0b000-aed4b000 r-xp 00000000 08:12 2375876    /usr/lib/libldap_r-2.4.so.2.4.1
aed4b000-aed4c000 ---p 00040000 08:12 2375876    /usr/lib/libldap_r-2.4.so.2.4.1
aed4c000-aed4d000 r--p 00040000 08:12 2375876    /usr/lib/libldap_r-2.4.so.2.4.1
aed4d000-aed4e000 rw-p 00041000 08:12 2375876    /usr/lib/libldap_r-2.4.so.2.4.1
aed4e000-aed4f000 rw-p aed4e000 00:00 0 
aed4f000-aed5b000 r-xp 00000000 08:12 2375875    /usr/lib/liblber-2.4.so.2.4.1
aed5b000-aed5c000 r--p 0000b000 08:12 2375875    /usr/lib/liblber-2.4.so.2.4.1
aed5c000-aed5d000 rw-p 0000c000 08:12 2375875    /usr/lib/liblber-2.4.so.2.4.1
aed5d000-aed8d000 r-xp 00000000 08:12 2377155    /usr/lib/libidn.so.11.5.39
aed8d000-aed8e000 ---p 00030000 08:12 2377155    /usr/lib/libidn.so.11.5.39
aed8e000-aed8f000 r--p 00030000 08:12 2377155    /usr/lib/libidn.so.11.5.39
aed8f000-aed90000 rw-p 00031000 08:12 2377155    /usr/lib/libidn.so.11.5.39
aed90000-aedcc000 r-xp 00000000 08:12 2377538    /usr/lib/libcurl.so.4.1.0
aedcc000-aedcd000 r--p 0003c000 08:12 2377538    /usr/lib/libcurl.so.4.1.0
aedcd000-aedce000 rw-p 0003d000 08:12 2377538    /usr/lib/libcurl.so.4.1.0
aede9000-aedea000 ---p aede9000 00:00 0 
aedea000-af5ea000 rwxp aedea000 00:00 0 
af622000-af668000 r-xp 00000000 08:12 2416709    /usr/lib/mozilla/plugins/mplayerplug-in.so
af668000-af669000 r--p 00046000 08:12 2416709    /usr/lib/mozilla/plugins/mplayerplug-in.so
af669000-af66a000 rw-p 00047000 08:12 2416709    /usr/lib/mozilla/plugins/mplayerplug-in.so
af66a000-af6b0000 r-xp 00000000 08:12 2416791    /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af6b0000-af6b1000 r--p 00045000 08:12 2416791    /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af6b1000-af6b2000 rw-p 00046000 08:12 2416791    /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af6b2000-af6f8000 r-xp 00000000 08:12 2416954    /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af6f8000-af6f9000 r--p 00045000 08:12 2416954    /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af6f9000-af6fa000 rw-p 00046000 08:12 2416954    /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af6fa000-af740000 r-xp 00000000 08:12 2416929    /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af740000-af741000 r--p 00045000 08:12 2416929    /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af741000-af742000 rw-p 00046000 08:12 2416929    /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af742000-af788000 r-xp 00000000 08:12 2416962    /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af788000-af789000 r--p 00045000 08:12 2416962    /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af789000-af78a000 rw-p 00046000 08:12 2416962    /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af78a000-af7b7000 r-xp 00000000 08:12 3424839    /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/i386/libjavaplugin_nscp.so
af7b7000-af7bd000 rw-p 0002d000 08:12 3424839    /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/i386/libjavaplugin_nscp.so
af7bd000-af7d3000 r-xp 00000000 08:12 3425027    /usr/lib/jvm/java-6-sun-1.6.0.16/jre/plugin/i386/ns7/libjavaplugin_oji.so
af7d3000-af7d7000 rw-p 00015000 08:12 3425027    /usr/lib/jvm/java-6-sun-1.6.0.16/jre/plugin/i386/ns7/libjavaplugin_oji.so
af7d7000-af9de000 rw-p af7d7000 00:00 0 
af9de000-afa0f000 ---p af9de000 00:00 0 
afa0f000-afa76000 rw-p afa0f000 00:00 0 
afa76000-afb87000 ---p afa76000 00:00 0 
afb87000-aff32000 rw-p afb87000 00:00 0 
aff32000-b0468000 ---p affTerminated

```

Any help will be greatly appreciated. 

Firefox either just shuts down and closes itself, or the whole window greys out (hangs) and I have to use alt+F2 and xkill to close it.

---

### Post by arnab_das on 2009-09-22
maybe updating to the latest version will help. there are various ways of doing it, synaptic is the easiest one. u could also try ubuntuzilla.

---

### Post by mahasmb on 2009-10-03
So I unknowingly updated to a probably unstable version (3.5.4pre) which thankfully has been working very well. 

Thank you for the suggestion. It didn't even cross my mind.

---

