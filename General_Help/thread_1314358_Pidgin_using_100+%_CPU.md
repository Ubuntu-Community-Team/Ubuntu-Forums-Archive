---
title: "Pidgin using 100+% CPU"
date: 2009-11-04
forum: General Help
---

### Post by ManiacDan on 2009-11-04
I just upgraded to Ubuntu 9.10 Karmic Koala (full title included here for google purposes), and Pidgin seems to be using an inordinate amount of CPU.

Pidgin version 2.6.2

Contents of my TOP from just before posting:
```
Tasks: 203 total,   4 running, 199 sleeping,   0 stopped,   0 zombie
Cpu(s): 69.3%us, 30.5%sy,  0.2%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2059448k total,  1985888k used,    73560k free,     5528k buffers
Swap:  4192956k total,   229072k used,  3963884k free,   125044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                 
19130 ManiacDan  20   0  314m  44m  22m S   97  2.2   2:20.18 pidgin                                  
31906 ManiacDan  20   0  183m  21m 9640 S   83  1.1  10:11.88 pidgin                                  
 8460 root       20   0  352m 184m  34m S    8  9.2  61:52.44 Xorg                                    
18287 ManiacDan  20   0 42500  18m  14m S    8  0.9   1:53.96 gnome-system-mo                         
32056 ManiacDan  20   0  383m 314m  31m R    1 15.6  11:54.82 VirtualBox                              
 8687 ManiacDan  20   0  823m 318m  21m S    1 15.8  68:01.21 firefox                                 
 1269 boinc      39  19  9572 1724 1020 R    0  0.1   1:23.43 boinc                                   
 9574 root       20   0  154m 1124  596 S    0  0.1   5:20.77 truecrypt                               
14411 ManiacDan  20   0 1230m 406m  12m S    0 20.2  10:02.28 ZendStudio                              
20113 ManiacDan  20   0  2468 1228  884 R    0  0.1   0:00.01 top                                     
21573 ManiacDan  20   0 59268  16m 3872 S    0  0.8   1:20.08 ubuntuone-clien                         
    1 root       20   0  2636  800  536 S    0  0.0   0:02.33 init                                    

```Yes, I'm running two copies of pidgin, one for my office jabber server that logs files locally, and one for my personal IM conversations which logs files to my flash drive.  I've tried running with just one or the other, but haven't had any luck, I included the output when they're both running for shock value, as 180% CPU is a bit much for two instances of an IM program.

Any thoughts?  I may just switch to Empathy.  I'll miss all the pidgin plugins I use, but I'd rather have a functioning computer.

-Dan

P.S. This machine had some major CPU issues related to libnotify a few months ago (on 9.04), I had to install a third party patch that was never merged into the repository.

---

### Post by undecim on 2009-11-04
Can you run pidgin from a terminal and post the output?

---

### Post by ManiacDan on 2009-11-04
Pidgin from the terminal produces no errors or output at all (other than invoking pidgin, of course).  Displaying the buddy list has no unexpected effects, but opening a chat window to someone (anyone, it seems), causes my CPU to go rapidly to 200%.  It's not immediate, it happens over the course of about 5 seconds.

I'll try to systematically disable plugins.  I noticed OTR was no longer supported, and if anything would gobble CPU it's that.  What bothers me is that the CPU load goes up immediately upon invoking a conversation window, regardless of the content or whether or not the target has OTR installed.




