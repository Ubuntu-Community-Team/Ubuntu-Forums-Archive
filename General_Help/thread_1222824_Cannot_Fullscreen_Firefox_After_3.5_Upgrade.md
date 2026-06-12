---
title: "Cannot Fullscreen Firefox After 3.5 Upgrade"
date: 2009-07-25
forum: General Help
---

### Post by Chuchaqui on 2009-07-25
Hello,

I upgraded Firefox to 3.5 the other day and today I can't seem to fullscreen online videos (at least from youtube and hulu). This is the error message I get when I run Firefox in terminal.

```

rob@rick-desktop:~$ firefox-3.5
*** glibc detected *** /usr/lib/firefox-3.5.1/firefox-3.5: free(): invalid pointer: 0xaa3492c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c4e604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7c505b6]
/usr/lib/libGL.so.1[0xaa8e8075]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:01 313190     /usr/lib/firefox-3.5.1/firefox-3.5
0805b000-0805c000 r--p 00012000 08:01 313190     /usr/lib/firefox-3.5.1/firefox-3.5
0805c000-0805d000 rw-p 00013000 08:01 313190     /usr/lib/firefox-3.5.1/firefox-3.5
0805d000-0805e000 rw-p 0805d000 00:00 0 
a0cc0000-a186e000 r-xp 00000000 08:01 134313     /usr/lib/libGLcore.so.173.14.16
a186e000-a19fb000 rwxp 00bae000 08:01 134313     /usr/lib/libGLcore.so.173.14.16
a19fb000-a1a00000 rwxp a19fb000 00:00 0 
a1a00000-a1f00000 rw-p a1a00000 00:00 0 
a1fe9000-a1ffb000 rw-s 00000000 00:09 4161588    /SYSV00000000 (deleted)
a1ffb000-a1ffc000 ---p a1ffb000 00:00 0 
a1ffc000-a27fc000 rwxp a1ffc000 00:00 0 
a27fc000-a27fd000 ---p a27fc000 00:00 0 
a27fd000-a2ffd000 rwxp a27fd000 00:00 0 
a2ffd000-a2ffe000 ---p a2ffd000 00:00 0 
a2ffe000-a37fe000 rwxp a2ffe000 00:00 0 
a37fe000-a37ff000 ---p a37fe000 00:00 0 
a37ff000-a3fff000 rwxp a37ff000 00:00 0 
a3fff000-a8000000 rw-s 00000000 00:15 32483      /dev/shm/pulse-shm-1561794484
a8000000-a8100000 rw-p a8000000 00:00 0 
a8183000-a81e0000 r-xp 00000000 08:01 130999     /usr/lib/libpulse.so.0.7.1
a81e0000-a81e1000 r--p 0005c000 08:01 130999     /usr/lib/libpulse.so.0.7.1
a81e1000-a81e2000 rw-p 0005d000 08:01 130999     /usr/lib/libpulse.so.0.7.1
a81e2000-a81e3000 ---p a81e2000 00:00 0 
a81e3000-a89e3000 rwxp a81e3000 00:00 0 
a89e3000-a89e4000 ---p a89e3000 00:00 0 
a89e4000-a91e4000 rwxp a89e4000 00:00 0 
a91e4000-a9481000 rw-p a91e4000 00:00 0 
a9481000-a94ec000 ---p a9481000 00:00 0 
a94ec000-aa1e4000 rw-p a94ec000 00:00 0 
aa1e4000-aa300000 rw-s 00000000 00:09 4128811    /SYSV00000000 (deleted)
aa300000-aa800000 rw-p aa300000 00:00 0 
aa81e000-aa822000 r-xp 00000000 08:01 539651     /lib/libattr.so.1.1.0
aa822000-aa823000 r--p 00003000 08:01 539651     /lib/libattr.so.1.1.0
aa823000-aa824000 rw-p 00004000 08:01 539651     /lib/libattr.so.1.1.0
aa824000-aa829000 r-xp 00000000 08:01 132702     /usr/lib/libgdbm.so.3.0.0
aa829000-aa82a000 r--p 00004000 08:01 132702     /usr/lib/libgdbm.so.3.0.0
aa82a000-aa82b000 rw-p 00005000 08:01 132702     /usr/lib/libgdbm.so.3.0.0
aa82b000-aa82e000 r-xp 00000000 08:01 539662     /lib/libcap.so.2.11
aa82e000-aa82f000 r--p 00002000 08:01 539662     /lib/libcap.so.2.11
aa82f000-aa830000 rw-p 00003000 08:01 539662     /lib/libcap.so.2.11
aa8a8000-aa930000 r-xp 00000000 08:01 134312     /usr/lib/libGL.so.173.14.16
aa930000-aa94b000 rwxp 00088000 08:01 134312     /usr/lib/libGL.so.173.14.16
aa94b000-aa94c000 rwxp aa94b000 00:00 0 
aa95e000-aa99e000 rwxp aa95e000 00:00 0 
aa99e000-aaa2a000 r--p 00000000 08:01 271353     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
aaa2a000-aaa2c000 r-xp 00000000 08:01 539690     /lib/libkeyutils-1.2.so
aaa2c000-aaa2d000 r--p 00001000 08:01 539690     /lib/libkeyutils-1.2.so
aaa2d000-aaa2e000 rw-p 00002000 08:01 539690     /lib/libkeyutils-1.2.so
aaa2e000-aaa50000 r-xp 00000000 08:01 132993     /usr/lib/libk5crypto.so.3.1
aaa50000-aaa51000 r--p 00022000 08:01 132993     /usr/lib/libk5crypto.so.3.1
aaa51000-aaa52000 rw-p 00023000 08:01 132993     /usr/lib/libk5crypto.so.3.1
aaa52000-aaae1000 r-xp 00000000 08:01 132999     /usr/lib/libkrb5.so.3.3
aaae1000-aaae3000 r--p 0008e000 08:01 132999     /usr/lib/libkrb5.so.3.3
aaae3000-aaae4000 rw-p 00090000 08:01 132999     /usr/lib/libkrb5.so.3.3
aaae4000-aaafa000 r-xp 00000000 08:01 130972     /usr/lib/libsasl2.so.2.0.22
aaafa000-aaafb000 r--p 00015000 08:01 130972     /usr/lib/libsasl2.so.2.0.22
aaafb000-aaafc000 rw-p 00016000 08:01 130972     /usr/lib/libsasl2.so.2.0.22
aaafc000-aab25000 r-xp 00000000 08:01 132848     /usr/lib/libgssapi_krb5.so.2.2
aab25000-aab26000 r--p 00028000 08:01 132848     /usr/lib/libgssapi_krb5.so.2.2
aab26000-aab27000 rw-p 00029000 08:01 132848     /usr/lib/libgssapi_krb5.so.2.2
aab27000-aab60000 r-xp 00000000 08:01 132579     /usr/lib/libcurl-gnutls.so.4.1.0
aab60000-aab61000 r--p 00038000 08:01 132579     /usr/lib/libcurl-gnutls.so.4.1.0
aab61000-aab62000 rw-p 00039000 08:01 132579     /usr/lib/libcurl-gnutls.so.4.1.0
aab65000-aab6a000 r-xp 00000000 08:01 148436     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
aab6a000-aab6b000 r--p 00004000 08:01 148436     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
aab6b000-aab6c000 rw-p 00005000 08:01 148436     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
aab6c000-aab74000 rwxp aab6c000 00:00 0 
aab74000-aab75000 ---p aab74000 00:00 0 
aab75000-ab375000 rwxp aab75000 00:00 0 
ab375000-ac375000 rw-p ab375000 00:00 0 
ac375000-acce2000 r-xp 00000000 08:01 163948     /usr/lib/adobe-flashplugin/libflashplayer.so
acce2000-acd15000 rw-p 0096c000 08:01 163948     /usr/lib/adobe-flashplugin/libflashplayer.so
acd15000-ad800000 rw-p acd15000 00:00 0 
ad801000-ad808000 r-xp 00000000 08:01 133001     /usr/lib/libkrb5support.so.0.1
ad808000-ad809000 r--p 00006000 08:01 133001     /usr/lib/libkrb5support.so.0.1
ad809000-ad80a000 rw-p 00007000 08:01 133001     /usr/lib/libkrb5support.so.0.1
ad80a000-ad84a000 r-xp 00000000 08:01 133010     /usr/lib/libldap_r-2.4.so.2.4.1
ad84a000-ad84b000 ---p 00040000 08:01 133010     /usr/lib/libldap_r-2.4.so.2.4.1
ad84b000-ad84c000 r--p 00040000 08:01 133010     /usr/lib/libldap_r-2.4.so.2.4.1
ad84c000-ad84d000 rw-p 00041000 08:01 133010     /usr/lib/libldap_r-2.4.so.2.4.1
ad84d000-ad84e000 rw-p ad84d000 00:00 0 
ad84e000-ad85a000 r-xp 00000000 08:01 133005     /usr/lib/liblber-2.4.so.2.4.1
ad85a000-ad85b000 r--p 0000b000 08:01 133005     /usr/lib/liblber-2.4.so.2.4.1
ad85b000-ad85c000 rw-p 0000c000 08:01 133005     /usr/lib/liblber-2.4.so.2.4.1
ad85c000-ad88c000 r-xp 00000000 08:01 132973     /usr/lib/libidn.so.11.5.39
ad88c000-ad88d000 ---p 00030000 08:01 132973     /usr/lib/libidn.so.11.5.39
ad88d000-ad88e000 r--p 00030000 08:01 132973     /usr/lib/libidn.so.11.5.39
ad88e000-ad88f000 rw-p 00031000 08:01 132973     /usr/lib/libidn.so.11.5.39
ad88f000-ad896000 r-xp 00000000 08:01 183331     /usr/lib/mozilla/plugins/mozplugger.so
ad896000-ad897000 r--p 00006000 08:01 183331     /usr/lib/mozilla/plugins/mozplugger.so
ad897000-ad898000 rw-p 00007000 08:01 183331     /usr/lib/mozilla/plugins/mozplugger.so
ad898000-ad8b8000 rw-p ad898000 00:00 0 
ad8b8000-ad8d0000 r-xp 00000000 08:01 221140     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
ad8d0000-ad8d1000 r--p 00018000 08:01 221140     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
ad8d1000-ad8d2000 rw-p 00019000 08:01 221140     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
ad8d2000-ad8e9000 r-xp 00000000 08:01 221139     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
ad8e9000-ad8ea000 r--p 00016000 08:01 221139     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
ad8ea000-ad8eb000 rw-p 00017000 08:01 221139     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
ad8eb000-ad8fd000 r-xp 00000000 08:01 221142     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad8fd000-ad8fe000 r--p 00011000 08:01 221142     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad8fe000-ad8ff000 rw-p 00012000 08:01 221142     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad8ff000-ad900000 ---p ad8ff000 00:00 0 
ad900000-ae100000 rwxp ad900000 00:00 0 
ae100000-aea00000 rw-p ae100000 00:00 0 
aea00000-aea10000 r-xp 00000000 08:01 221141     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
aea10000-aea11000 ---p 00010000 08:01 221141     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
aea11000-aea12000 r--p 00010000 08:01 221141     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
aea12000-aea13000 rw-p 00011000 08:01 221141     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
aea13000-aea47000 r-xp 00000000 08:01 466702     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
aea47000-aea48000 ---p 00034000 08:01 466702     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
aea48000-aea49000 r--p 00034000 08:01 466702     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
aea49000-aea4a000 rw-p 00035000 08:01 466702     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
aea4a000-aea5c000 r--p 00000000 08:01 278030     /usr/share/fonts/type1/gsfonts/n019004l.pfb
aea5c0Aborted

```

