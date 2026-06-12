---
title: "CPU constantly running at 90%"
date: 2011-10-15
forum: General Help
---

### Post by noveus on 2011-10-15
I have checked the CPU usage using the "top" function and this is what i found:

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3002 root      39  19  180m 161m 6404 R   93  4.0   0:34.37 update-apt-xapi    
 1208 root      20   0 63508  45m  14m R   65  1.1  21:26.95 Xorg               
 1719 ren       20   0 44972  10m 8888 S   25  0.3   8:45.45 gdl_box            
 1658 ren       20   0  246m 133m  33m S    4  3.3   0:47.79 compiz             
 2174 ren       20   0  289m  51m  18m S    3  1.3   0:37.59 chromium-browse    
 1622 ren       20   0  6832 3168  916 S    2  0.1   0:18.42 dbus-daemon        
 1666 ren        9 -11  160m 6816 4896 S    1  0.2   0:13.85 pulseaudio         
 1791 ren       20   0 84368  21m 9.9m S    1  0.5   0:21.10 unity-panel-ser    
 2601 ren       20   0 77196  14m  10m S    1  0.4   0:01.02 gnome-terminal     
 1689 ren       20   0 64448 9908 7440 S    1  0.2   0:08.88 indicator-multi    
 2052 ren       20   0  430m 134m  42m S    1  3.3   0:43.84 chromium-browse    
 2204 ren       20   0  209m  71m  20m S    1  1.8   0:23.22 chromium-browse    
 1647 ren       20   0  121m  14m  10m S    0  0.4   0:01.09 gnome-settings-    
 1754 ren       20   0 22688 9580 7776 S    0  0.2   0:00.38 unity-window-de    
 1814 ren       20   0 42512 4284 3496 S    0  0.1   0:03.00 indicator-appli    
 1897 ren       20   0 74976  29m 9840 S    0  0.7   0:02.44 ubuntuone-syncd    
 2661 ren       20   0  2820 1192  868 R    0  0.0   0:01.84 top    


The update-apt-xapi thing seems to consume alot of CPU. How can i disable it? Thanks.

---

### Post by noveus on 2011-10-15
After rechecking it, it is the XORG that takes up most of the CPU processors.

Tasks: 184 total,   3 running, 181 sleeping,   0 stopped,   0 zombie
Cpu(s): 39.5%us, 30.2%sy,  0.0%ni, 29.2%id,  0.7%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   4119744k total,  3753576k used,   366168k free,   530432k buffers
Swap:  2184804k total,      156k used,  2184648k free,  1962564k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1208 root      20   0 60896  40m 9288 R   95  1.0  30:12.95 Xorg               
 1719 ren       20   0 45056  10m 8544 R   31  0.3  11:23.79 gdl_box            
 2174 ren       20   0  356m 108m  20m S    3  2.7   1:06.04 chromium-browse    
 1658 ren       20   0  254m 135m  25m S    2  3.4   1:11.48 compiz             
 1622 ren       20   0  6832 3168  916 S    1  0.1   0:25.67 dbus-daemon        
 1666 ren        9 -11  160m 6640 4720 S    1  0.2   0:20.31 pulseaudio         
 1791 ren       20   0 84628  21m  10m S    1  0.5   0:29.41 unity-panel-ser    
 6268 ren       20   0  253m 128m  21m S    1  3.2   0:05.60 chromium-browse    
 2052 ren       20   0  447m 128m  35m S    1  3.2   0:57.74 chromium-browse    
 2089 ren       20   0  152m  20m  13m S    1  0.5   0:13.18 chromium-browse    
 1045 root      20   0  3420  628  484 S    0  0.0   0:00.17 irqbalance         
 1689 ren       20   0 64884  10m 8088 S    0  0.3   0:12.51 indicator-multi    
 2204 ren       20   0  210m  68m  20m S    0  1.7   0:29.02 chromium-browse    
 2546 ren       20   0  243m 100m  21m S    0  2.5   0:20.06 chromium-browse    
 6302 ren       20   0  2820 1188  868 R    0  0.0   0:00.02 top                
    1 root      20   0  3316 1832 1244 S    0  0.0   0:00.48 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd

---