If it helps, output of "lsof | grep pidgin"
```
pidgin    23253   ManiacDan  cwd       DIR        8,3      4096  4562946 /home/ManiacDan
pidgin    23253   ManiacDan  rtd       DIR        8,3      4096        2 /
pidgin    23253   ManiacDan  txt       REG        8,3    888120  3416834 /usr/bin/pidgin
pidgin    23253   ManiacDan  mem       REG        8,3      9656  3417694 /usr/lib/libXss.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3   1001700  3417514 /usr/lib/libpurple.so.0.6.2
pidgin    23253   ManiacDan  mem       REG        8,3    227000  5537836 /lib/libdbus-1.so.3.4.0
pidgin    23253   ManiacDan  mem       REG        8,3    116920   180250 /lib/tls/i686/cmov/libpthread-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     17940  3417858 /usr/lib/libgthread-2.0.so.0.2200.2
pidgin    23253   ManiacDan  mem       REG        8,3    120380  1327188 /usr/lib/libxcb.so.1.1.0
pidgin    23253   ManiacDan  mem       REG        8,3     60024  3416066 /usr/lib/libXext.so.6.4.0
pidgin    23253   ManiacDan  mem       REG        8,3     13988  5537922 /lib/libuuid.so.1.3.0
pidgin    23253   ManiacDan  mem       REG        8,3    166292  3416551 /usr/lib/libpangoft2-1.0.so.0.2600.0
pidgin    23253   ManiacDan  mem       REG        8,3    179024  3416566 /usr/lib/libfontconfig.so.1.3.0
pidgin    23253   ManiacDan  mem       REG        8,3     13704  3417849 /usr/lib/libgmodule-2.0.so.0.2200.2
pidgin    23253   ManiacDan  mem       REG        8,3     38444  3417495 /usr/lib/libenchant.so.1.5.0
pidgin    23253   ManiacDan  mem       REG        8,3     13672  3419562 /usr/lib/libxcb-aux.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      9564  3416104 /usr/lib/libXcomposite.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      6260  3417664 /usr/lib/libXdamage.so.1.1.0
pidgin    23253   ManiacDan  mem       REG        8,3     17696  3417894 /usr/lib/libXfixes.so.3.1.0
pidgin    23253   ManiacDan  mem       REG        8,3      6528  3417680 /usr/lib/libXinerama.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      5560  3424897 /usr/lib/pidgin/iconaway.so
pidgin    23253   ManiacDan  mem       REG        8,3     22116  3418227 /usr/lib/libgtkspell.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3   3924540  3417963 /usr/lib/libgtk-x11-2.0.so.0.1800.3
pidgin    23253   ManiacDan  mem       REG        8,3    547284  1327198 /usr/lib/libcairo.so.2.10800.8
pidgin    23253   ManiacDan  mem       REG        8,3      9564  1327186 /usr/lib/libXau.so.6.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      9752  3424654 /usr/lib/pidgin/extplacement.so
pidgin    23253   ManiacDan  mem       REG        8,3    116448  1327166 /usr/lib/libatk-1.0.so.0.2809.1
pidgin    23253   ManiacDan  mem       REG        8,3    743912  5538137 /lib/libglib-2.0.so.0.2200.2
pidgin    23253   ManiacDan  mem       REG        8,3     16628  3417666 /usr/lib/libXdmcp.so.6.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     38372  3419566 /usr/lib/libstartup-notification-1.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    774828  3418463 /usr/lib/libgstreamer-0.10.so.0.22.0
pidgin    23253   ManiacDan  mem       REG        8,3     34412  1327196 /usr/lib/libXrender.so.1.3.0
pidgin    23253   ManiacDan  mem       REG        8,3     30684   180252 /lib/tls/i686/cmov/librt-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3    288832  3416301 /usr/lib/libpango-1.0.so.0.2600.0
pidgin    23253   ManiacDan  mem       REG        8,3     83608  5538126 /lib/libz.so.1.2.3.3
pidgin    23253   ManiacDan  mem       REG        8,3     38384  5308450 /usr/lib/libXi.so.6.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     38332  3416468 /usr/lib/libXcursor.so.1.0.2
pidgin    23253   ManiacDan  mem       REG        8,3      5596  3424719 /usr/lib/pidgin/gtkbuddynote.so
pidgin    23253   ManiacDan  mem       REG        8,3     13700  3419564 /usr/lib/libxcb-event.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      9756  3424905 /usr/lib/pidgin/timestamp_format.so
pidgin    23253   ManiacDan  mem       REG        8,3    100132  3418420 /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
pidgin    23253   ManiacDan  mem       REG        8,3     13760  1327194 /usr/lib/libxcb-render-util.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     47020  3416348 /usr/lib/libpangocairo-1.0.so.0.2600.0
pidgin    23253   ManiacDan  mem       REG        8,3    605480  3417925 /usr/lib/libgio-2.0.so.0.2200.2
pidgin    23253   ManiacDan  mem       REG        8,3     34292  1327174 /usr/lib/libfusion-1.2.so.0.7.0
pidgin    23253   ManiacDan  mem       REG        8,3      5564  3407882 /usr/lib/purple-2/buddynote.so
pidgin    23253   ManiacDan  mem       REG        8,3   1233824  1327190 /usr/lib/libX11.so.6.2.0
pidgin    23253   ManiacDan  mem       REG        8,3    117152  5554553 /usr/lib/libdbus-glib-1.so.2.1.0
pidgin    23253   ManiacDan  mem       REG        8,3     59292  3418518 /usr/lib/libgstfarsight-0.10.so.0.3.1
pidgin    23253   ManiacDan  mem       REG        8,3     34184  1327192 /usr/lib/libxcb-render.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    610180  3418411 /usr/lib/libgdk-x11-2.0.so.0.1800.3
pidgin    23253   ManiacDan  mem       REG        8,3     59028  3419070 /usr/lib/libgstinterfaces-0.10.so.0.18.0
pidgin    23253   ManiacDan  mem       REG        8,3      5588  3407886 /usr/lib/purple-2/newline.so
pidgin    23253   ManiacDan  mem       REG        8,3     13672  3419542 /usr/lib/libxcb-atom.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     26400   180243 /lib/tls/i686/cmov/libnss_compat-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     13772  3417595 /usr/lib/libcanberra-gtk.so.0.1.1
pidgin    23253   ManiacDan  mem       REG        8,3     13956  3416339 /usr/lib/liblaunchpad-integration.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     79676   180242 /lib/tls/i686/cmov/libnsl-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     71432   180251 /lib/tls/i686/cmov/libresolv-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     17988  4104279 /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
pidgin    23253   ManiacDan  mem       REG        8,3     96440  3418327 /usr/lib/libICE.so.6.3.0
pidgin    23253   ManiacDan  mem       REG        8,3     13600  5537913 /lib/libgpg-error.so.0.4.0
pidgin    23253   ManiacDan  mem       REG        8,3    113320  5537840 /lib/ld-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3    104148  5537827 /lib/libselinux.so.1
pidgin    23253   ManiacDan  mem       REG        8,3      9844  3424904 /usr/lib/pidgin/timestamp.so
pidgin    23253   ManiacDan  mem       REG        8,3    247788  3417283 /usr/lib/libgobject-2.0.so.0.2200.2
pidgin    23253   ManiacDan  mem       REG        8,3     38504   180247 /lib/tls/i686/cmov/libnss_nis-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     34316  3416429 /usr/lib/libvorbisfile.so.3.2.0
pidgin    23253   ManiacDan  mem       REG        8,3     30080  3417613 /usr/lib/libSM.so.6.0.0
pidgin    23253   ManiacDan  mem       REG        8,3   1319364   180236 /lib/tls/i686/cmov/libc-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     92300  3416904 /usr/lib/libdirect-1.2.so.0.7.0
pidgin    23253   ManiacDan  mem       REG        8,3     21836  3417576 /usr/lib/libogg.so.0.6.0
pidgin    23253   ManiacDan  mem       REG        8,3      5556  3407878 /usr/lib/purple-2/ssl.so
pidgin    23253   ManiacDan  mem       REG        8,3      9736   180239 /lib/tls/i686/cmov/libdl-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     42572   180245 /lib/tls/i686/cmov/libnss_files-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     34260  3417905 /usr/lib/libltdl.so.7.2.0
pidgin    23253   ManiacDan  mem       REG        8,3    149392   180240 /lib/tls/i686/cmov/libm-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     59036  3418561 /usr/lib/libcanberra.so.0.1.7
pidgin    23253   ManiacDan  mem       REG        8,3     18220  3424635 /usr/lib/pidgin/musicmessaging.so
pidgin    23253   ManiacDan  mem       REG        8,3      9632  5538131 /lib/libcom_err.so.2.1
pidgin    23253   ManiacDan  mem       REG        8,3    513472  1327180 /usr/lib/libfreetype.so.6.3.20
pidgin    23253   ManiacDan  mem       REG        8,3    157536  1327184 /usr/lib/libpng12.so.0.37.0
pidgin    23253   ManiacDan  mem       REG        8,3     30064  3418514 /usr/lib/libXrandr.so.2.2.0
pidgin    23253   ManiacDan  mem       REG        8,3    244056  3418413 /usr/lib/libgstbase-0.10.so.0.22.0
pidgin    23253   ManiacDan  mem       REG        8,3    199220  3419534 /usr/lib/libebook-1.2.so.9.3.1
pidgin    23253   ManiacDan  mem       REG        8,3     91484  1327208 /usr/lib/libbonobo-activation.so.4.0.0
pidgin    23253   ManiacDan  mem       REG        8,3   1214216  3419001 /usr/lib/libnss3.so
pidgin    23253   ManiacDan  mem       REG        8,3    728616  1327149 /usr/lib/libkrb5.so.3.3
pidgin    23253   ManiacDan  mem       REG        8,3   1468536  3416937 /usr/lib/libdb-4.7.so
pidgin    23253   ManiacDan  mem       REG        8,3     34832  3424637 /usr/lib/pidgin/xmppdisco.so
pidgin    23253   ManiacDan  mem       REG        8,3    106432  3407898 /usr/lib/purple-2/libnovell.so
pidgin    23253   ManiacDan  mem       REG        8,3    278844  3407896 /usr/lib/purple-2/libmsn.so
pidgin    23253   ManiacDan  mem       REG        8,3     18332  3407895 /usr/lib/purple-2/libxmpp.so
pidgin    23253   ManiacDan  mem       REG        8,3     21788  3475799 /usr/lib/sasl2/libsasldb.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3      9784  3407887 /usr/lib/purple-2/offlinemsg.so
pidgin    23253   ManiacDan  mem       REG        8,3     18280  3407879 /usr/lib/purple-2/ssl-nss.so
pidgin    23253   ManiacDan  mem       REG        8,3     22080  3449044 /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
pidgin    23253   ManiacDan  mem       REG        8,3    162784  3418709 /usr/lib/libsmime3.so
pidgin    23253   ManiacDan  mem       REG        8,3    800304  3417061 /usr/lib/libtcl8.4.so.0
pidgin    23253   ManiacDan  mem       REG        8,3    198288  3416557 /usr/lib/libmeanwhile.so.1.0.2
pidgin    23253   ManiacDan  mem       REG        8,3     38680  3407885 /usr/lib/purple-2/log_reader.so
pidgin    23253   ManiacDan  mem       REG        8,3    248340  3252228 /usr/lib/nss/libsoftokn3.so
pidgin    23253   ManiacDan  mem       REG        8,3    150280  3449245 /usr/lib/gio/modules/libgvfsdbus.so
pidgin    23253   ManiacDan  mem       REG        8,3     22164  2342953 /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
pidgin    23253   ManiacDan  mem       REG        8,3      9616  3419361 /usr/lib/libindicate-gtk.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    974180  3417063 /usr/lib/libtk8.4.so.0
pidgin    23253   ManiacDan  mem       REG        8,3    281232  3416115 /usr/lib/libhunspell-1.2.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     39852  2539522 /usr/lib/enchant/libenchant_hspell.so
pidgin    23253   ManiacDan  mem       REG        8,3    140900  3418600 /usr/lib/libjpeg.so.62.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    204036  2900072 /usr/lib/gstreamer-0.10/libgstplaybin.so
pidgin    23253   ManiacDan  mem       REG        8,3     43020  2900065 /usr/lib/gstreamer-0.10/libgstdecodebin.so
pidgin    23253   ManiacDan  mem       REG        8,3    141328  3417386 /usr/lib/libgstaudio-0.10.so.0.18.0
pidgin    23253   ManiacDan  mem       REG        8,3     34540  3416694 /usr/lib/libnotify.so.1.1.3
pidgin    23253   ManiacDan  mem       REG        8,3     22320  3424903 /usr/lib/pidgin/themeedit.so
pidgin    23253   ManiacDan  mem       REG        8,3    490380  3417322 /usr/lib/liboil-0.3.so.0.3.0
pidgin    23253   ManiacDan  mem       REG        8,3     38360   180238 /lib/tls/i686/cmov/libcrypt-2.10.1.so
pidgin    23253   ManiacDan  mem       REG        8,3     92648  3424297 /usr/lib/gstreamer-0.10/libgstalsa.so
pidgin    23253   ManiacDan  mem       REG        8,3    257012  3418438 /usr/lib/libpulse.so.0.12.0
pidgin    23253   ManiacDan  mem       REG        8,3     46708  2539523 /usr/lib/enchant/libenchant_ispell.so
pidgin    23253   ManiacDan  mem       REG        8,3     30960  5538098 /lib/libwrap.so.0.7.6
pidgin    23253   ManiacDan  mem       REG        8,3   1432504  3417949 /usr/lib/libperl.so.5.10.0
pidgin    23253   ManiacDan  mem       REG        8,3    962800  1327159 /usr/lib/libstdc++.so.6.0.13
pidgin    23253   ManiacDan  mem       REG        8,3     22220  3424629 /usr/lib/pidgin/cap.so
pidgin    23253   ManiacDan  mem       REG        8,3    420372  3417598 /usr/lib/libsndfile.so.1.0.20
pidgin    23253   ManiacDan  mem       REG        8,3     17812  3424858 /usr/lib/sasl2/libplain.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3    809020  3416172 /usr/lib/libasound.so.2.0.0
pidgin    23253   ManiacDan  mem       REG        8,3   1020524  3417585 /usr/lib/libvorbisenc.so.2.0.3
pidgin    23253   ManiacDan  mem       REG        8,3     22316  3424638 /usr/lib/pidgin/ticker.so
pidgin    23253   ManiacDan  mem       REG        8,3     13880  3407881 /usr/lib/purple-2/autoaccept.so
pidgin    23253   ManiacDan  mem       REG        8,3     17940  3417244 /usr/lib/libplc4.so
pidgin    23253   ManiacDan  mem       REG        8,3     17816  3424377 /usr/lib/sasl2/libanonymous.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3     59376  3424902 /usr/lib/pidgin/spellchk.so
pidgin    23253   ManiacDan  mem       REG        8,3     18404  3424907 /usr/lib/pidgin/vvconfig.so
pidgin    23253   ManiacDan  mem       REG        8,3      9748  3407883 /usr/lib/purple-2/idle.so
pidgin    23253   ManiacDan  mem       REG        8,3    223760  5308427 /usr/lib/librsvg-2.so.2.26.0
pidgin    23253   ManiacDan  mem       REG        8,3     50860  3424487 /usr/lib/sasl2/libdigestmd5.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3     51584  3407923 /usr/lib/purple-2/libzephyr.so
pidgin    23253   ManiacDan  mem       REG        8,3     89552  3407903 /usr/lib/purple-2/libsametime.so
pidgin    23253   ManiacDan  mem       REG        8,3    125912  3417530 /usr/lib/libedata-book-1.2.so.2.4.1
pidgin    23253   ManiacDan  mem       REG        8,3      9692  3424901 /usr/lib/pidgin/sendbutton.so
pidgin    23253   ManiacDan  mem       REG        8,3     50608  3419074 /usr/lib/libgstriff-0.10.so.0.18.0
pidgin    23253   ManiacDan  mem       REG        8,3    340496  3407894 /usr/lib/purple-2/libjabber.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     63540  3419098 /usr/lib/libgsttag-0.10.so.0.18.0
pidgin    23253   ManiacDan  mem       REG        8,3     30252  1327137 /usr/lib/libkrb5support.so.0.1
pidgin    23253   ManiacDan  mem       REG        8,3     59748  3407880 /usr/lib/purple-2/tcl.so
pidgin    23253   ManiacDan  mem       REG        8,3    415836  1327206 /usr/lib/libbonobo-2.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3      9776  3407890 /usr/lib/purple-2/dbus-example.so
pidgin    23253   ManiacDan  mem       REG        8,3    178796  1327153 /usr/lib/libgssapi_krb5.so.2.2
pidgin    23253   ManiacDan  mem       REG        8,3     64552  2900077 /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
pidgin    23253   ManiacDan  mem       REG        8,3    682548  3417193 /usr/lib/libgnutls.so.26.14.10
pidgin    23253   ManiacDan  mem       REG        8,3     71588  3449244 /usr/lib/gio/modules/libgioremote-volume-monitor.so
pidgin    23253   ManiacDan  mem       REG        8,3      9780  3407884 /usr/lib/purple-2/joinpart.so
pidgin    23253   ManiacDan  mem       REG        8,3     18072  2900082 /usr/lib/gstreamer-0.10/libgstvolume.so
pidgin    23253   ManiacDan  mem       REG        8,3    195696  3407906 /usr/lib/purple-2/libymsg.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    150332  3417406 /usr/lib/libedataserver-1.2.so.11.0.1
pidgin    23253   ManiacDan  mem       REG        8,3    193860  5538135 /lib/libpcre.so.3.12.1
pidgin    23253   ManiacDan  mem       REG        8,3     42548  3416982 /usr/lib/libavahi-common.so.3.5.1
pidgin    23253   ManiacDan  mem       REG        8,3    116256  3418361 /usr/lib/libgadu.so.3.9.0
pidgin    23253   ManiacDan  mem       REG        8,3    228780  3416515 /usr/lib/libnspr4.so
pidgin    23253   ManiacDan  mem       REG        8,3      9748  3407888 /usr/lib/purple-2/psychic.so
pidgin    23253   ManiacDan  mem       REG        8,3     42240  5537950 /lib/libudev.so.0.5.0
pidgin    23253   ManiacDan  mem       REG        8,3     68468  3407891 /usr/lib/purple-2/libbonjour.so
pidgin    23253   ManiacDan  mem       REG        8,3    244896  3417785 /usr/lib/libgsf-1.so.114.0.15
pidgin    23253   ManiacDan  mem       REG        8,3    208212  3417815 /usr/lib/libcroco-0.6.so.3.0.1
pidgin    23253   ManiacDan  mem       REG        8,3     92808  3424721 /usr/lib/pidgin/pidgin-otr.so
pidgin    23253   ManiacDan  mem       REG        8,3    207928  3416370 /usr/lib/libssl3.so
pidgin    23253   ManiacDan  mem       REG        8,3    435340  3419011 /usr/lib/libcamel-1.2.so.14.0.1
pidgin    23253   ManiacDan  mem       REG        8,3     47252  3424633 /usr/lib/pidgin/gevolution.so
pidgin    23253   ManiacDan  mem       REG        8,3     81920  3407893 /usr/lib/purple-2/libirc.so
pidgin    23253   ManiacDan  mem       REG        8,3    154096  3418454 /usr/lib/libgstcontroller-0.10.so.0.22.0
pidgin    23253   ManiacDan  mem       REG        8,3     13912  3424898 /usr/lib/pidgin/markerline.so
pidgin    23253   ManiacDan  mem       REG        8,3     13756  3417246 /usr/lib/libplds4.so
pidgin    23253   ManiacDan  mem       REG        8,3     13964  3424430 /usr/lib/pidgin/nautilus.so
pidgin    23253   ManiacDan  mem       REG        8,3    157064  5537868 /lib/libexpat.so.1.5.2
pidgin    23253   ManiacDan  mem       REG        8,3     22244  3424900 /usr/lib/pidgin/pidginrc.so
pidgin    23253   ManiacDan  mem       REG        8,3     64124  3407892 /usr/lib/purple-2/libgg.so
pidgin    23253   ManiacDan  mem       REG        8,3    137144  3449209 /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
pidgin    23253   ManiacDan  mem       REG        8,3     89024  3407897 /usr/lib/purple-2/libmyspace.so
pidgin    23253   ManiacDan  mem       REG        8,3      9980  3407901 /usr/lib/purple-2/libicq.so
pidgin    23253   ManiacDan  mem       REG        8,3      9596  2539521 /usr/lib/enchant/libenchant_aspell.so
pidgin    23253   ManiacDan  mem       REG        8,3    116272  5537797 /lib/libgcc_s.so.1
pidgin    23253   ManiacDan  mem       REG        8,3      9948  3407900 /usr/lib/purple-2/libaim.so
pidgin    23253   ManiacDan  mem       REG        8,3      9640  3416821 /usr/lib/libavahi-glib.so.1.0.1
pidgin    23253   ManiacDan  mem       REG        8,3     14240  3407907 /usr/lib/purple-2/libyahoo.so
pidgin    23253   ManiacDan  mem       REG        8,3      9532  2678857 /usr/lib/gconv/ISO8859-1.so
pidgin    23253   ManiacDan  mem       REG        8,3     10052  3407910 /usr/lib/purple-2/libyahoojp.so
pidgin    23253   ManiacDan  mem       REG        8,3    169500  1327145 /usr/lib/libk5crypto.so.3.1
pidgin    23253   ManiacDan  mem       REG        8,3    269884  3407899 /usr/lib/purple-2/liboscar.so.0.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     59328  2900060 /usr/lib/gstreamer-0.10/libgstaudioconvert.so
pidgin    23253   ManiacDan  mem       REG        8,3    100160  3419000 /usr/lib/libnssutil3.so
pidgin    23253   ManiacDan  mem       REG        8,3    338056  3417615 /usr/lib/libORBit-2.so.0.1.0
pidgin    23253   ManiacDan  mem       REG        8,3     59144  3416491 /usr/lib/libindicate.so.3.0.2
pidgin    23253   ManiacDan  mem       REG        8,3    312972  3252227 /usr/lib/nss/libfreebl3.so
pidgin    23253   ManiacDan  mem       REG        8,3     34864  3424908 /usr/lib/purple-2/pidgin-libnotify.so
pidgin    23253   ManiacDan  mem       REG        8,3    100136  1327210 /usr/lib/libsasl2.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3    284892  1327182 /usr/lib/libpixman-1.so.0.14.0
pidgin    23253   ManiacDan  mem       REG        8,3     54744  3416591 /usr/lib/libtdb.so.1.1.5
pidgin    23253   ManiacDan  mem       REG        8,3     67028  3417597 /usr/lib/libtasn1.so.3.1.5
pidgin    23253   ManiacDan  mem       REG        8,3    184296  3424396 /usr/lib/gstreamer-0.10/libgstcoreelements.so
pidgin    23253   ManiacDan  mem       REG        8,3      9916  3484066 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
pidgin    23253   ManiacDan  mem       REG        8,3     18088  3424640 /usr/lib/pidgin/convcolors.so
pidgin    23253   ManiacDan  mem       REG        8,3     18164  3424631 /usr/lib/pidgin/gestures.so
pidgin    23253   ManiacDan  mem       REG        8,3     34196  3424855 /usr/lib/sasl2/libntlm.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3     17964  4148012 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
pidgin    23253   ManiacDan  mem       REG        8,3     51116  3407877 /usr/lib/purple-2/perl.so
pidgin    23253   ManiacDan  mem       REG        8,3     70072  5537894 /lib/libbz2.so.1.0.4
pidgin    23253   ManiacDan  mem       REG        8,3   1208796  3418278 /usr/lib/libxml2.so.2.7.5
pidgin    23253   ManiacDan  mem       REG        8,3     50704  3417510 /usr/lib/libzephyr.so.4.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     75324  3418353 /usr/lib/libotr.so.2.2.0
pidgin    23253   ManiacDan  mem       REG        8,3      9652  3449202 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
pidgin    23253   ManiacDan  mem       REG        8,3     30524  3424906 /usr/lib/pidgin/xmppconsole.so
pidgin    23253   ManiacDan  mem       REG        8,3      9492  5538133 /lib/libkeyutils-1.2.so
pidgin    23253   ManiacDan  mem       REG        8,3    202300  3416288 /usr/lib/libidn.so.11.5.44
pidgin    23253   ManiacDan  mem       REG        8,3    379204  3252230 /usr/lib/nss/libnssckbi.so
pidgin    23253   ManiacDan  mem       REG        8,3     51204  2900055 /usr/lib/gstreamer-0.10/libgstwavparse.so
pidgin    23253   ManiacDan  mem       REG        8,3    492192  1327173 /usr/lib/libdirectfb-1.2.so.0.7.0
pidgin    23253   ManiacDan  mem       REG        8,3    198816  3416978 /usr/lib/libgconf-2.so.4.1.5
pidgin    23253   ManiacDan  mem       REG        8,3    297368  3418449 /usr/lib/libpulsecommon-0.9.19.so
pidgin    23253   ManiacDan  mem       REG        8,3    661292  3416127 /usr/lib/libaspell.so.15.1.4
pidgin    23253   ManiacDan  mem       REG        8,3     17816  3424482 /usr/lib/sasl2/libcrammd5.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3     46700  3417414 /usr/lib/libgstpbutils-0.10.so.0.18.0
pidgin    23253   ManiacDan  mem       REG        8,3    503740  5537857 /lib/libgcrypt.so.11.5.2
pidgin    23253   ManiacDan  mem       REG        8,3     43232  3407905 /usr/lib/purple-2/libsimple.so
pidgin    23253   ManiacDan  mem       REG        8,3     22076  3416130 /usr/lib/libXtst.so.6.1.0
pidgin    23253   ManiacDan  mem       REG        8,3    557452  3416256 /usr/lib/libsqlite3.so.0.8.6
pidgin    23253   ManiacDan  mem       REG        8,3     17988  2539524 /usr/lib/enchant/libenchant_myspell.so
pidgin    23253   ManiacDan  mem       REG        8,3     17904  4148010 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
pidgin    23253   ManiacDan  mem       REG        8,3    273544  3417425 /usr/lib/libsoup-2.4.so.1.3.0
pidgin    23253   ManiacDan  mem       REG        8,3      9676  2539525 /usr/lib/enchant/libenchant_zemberek.so
pidgin    23253   ManiacDan  mem       REG        8,3     22044  3416475 /usr/lib/libebackend-1.2.so.0.0.1
pidgin    23253   ManiacDan  mem       REG        8,3    154952  3407904 /usr/lib/purple-2/libsilcpurple.so
pidgin    23253   ManiacDan  mem       REG        8,3   1454876  5538145 /lib/i686/cmov/libcrypto.so.0.9.8
pidgin    23253   ManiacDan  mem       REG        8,3     30608  2900013 /usr/lib/gstreamer-0.10/libgstgconfelements.so
pidgin    23253   ManiacDan  mem       REG        8,3     63244  3417151 /usr/lib/libavahi-client.so.3.2.5
pidgin    23253   ManiacDan  mem       REG        8,3    248192  3417504 /usr/lib/libsilcclient-1.1.so.3.0.0
pidgin    23253   ManiacDan  mem       REG        8,3     63560  2900062 /usr/lib/gstreamer-0.10/libgstaudioresample.so
pidgin    23253   ManiacDan  mem       REG        8,3      9752  3407889 /usr/lib/purple-2/statenotify.so
pidgin    23253   ManiacDan  mem       REG        8,3      9784  3424896 /usr/lib/pidgin/history.so
pidgin    23253   ManiacDan  mem       REG        8,3    228516  3417172 /usr/lib/libibus.so.1.0.0
pidgin    23253   ManiacDan  mem       REG        8,3    171984  3417583 /usr/lib/libvorbis.so.0.4.0
pidgin    23253   ManiacDan  mem       REG        8,3     17812  3424810 /usr/lib/sasl2/liblogin.so.2.0.23
pidgin    23253   ManiacDan  mem       REG        8,3     19504  3418522 /usr/lib/libORBitCosNaming-2.so.0.1.0
pidgin    23253   ManiacDan  mem       REG        8,3    322192  3418379 /usr/lib/libFLAC.so.8.2.0
pidgin    23253   ManiacDan  mem       REG        8,3    231920  3407902 /usr/lib/purple-2/libqq.so
pidgin    23253   ManiacDan  mem       REG        8,3     22160  3424899 /usr/lib/pidgin/notify.so
pidgin    23253   ManiacDan  mem       REG        8,3    867916  3417462 /usr/lib/libsilc-1.1.so.2.1.0
pidgin    23253   ManiacDan  mem       REG        8,3     84460  3419363 /usr/lib/libgvfscommon.so.0.0.0
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1352402 /dev/shm/pulse-shm-2463632129
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1352053 /dev/shm/pulse-shm-1418500817
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1346867 /dev/shm/pulse-shm-2961154363
pidgin    23253   ManiacDan  mem       REG        8,3     79155  3555533 /usr/share/fonts/type1/gsfonts/n019003l.pfb
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1346508 /dev/shm/pulse-shm-4038157181
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1346402 /dev/shm/pulse-shm-2912044860
pidgin    23253   ManiacDan  mem       REG       0,17  67108904  1346241 /dev/shm/pulse-shm-1824866518
pidgin    23253   ManiacDan  DEL       REG        0,9           36143123 /SYSV00000000
pidgin    23253   ManiacDan  DEL       REG        0,9           36110348 /SYSV00000000
pidgin    23253   ManiacDan  mem       REG        8,3    329136  3547252 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
pidgin    23253   ManiacDan  mem       REG        8,3    572908  3547177 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
pidgin    23253   ManiacDan  mem       REG        8,3    622020  3547176 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
pidgin    23253   ManiacDan  mem       REG        8,3      1136  2091083 /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     23800  2091074 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      5280  2089297 /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      7384  2091084 /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      8664  2089567 /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     10992  2091077 /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      1232  2089563 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     13088  2091081 /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     10872  2089495 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     25520  2089295 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     31424  2089557 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     44360  2091076 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      7104  2089589 /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      1640  2089294 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3    138776  2091080 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      5792  2089405 /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      8240  2089292 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     28936  2089549 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     20920  2089552 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3     29120  2091086 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3      7992  2089555 /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
pidgin    23253   ManiacDan  mem       REG        8,3    107356  3497993 /usr/share/mime/mime.cache
pidgin    23253   ManiacDan  mem       REG        8,3   5004204  3637285 /usr/share/icons/hicolor/icon-theme.cache
pidgin    23253   ManiacDan  mem       REG        8,3   6569884  3637993 /usr/share/icons/gnome/icon-theme.cache
pidgin    23253   ManiacDan  mem       REG        8,3    638600  3613567 /usr/share/icons/Humanity/icon-theme.cache
pidgin    23253   ManiacDan  mem       REG        8,3    256316  3448849 /usr/lib/locale/en_US.utf8/LC_CTYPE
pidgin    23253   ManiacDan  mem       REG        8,3    966938  4170750 /usr/lib/locale/en_US.utf8/LC_COLLATE
pidgin    23253   ManiacDan  mem       REG        8,3        54  3449736 /usr/lib/locale/en_US.utf8/LC_NUMERIC
pidgin    23253   ManiacDan  mem       REG        8,3      2454  3449397 /usr/lib/locale/en_US.utf8/LC_TIME
pidgin    23253   ManiacDan  mem       REG        8,3       286  3449398 /usr/lib/locale/en_US.utf8/LC_MONETARY
pidgin    23253   ManiacDan  mem       REG        8,3        52  3457034 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
pidgin    23253   ManiacDan  mem       REG        8,3        34  3449770 /usr/lib/locale/en_US.utf8/LC_PAPER
pidgin    23253   ManiacDan  mem       REG        8,3        77  3449768 /usr/lib/locale/en_US.utf8/LC_NAME
pidgin    23253   ManiacDan  mem       REG        8,3       155  3449399 /usr/lib/locale/en_US.utf8/LC_ADDRESS
pidgin    23253   ManiacDan  mem       REG        8,3        59  3449400 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
pidgin    23253   ManiacDan  mem       REG        8,3        23  3449739 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
pidgin    23253   ManiacDan  mem       REG        8,3     26048  3425402 /usr/lib/gconv/gconv-modules.cache
pidgin    23253   ManiacDan  mem       REG        8,3       373  3449401 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
pidgin    23253   ManiacDan    0r      CHR        1,3       0t0     1290 /dev/null
pidgin    23253   ManiacDan    1u      REG        8,3   5536291  4562956 /home/ManiacDan/.xsession-errors
pidgin    23253   ManiacDan    2u      REG        8,3   5536291  4562956 /home/ManiacDan/.xsession-errors
pidgin    23253   ManiacDan    3u     unix 0xf4fa5e00       0t0  1343958 socket
pidgin    23253   ManiacDan    4r     FIFO        0,6       0t0  1343960 pipe
pidgin    23253   ManiacDan    5w     FIFO        0,6       0t0  1343960 pipe
pidgin    23253   ManiacDan    6r     unix 0xf4fa6c00       0t0  1343961 socket
pidgin    23253   ManiacDan    7w      REG        8,3      1866  4661330 /home/ManiacDan/.purple/logs/jabber/ManiacDan@192.168.69.180/coworker@jabber.myCompanyJabberServer.local/2009-11-04.113949-0600CST.txt
pidgin    23253   ManiacDan    8r     FIFO        0,6       0t0  1343972 pipe
pidgin    23253   ManiacDan    9w     FIFO        0,6       0t0  1343972 pipe
pidgin    23253   ManiacDan   10u     FIFO        0,6       0t0  1343973 pipe
pidgin    23253   ManiacDan   11u     FIFO        0,6       0t0  1343973 pipe
pidgin    23253   ManiacDan   12u     FIFO        0,6       0t0  1343974 pipe
pidgin    23253   ManiacDan   13u     FIFO        0,6       0t0  1343974 pipe
pidgin    23253   ManiacDan   14u     unix 0xcd293e00       0t0  1343982 socket
pidgin    23253   ManiacDan   15u     unix 0xd824fa00       0t0  1345465 socket
pidgin    23253   ManiacDan   16u     unix 0xd824ee00       0t0  1345467 socket
pidgin    23253   ManiacDan   17u      DIR       0,10         0        1 inotify
pidgin    23253   ManiacDan   18u     IPv4    1345571       0t0      TCP ManiacDan.myCompanyJabberServer.local:36955->jabber.myCompanyJabberServer.local:xmpp-client (ESTABLISHED)
pidgin    23253   ManiacDan   19u     FIFO        0,6       0t0  1345616 pipe
pidgin    23253   ManiacDan   20u     IPv4    1345626       0t0      TCP ManiacDan.myCompanyJabberServer.local:59251->yw-in-f125.1e100.net:xmpp-client (ESTABLISHED)
pidgin    23253   ManiacDan   21u     unix 0xd824da00       0t0  1346034 socket
pidgin    23253   ManiacDan   22r     FIFO        0,6       0t0  1345617 pipe
pidgin    23253   ManiacDan   23u     unix 0xd824f400       0t0  1346036 /tmp/orbit-ManiacDan/linc-5ad5-0-4c43b836bad17
pidgin    23253   ManiacDan   24u     unix 0xd824dc00       0t0  1346039 /tmp/orbit-ManiacDan/linc-5ad5-0-4c43b836bad17
pidgin    23253   ManiacDan   25u      REG        8,3     57440  3711269 /usr/share/sounds/purple/send.wav
pidgin    23253   ManiacDan   26u     unix 0xcd291200       0t0  1346235 socket
pidgin    23253   ManiacDan   27u      CHR        1,9       0t0     1717 /dev/urandom
pidgin    23253   ManiacDan   28u     unix 0xcd292200       0t0  1346236 socket
pidgin    23253   ManiacDan   29u     FIFO        0,6       0t0  1346237 pipe
pidgin    23253   ManiacDan   30u     FIFO        0,6       0t0  1346237 pipe
pidgin    23253   ManiacDan   31u     FIFO        0,6       0t0  1346238 pipe
pidgin    23253   ManiacDan   32u     FIFO        0,6       0t0  1346238 pipe
pidgin    23253   ManiacDan   33r     unix 0xcd290a00       0t0  1346242 socket
pidgin    23253   ManiacDan   34w      REG        8,3     57440  3711269 /usr/share/sounds/purple/send.wav
pidgin    23253   ManiacDan   35u     unix 0xd824ea00       0t0  1346396 socket
pidgin    23253   ManiacDan   36w     unix 0xd824de00       0t0  1346397 socket
pidgin    23253   ManiacDan   37r     FIFO        0,6       0t0  1346398 pipe
pidgin    23253   ManiacDan   38w     FIFO        0,6       0t0  1346398 pipe
pidgin    23253   ManiacDan   39r     FIFO        0,6       0t0  1346399 pipe
pidgin    23253   ManiacDan   40w     FIFO        0,6       0t0  1346399 pipe
pidgin    23253   ManiacDan   41u     unix 0xd824f800       0t0  1346403 socket
pidgin    23253   ManiacDan   42r      REG        8,3     57440  3711269 /usr/share/sounds/purple/send.wav
pidgin    23253   ManiacDan   43u     unix 0xdd09de00       0t0  1346502 socket
pidgin    23253   ManiacDan   44u     unix 0xdd09dc00       0t0  1346503 socket
pidgin    23253   ManiacDan   45r     FIFO        0,6       0t0  1346504 pipe
pidgin    23253   ManiacDan   46w     FIFO        0,6       0t0  1346504 pipe
pidgin    23253   ManiacDan   47r     FIFO        0,6       0t0  1346505 pipe
pidgin    23253   ManiacDan   48w     FIFO        0,6       0t0  1346505 pipe
pidgin    23253   ManiacDan   49u     unix 0xf4d92400       0t0  1346509 socket
pidgin    23253   ManiacDan   50r      REG        8,3     55008  3711268 /usr/share/sounds/purple/receive.wav
pidgin    23253   ManiacDan   51u     unix 0xc0b97e00       0t0  1346859 socket
pidgin    23253   ManiacDan   52u     unix 0xc0b94c00       0t0  1346860 socket
pidgin    23253   ManiacDan   53r     FIFO        0,6       0t0  1346861 pipe
pidgin    23253   ManiacDan   54w     FIFO        0,6       0t0  1346861 pipe
pidgin    23253   ManiacDan   55r     FIFO        0,6       0t0  1346862 pipe
pidgin    23253   ManiacDan   56w     FIFO        0,6       0t0  1346862 pipe
pidgin    23253   ManiacDan   57u     unix 0xc0b95400       0t0  1346868 socket
pidgin    23253   ManiacDan   58r      REG        8,3    155888  3711267 /usr/share/sounds/purple/logout.wav
pidgin    23253   ManiacDan   59u     unix 0xcd291600       0t0  1352029 socket
pidgin    23253   ManiacDan   60u     unix 0xcd293200       0t0  1352030 socket
pidgin    23253   ManiacDan   61r     FIFO        0,6       0t0  1352031 pipe
pidgin    23253   ManiacDan   62w     FIFO        0,6       0t0  1352031 pipe
pidgin    23253   ManiacDan   63r     FIFO        0,6       0t0  1352032 pipe
pidgin    23253   ManiacDan   64w     FIFO        0,6       0t0  1352032 pipe
pidgin    23253   ManiacDan   65u     unix 0xcd19ce00       0t0  1352054 socket
pidgin    23253   ManiacDan   66r      REG        8,3     55008  3711268 /usr/share/sounds/purple/receive.wav
pidgin    23253   ManiacDan   67u     unix 0xf658e200       0t0  1352395 socket
pidgin    23253   ManiacDan   68u     unix 0xf5710800       0t0  1352396 socket
pidgin    23253   ManiacDan   69r     FIFO        0,6       0t0  1352397 pipe
pidgin    23253   ManiacDan   70w     FIFO        0,6       0t0  1352397 pipe
pidgin    23253   ManiacDan   71r     FIFO        0,6       0t0  1352398 pipe
pidgin    23253   ManiacDan   72w     FIFO        0,6       0t0  1352398 pipe
pidgin    23253   ManiacDan   73u     unix 0xdcc3e400       0t0  1352403 socket
```

