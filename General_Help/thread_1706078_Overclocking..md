---
title: "Overclocking."
date: 2011-03-13
forum: General Help
---

### Post by Jragon on 2011-03-13
Hi,

I did some searching, and I found some commands to see what sort of pc you have:

 ps -eo pcpu,pid,user,args | sort -k 1 -r | head -10
```
jragon@jragons-puter:~$  ps -eo pcpu,pid,user,args | sort -k 1 -r | head -10
%CPU   PID USER     COMMAND
59.7  1788 jragon   /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/1752-1
32.7  1399 root     /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-r1RvJ1/database -nolisten tcp vt7
 2.3  1567 jragon   /usr/bin/pulseaudio --start --log-target=syslog
13.0  1574 jragon   /usr/bin/compiz
12.2  1752 jragon   /usr/lib/firefox-3.6.15/firefox-bin
 1.2  2024 jragon   /usr/bin/skype
 1.2  2015 jragon   python /usr/share/emesene/Controller.py
10.7  2067 jragon   java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
 0.3  1572 jragon   nautilus
jragon@jragons-puter:~$ 
```


iostat
```
root@jragons-puter:/home/jragon# iostat
Linux 2.6.35-27-generic (jragons-puter)     13/03/11     _x86_64_    (6 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          14.35    0.02    4.19    0.55    0.00   80.89

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              11.74       607.28       517.04    1127806     960216
sdb               0.08         0.87         0.00       1621          0

root@jragons-puter:/home/jragon# 

```


grep "model name" /proc/cpuinfo
```
model name    : AMD Phenom(tm) II X6 1090T Processor
model name    : AMD Phenom(tm) II X6 1090T Processor
model name    : AMD Phenom(tm) II X6 1090T Processor
model name    : AMD Phenom(tm) II X6 1090T Processor
model name    : AMD Phenom(tm) II X6 1090T Processor
model name    : AMD Phenom(tm) II X6 1090T Processor

```

I'm using the stock cooler, and I have 4 gigs of ram. I'm on Ubuntu 10.10. Although the specs are good it is still kind of slow, the I have the cpu monitor thing in my task bar and I have put all 6 processers up to max, yet it is still not that fast. It may be the ram. I would like to know how to overclock my cpu and ram. The mother board is:
M4A87tD USB3

---

### Post by Frogs Hair on 2011-03-13
I have not over clocked , hear are a couple of links.
[http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)
[http://forums.overclockersclub.com/index.php?showtopic=173999](http://forums.overclockersclub.com/index.php?showtopic=173999)

---

### Post by cchhrriiss121212 on 2011-03-13
When you say not that fast, what do you refer to? Compile times? Startup speed?

If you want better speed, there are a few tweaks you can do without overclocking (overclocking will not increase speed BTW, it will increase power):
Set swappiness to 0
Install preload
Buy an SSD - on many modern systems like yours, a mechanical HD will be the bottleneck

If you still want to OC, do it via BIOS.

---

### Post by Jragon on 2011-03-13
Ok, could you please tell me how I can set the swappieness and install preload.

Thanks

Jragon

P.S. When I say slow, I mean when I run minecraft and try to do other things there is a lot of lag.

---

### Post by cchhrriiss121212 on 2011-03-13
Swappiness:
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")
Preload you will find in the package manager, you only need to install it, no further setup required.

But I'm not sure these tweaks will cure what you are describing. Lag could be a result of an overtaxed GPU, or something else. Are you using any desktop effects? If so switch them off and note the difference. 

When you get laggy behaviour, open up system monitor, then keep an eye on your CPU usage. If it is hitting 100%, then you will know whether you need to OC or not.

---