### Post by LinuxFan999 on 2011-10-15
Which version of Ubuntu are you using?

---

### Post by uzzo2 on 2011-10-15
> **LinuxFan999 said:**
> Which version of Ubuntu are you using?
I just updated to 11.10, I'm not having this problem from what I can tell. But I was used to having panels and the sensors applet running to be able to watch all of it while I'm working. Does anyone know how to do this with the new version?

---

### Post by noveus on 2011-10-17
Ubuntu 11.10

---

### Post by linuxwin2 on 2011-10-17
Try to kill this process
```
$sudo kill -9 3002

```
then check the speed of the system.

---

### Post by noveus on 2011-10-18
I dont think i can kill the XORG operation. =/

---

### Post by Mark Phelps on 2011-10-18
The command results are obviously flawed. 

For one, it says you have four processes running when you clearly have more than that.

More important, if you add up the CPU% of the top few processes, you get MORE than 100% -- which is not possible.

If you're basing your concerns solely on the results of this command, you're being misled.

---

### Post by DZ* on 2011-10-18
Try to kill the gdl_box process. It is the "google desktop" process, but not its crawler, and I don't think it's supposed to run at high CPU. Google stopped supporting this program ): It looks like it is misbehaving in 11.10.

---

### Post by peter_altherr on 2011-10-22
can absolutely confirm this. i was using google desktop search before as it was indexing all my documents very reliable, so i was always able to find them :-) unfortunately gdl_box does not behave in oneiric... and what a shame to no longer support it. as i was not able to find a workaround i switched to tracker/tracker-needle. it requires some familiarizing but now i can deal with.


greetings

peter

---

### Post by DZ* on 2011-10-24
> **peter_altherr said:**
> can absolutely confirm this. i was using google desktop search before as it was indexing all my documents very reliable, so i was always able to find them :-) unfortunately gdl_box does not behave in oneiric... and what a shame to no longer support it. as i was not able to find a workaround i switched to tracker/tracker-needle. it requires some familiarizing but now i can deal with.

I'm like a squirrel and its nuts -- never know where is what on my computer and ***absolutely*** need full text indexing. Google desktop was a great program... and Beagle before that.

I've currently settled on recoll, which in many respects is short of amazing. For example, it indexes attachments such as PDFs inside of offline emails (confirmed to work with IMAP folders of thunderbird and kmail, although not with evolution). I just needed to add an appropriate folder in the indexer preferences.

---

### Post by noveus on 2011-10-31
> **peter_altherr said:**
> can absolutely confirm this. i was using google desktop search before as it was indexing all my documents very reliable, so i was always able to find them :-) unfortunately gdl_box does not behave in oneiric... and what a shame to no longer support it. as i was not able to find a workaround i switched to tracker/tracker-needle. it requires some familiarizing but now i can deal with.


greetings

peter

> **DZ* said:**
> Try to kill the gdl_box process. It is the "google desktop" process, but not its crawler, and I don't think it's supposed to run at high CPU. Google stopped supporting this program ): It looks like it is misbehaving in 11.10.



It is what you both suggested, it is the Google Desktop program that took up a big chunk of it. I have uninstall it now and its working flawlessly. So which file indexer you guys are using now? I loved my Google Desktop. ):

---

### Post by feistybird on 2011-11-21
> **noveus said:**
> It is what you both suggested, it is the Google Desktop program that took up a big chunk of it. I have uninstall it now and its working flawlessly. So which file indexer you guys are using now? I loved my Google Desktop. ):

I'm still using Google Desktop Linux for my desktop search... Tracker/Tracker-needle is so useless , it can't even index PDF files unless rebuild manually with proper configurations.

I noticed that the GDL tray icon flickers a lot in the Gnome 3 so I guess this is what caused very high CPU Load. Unfortunately there is no way to hide the tray icon in Gnome 3 Desktop, so I log in to Unity Desktop , and hide the GDL icon rom the notification area using this trick here [http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html), but blacklist GDL instead of whitelist it - you may also you dconf-editor to change this too.

Not sure if this made any difference, but my GDL actually became much more stable after this tweak! I mean the high CPU load could occasionally happen sometimes when running too much programs altogether in Unity, but not very often now.

---