---

### Post by undecim on 2009-11-04
Try closing pidgin, renaming your .purple folder to something else, and starting it again

---

### Post by ManiacDan on 2009-11-04
I have two different instances of pidgin running two different .purples (on two different drives), both with this issue.

But never leave a stone unturned...

Starting with a fresh .purple file and no accounts, everything was fine.

Adding my gtalk account to fresh pidgin, everything was fine.

Opening the window of a google talk contact, everything was fine.

Chatting with a google talk client spikes my CPU.

Started over with a fresh .purple.

No accounts, everything was fine.

Adding my jabber account, everything was fine.

Opening a jabber contact, everything was fine.

Sending a single character to that jabber contact spiked my CPU.

Rolling back to my old .purple and using empathy for now.

It seems that the act of sending a message spikes my CPU, sometimes to more than 100%.  More thoughts?

-Dan

---

### Post by ManiacDan on 2009-11-04
[NOTE:  I thought this was solved but turns out it's not, see below]

"Mark for Re-installation" ended up being the key, something must have gotten screwed in the update.

On a side note, BACK UP YOUR LOG FILES BEFORE YOU RE-INSTALL.

So yeah, I'm back to having a working version of pidgin, and kicking myself for hosing the logs from the last 2 years.

-Dan

---

### Post by ManiacDan on 2009-11-04
Cancel that, re-installing didn't fix it at all, and now I've deleted my log files on top of that.  Switching to Empathy until I read something about this issue.

-Dan

---

### Post by ManiacDan on 2009-11-04
For real this time, I fixed it.

I re-installed libpurple, pidgin, and all the pidgin plugins that I had already installed.

The process was:
1)  I upgrade to 9.10
2)  pidgin upgrade comes with it, one of the features of which is "voice and video hurrah!"
3)  My pidgin goes all to hell, "voice and video" isn't in my list of plugins, 5 people ask me "why is it telling me to view your webcam, aren't you at work?"
4)  I re-install libpurple, otr, etc.
5)  Voice and video is now an option I can disable
6)  Pigin starts working again