From what little of this I understand it looks like it may not be a problem with Ubuntu and this forum may not be the appropriate location for this message. That being said, if that's the case if someone could tell me a more appropriate place to report this problem.

Cheers

**Editorial**
In case this has anything to do with it:

Firefox Version: 3.5.1
Flash Version: 10.0.22.87
Graphics Card: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by deadspider187 on 2009-07-25
What method did you use to upgrade to Firefox 3.5?  Did you upgrade by adding a repository, try to compile it, or grab a binary?  How did you install Flash?

---

### Post by Chuchaqui on 2009-07-25
I've had flashed installed for I don't know how long no this computer with no previous problems with it. I don't think I had to update it or anything when I switched to Firefox-3.5. I think I originally installed flash with ubuntu-restricted extras or just with Firefox itself, not sure which :s .

I installed Firefox-3.5 with synaptic.

---

### Post by khelben1979 on 2009-07-25
It don't work on my system either. In my case I just grabbed the binary. I'm using YouTube together with flash 10,

With Opera it works, though,

---

### Post by lovinglinux on 2009-07-25
See **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

---

### Post by Chuchaqui on 2009-07-25
That seems to have done it. Thanks a bunch!

---

### Post by lovinglinux on 2009-07-25
> **Chuchaqui said:**
> That seems to have done it. Thanks a bunch!

You are welcome.

---

