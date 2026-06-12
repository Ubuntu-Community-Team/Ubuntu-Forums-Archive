---
title: "firefox 3.5 problem"
date: 2009-07-14
forum: General Help
---

### Post by jimmyboy09 on 2009-07-14
I recently upgraded to FF 3.5, and mostly everything seems to work okay.  But I noticed that whenever I maximize flash videos (ie. hulu videos), firefox crashes immediately and I have to force quit.

Anyone know how to fix the problem?

Thanks.

---

### Post by peakshysteria on 2009-07-14
How did you upgrade? What system are you running? The more you could tell us the faster we can help you.

---

### Post by y-lee on 2009-07-14
> **peakshysteria said:**
> How did you upgrade? What system are you running? The more you could tell us the faster we can help you.

agreed. Also try starting firefox in a terminal

```
firefox

```
and then maximize a flash video and when firefox crashes it should report some errors in the terminal. Post the error messages here.

---

### Post by jimmyboy09 on 2009-07-14
I upgraded using ubuntuzilla, and I'm running jaunty.

Here's what I got after starting firefox from terminal, and trying to maximize a video on youtube (flash player 10).

> desktop:~$ firefox
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
!!! [Hook] hook(): title not found
*** glibc detected *** /opt/firefox/firefox-bin: free(): invalid pointer: 0xad5a2100 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6725604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb67275b6]
/usr/lib/libGL.so.1[0xaafa5355]
======= Memory map: ========
08048000-08056000 r-xp 00000000 08:03 268302     /opt/firefox/firefox-bin
08056000-08057000 rw-p 0000d000 08:03 268302     /opt/firefox/firefox-bin
08057000-08058000 rw-p 08057000 00:00 0 
a0de8000-a1b02000 r-xp 00000000 08:03 717039     /usr/lib/libGLcore.so.180.44
a1b02000-a1cf4000 rwxp 00d19000 08:03 717039     /usr/lib/libGLcore.so.180.44
a1cf4000-a1d00000 rwxp a1cf4000 00:00 0 
a1d00000-a2e00000 rw-p a1d00000 00:00 0 
a2efb000-a2efc000 ---p a2efb000 00:00 0 
a2efc000-a36fc000 rwxp a2efc000 00:00 0 
a36fc000-a36fd000 ---p a36fc000 00:00 0 
a36fd000-a3efd000 rwxp a36fd000 00:00 0 
a3efd000-a3efe000 ---p a3efd000 00:00 0 
a3efe000-a46fe000 rwxp a3efe000 00:00 0 
a46fe000-a46ff000 ---p a46fe000 00:00 0 
a46ff000-a4eff000 rwxp a46ff000 00:00 0 
a4eff000-a8f00000 rw-s 00000000 00:15 12285      /dev/shm/pulse-shm-2231708859
a8f00000-a9000000 rw-p a8f00000 00:00 0 
a90db000-a9173000 r--p 00000000 08:03 40792      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a9173000-a91ff000 r--p 00000000 08:03 40791      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
a91ff000-a9200000 ---p a91ff000 00:00 0 
a9200000-a9a00000 rwxp a9200000 00:00 0 
a9a00000-a9d00000 rw-p a9a00000 00:00 0 
a9d08000-a9d65000 r-xp 00000000 08:03 717637     /usr/lib/libpulse.so.0.7.1
a9d65000-a9d66000 r--p 0005c000 08:03 717637     /usr/lib/libpulse.so.0.7.1
a9d66000-a9d67000 rw-p 0005d000 08:03 717637     /usr/lib/libpulse.so.0.7.1
a9d67000-a9dff000 r--p 00000000 08:03 40792      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a9dff000-a9e00000 ---p a9dff000 00:00 0 
a9e00000-aa600000 rwxp a9e00000 00:00 0 
aa600000-aaf00000 rw-p aa600000 00:00 0 
aaf44000-aafd1000 r-xp 00000000 08:03 717038     /usr/lib/libGL.so.180.44
aafd1000-aafef000 rwxp 0008d000 08:03 717038     /usr/lib/libGL.so.180.44
aafef000-aaffe000 rwxp aafef000 00:00 0 
aaffe000-aafff000 ---p aaffe000 00:00 0 
aafff000-ab7ff000 rwxp aafff000 00:00 0 
ab7ff000-ab800000 ---p ab7ff000 00:00 0 
ab800000-ac000000 rwxp ab800000 00:00 0 
ac000000-ac100000 rw-p ac000000 00:00 0 
ac132000-ac136000 r-xp 00000000 08:03 16291      /lib/libattr.so.1.1.0
ac136000-ac137000 r--p 00003000 08:03 16291      /lib/libattr.so.1.1.0
ac137000-ac138000 rw-p 00004000 08:03 16291      /lib/libattr.so.1.1.0
ac138000-ac13d000 r-xp 00000000 08:03 717150     /usr/lib/libgdbm.so.3.0.0
ac13d000-ac13e000 r--p 00004000 08:03 717150     /usr/lib/libgdbm.so.3.0.0
ac13e000-ac13f000 rw-p 00005000 08:03 717150     /usr/lib/libgdbm.so.3.0.0
ac13f000-ac17f000 rwxp ac13f000 00:00 0 
ac17f000-ac1ff000 r--p 00000000 08:03 40822      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
ac1ff000-ac200000 ---p ac1ff000 00:00 0 
ac200000-aca00000 rwxp ac200000 00:00 0 
aca00000-acc00000 rw-p aca00000 00:00 0 
acc00000-acc19000 r--p 00000000 08:03 48838      /usr/share/fonts/type1/gsfonts/n021003l.pfb
acc19000-acc49000 rwxp acc19000 00:00 0 
acc49000-acc6b000 r-xp 00000000 08:03 717441     /usr/lib/libk5crypto.so.3.1
acc6b000-acc6c000 r--p 00022000 08:03 717441     /usr/lib/libk5crypto.so.3.1
acc6c000-acc6d000 rw-p 00023000 08:03 717441     /usr/lib/libk5crypto.so.3.1
acc6d000-accfc000 r-xp 00000000 08:03 717447     /usr/lib/libkrb5.so.3.3
accfc000-accfe000 r--p 0008e000 08:03 717447     /usr/lib/libkrb5.so.3.3
accfe000-accff000 rw-p 00090000 08:03 717447     /usr/lib/libkrb5.so.3.3
accff000-acd00000 ---p accff000 00:00 0 
acd00000-ad500000 rwxp acd00000 00:00 0 
ad500000-ad600000 rw-p ad500000 00:00 0 
ad600000-ad603000 r-xp 00000000 08:03 16302      /lib/libcap.so.2.11
ad603000-ad604000 r--p 00002000 08:03 16302      /lib/libcap.so.2.11
ad604000-ad605000 rw-p 00003000 08:03 16302      /lib/libcap.so.2.11
ad605000-ad61b000 r-xp 00000000 08:03 715421     /usr/lib/libsasl2.so.2.0.22
ad61b000-ad61c000 r--p 00015000 08:03 715421     /usr/lib/libsasl2.so.2.0.22
ad61c000-ad61d000 rw-p 00016000 08:03 715421     /usr/lib/libsasl2.so.2.0.22
ad61d000-ad65d000 r-xp 00000000 08:03 717458     /usr/lib/libldap_r-2.4.so.2.4.1
ad65d000-ad65e000 ---p 00040000 08:03 717458     /usr/lib/libldap_r-2.4.so.2.4.1
ad65e000-ad65f000 r--p 00040000 08:03 717458     /usr/lib/libldap_r-2.4.so.2.4.1
ad65f000-ad660000 rw-p 00041000 08:03 717458     /usr/lib/libldap_r-2.4.so.2.4.1
ad660000-ad661000 rw-p ad660000 00:00 0 
ad661000-ad673000 r-xp 00000000 08:03 782386     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad673000-ad674000 r--p 00011000 08:03 782386     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad674000-ad675000 rw-p 00012000 08:03 782386     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
ad675000-ae675000 rw-p ad675000 00:00 0 
ae675000-aefe2000 r-xp 00000000 08:03 155052     /usr/lib/flashplugin-installer/libflashplayer.so
aefe2000-af015000 rw-p 0096c000 08:03 155052     /usr/lib/flashplugin-installer/libflashplayer.so
af015000-af300000 rw-p af015000 00:00 0 
af314000-af33d000 r-xp 00000000 08:03 717296     /usr/lib/libgssapi_krb5.so.2.2
af33d000-af33e000 r--p 00028000 08:03 717296     /usr/lib/libgssapi_krb5.so.2.2
af33e000-af33f000 rw-p 00029000 08:03 717296     /usr/lib/libgssapi_krb5.so.2.2
af33f000-af36f000 r-xp 00000000 08:03 717421     /usr/lib/libidn.so.11.5.39
af36f000-af370000 ---p 00030000 08:03 717421     /usr/lib/libidn.so.11.5.39
af370000-af371000 r--p 00030000 08:03 717421     /usr/lib/libidn.so.11.5.39
af371000-af372000 rw-p 00031000 08:03 717421     /usr/lib/libidn.so.11.5.39
af372000-af3fe000 r--p 00000000 08:03 40791      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
af3fe000-af3ff000 ---p af3fe000 00:00 0 
af3ff000-afbff000 rwxp af3ff000 00:00 0 
afbff000-afc00000 ---p afbff000 00:00 0 
afc00000-b0400000 rwxp afc00000 00:00 0 
b0400000-b0900000 rw-p b0400000 00:00 0 
b0904000-b090b000 r-xp 00000000 08:03 717449     /usr/lib/libkrb5support.so.0.1
b090b000-b090c000 r--p 00006000 08:03 717449     /usr/lib/libkrb5support.so.0.1
b090c000-b090d000 rw-p 00007000 08:03 717449     /usr/lib/libkrb5support.so.0.1
b090d000-b0919000 r-xp 00000000 08:03 717453     /usr/lib/liblber-2.4.so.2.4.1
b0919000-b091a000 r--p 0000b000 08:03 717453     /usr/lib/liblber-2.4.so.2.4.1
b091a000-b091b000 rw-p 0000c000 08:03 717453     /usr/lib/liblber-2.4.so.2.4.1
b091b000-b0954000 r-xp 00000000 08:03 717027     /usr/lib/libcurl-gnutls.so.4.1.0
b0954000-b0955000 r--p 00038000 08:03 717027     /usr/lib/libcurl-gnutls.so.4.1.0
b0955000-b0956000 rw-p 00039000 08:03 717027     /usr/lib/libcurl-gnutls.so.4.1.0
b0957000-b095c000 r-xp 00000000 08:03 422673     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b095c000-b095d000 r--p 00004000 08:03 422673     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b095d000-b095e000 rw-p 00005000 08:03 422673     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b095e000-b0966000 rwxp b095e000 00:00 0 
b0966000-b0978000 r--p 00000000 08:03 48817      /usr/share/fonts/type1/gsfonts/n019004l.pfb
b0978000-b098c000 r--p 00000000 08:03 48814      /usr/share/fonts/type1/gsfonts/n019003l.pfb
b098c000-b09a4000 r-xp 00000000 08:03 782384     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b09a4000-b09a5000 r--p 00018000 08:03 782384     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b09a5000-b09a6000 rw-p 00019000 08:03 782384     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b09a6000-b09bd000 r-xp 00000000 08:03 782383     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
b09bd000-b09be000 r--p 00016000 08:03 782383     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
b09be000-b09bf000 rw-p 00017000 08:03 782383     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
b09bf000-b09cf000 r-xp 00000000 08:03 782385     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b09cf000-b09d0000 ---p 00010000 08:03 782385     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b09d0000-b09d1000 r--p 00010000 08:03 782385     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b09d1000-b09d2000 rw-p 00011000 08:03 782385     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b09d2000-b09ea000 r--s 00000000 08:03 788736     /usr/share/mime/mime.cache
b09ea000-b09fc000 r-xp 00000000 08:03 716026     /usr/lib/libgvfscommon.so.0.0.0
b09fc000-b09fd000 r--p 00012000 08:03 7160Segmentation fault
desktop:~$ Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed


---

### Post by y-lee on 2009-07-14
Hmm, Try the advice found in the thread : [Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed]("http://ubuntuforums.org/showthread.php?t=849155"). Then restart firefox and test it. If it still seg  faults, start it in a terminal and paste the error message here. And by the way [use the code tag]("http://ubuntuforums.org/showthread.php?t=1163202") around long error reports.

---

### Post by lovinglinux on 2009-07-14
The solution to your problem is the **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

---

### Post by jimmyboy09 on 2009-07-14
uhhhh sorry.  I'm such a forum noob.  Too lazy to search for myself.  

Won't happen again.  

Thanks.

---

### Post by jimmyboy09 on 2009-07-14
Hold up...

So I tried fixing my .fonts.conf file with the advice in the thread referred to above...but I still get the line:

```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed 
```

I just straight copied/pasted the top line from the code given there but I still get the error.

Help?

---

### Post by lovinglinux on 2009-07-15
As I mentioned in post number 6, the solution to your problem is the **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

It's a known bug. Just follow the instructions there and you will be fine.

---

### Post by jimmyboy09 on 2009-07-15
sorry sorry miscommunication on my part.

thanks lovinglinux.  I followed those instructions and the fullscreen vid issue has been fixed.

But when I was troubleshooting earlier I got the XML declaration error shown in my previous posts.  That issue hasn't been fixed.  It's not affecting my pc's performance at all, but I thought I'd tie up some loose ends while I'm fixing things.

I followed the instructions in the other thread, even copied lines, but nothing has worked so far.

any ideas?

thanks.

---