Marking this thread solved...hate computers.

-Dan

---

### Post by pcaustin on 2009-11-05
I don't see this as solved.  How do I "unsolve" this thread?  I have turned on the debug window and waited for the cpu to go up.  In both cases, I see something similar to this at the exact time the cpu goes up:

> (12:25:40) oscar: incomingim_ch1: unknown TLV 0x000d (len 27)
(12:25:40) oscar: incomingim_ch1: unknown TLV 0x0013 (len 1)
(12:25:40) oscar: Received IM from jxxxx78726 with 1 parts
(12:25:40) util: Writing file /home/paul/.purple/icons/4bccc92f06e979b577a31733d0d181486be9fdb2.jpg
(12:25:40) oscar: Parsing IM part, charset=0x0000, charsubset=0x0000, datalen=75
I know that receiving the IM isn't the trouble, so I'm guessing that writing out the icon is.

I had this problem with the pidgin installed by Ubuntu 9.10 but not on previous versions.  I still have this problem even though I updated pidgin as described at [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

I am now running pidgin version 2.6.3

---

### Post by ManiacDan on 2009-11-05
Go into synaptic and "mark for reinstallation" both pidgin and the libpurple core library, plus any other results for "pidgin" that you may have, like OTR.  That fixed it for me.

-Dan

---

### Post by ManiacDan on 2009-11-09
Sorry to open this back up, but the issue returned.  I'm not going to re-install libpurple every week because of this, that's stupid.  If there's any other data any experts need, please let us know.

If I have time later in the week, I'll be filing an official bug report too.  If I get any information there, I'll post it here.

-Dan

---

### Post by ManiacDan on 2009-11-10
I was having what I thought was an unrelated issue with Flash taking a lot of CPU, so I did some research.  I was already using the latest version of flash-nonfree, so the only thing left was to update my proprietary ATI driver to the most recent version (9.10, not to be confused with Ubuntu 9.10).  I did so, and my flash problem went away on reboot.  Also on reboot pidgin loaded...and didn't display any of the CPU hogging symptoms.

There were no other changes to the system other than installing the ATI driver and rebooting.  As odd as it sounds, new video drivers seem to have fixed pidgin's CPU usage.  To the other member of this thread having problems: if that fixes it for you, I think we can file it under "wtf, solved I guess."

-Dan

---

### Post by ManiacDan on 2009-11-11
Nevermind, came back on its own.  It seems that the symptoms are time related, about 18 hours after a reboot.  The video drivers fixed flash, but that was a red herring.

-Dan

---

### Post by newton21989 on 2009-12-07
I can confirm this problem. Running Pidgin 2.6.2 (libpurple 2.6.2) on Ubuntu Karmic Koala 9.10 x86-64. Pidgin automatically connects to IRC and displays an MOTD when it starts... which eats up my Intel Core 2 Duo. I don't suspect graphics; I have integrated Intel crap. ManiacDan, did you file a bug report?

---

### Post by Linuxforall on 2009-12-07
Open terminal, type sudo add-apt repository ppa:pidgin-developers/ppa and hit enter.

Hit the update manager and your pidgin will be upgraded to the latest version and see if your issue goes away.

---

### Post by ManiacDan on 2009-12-08
I was waiting to confirm "for real" but the pidgin problem went away on the last update (a couple days ago).  I disabled my sounds just in case, but if the latest build works for Newton I think that will do it.

-Dan

---

