---
title: "Xorg using 1.3GB of RAM"
date: 2009-10-19
forum: General Help
---

### Post by MiniZiper on 2009-10-19
Image: [http://i35.tinypic.com/kbc6t0.png](http://i35.tinypic.com/kbc6t0.png)



Is this a bug? I tried googling around, but the most up-to-date info was '06.

---

### Post by QIII on 2009-10-19
Do you have an ATI GPU, particularly and integrated one?

---

### Post by -Zeus- on 2009-10-19
I assume you have tried logging out and back in?  What version/distro are you running?

---

### Post by P4man on 2009-10-19
yes its a bug. More precisely a memory leak. Could either be in xorg or in the videodrivers. Is your machine up to date? Can you try newer videodrivers (what card do you have?) If everything is up to date Id file a bug report against xorg.

In the meanwhile restart X should be a workaround. control + alt + backspace is a quick way to do that if its enabled in Mint.

---

### Post by Giblet5 on 2009-10-19
What is it really using? Is it in the top-ten memory hogs Hall-o-Shame?

```
ps auxf | sort -nr -k 4 | head -10
```

X is using 1.8% of memory on this system.

Your desktop seems a bit obsessive in terms of monitoring gadgets. Are you looking for problems so hard that you're creating them?

---

### Post by P4man on 2009-10-19
btw, im not sure what rosetta beta is, but you have a lot of instances consuming a ton of ram as well.. is that normal?

---

### Post by Giblet5 on 2009-10-19
> **-Zeus- said:**
> I assume you have tried logging out and back in?  What version/distro are you running?

Great question.

JD?

---

### Post by MiniZiper on 2009-10-19
> **QIII said:**
> Do you have an ATI GPU, particularly and integrated one?

Yes. ATI. Not integrated. Has separate VRAM (1GB)

> **-Zeus- said:**
> I assume you have tried logging out and back in?  What version/distro are you running?

9.04 Mint variant

> **Giblet5 said:**
> What is it really using? Is it in the top-ten memory hogs Hall-o-Shame?

```
ps auxf | sort -nr -k 4 | head -10
```

X is using 1.8% of memory on this system.

Your desktop seems a bit obsessive in terms of monitoring gadgets. Are you looking for problems so hard that you're creating them?

LOl I just started learning how to use conky :D But no I doubt conky is causing xorg to use over 1GB of RAM

> **P4man said:**
> btw, im not sure what rosetta beta is, but you have a lot of instances consuming a ton of ram as well.. is that normal?

Distributed computing project [http://boinc.bakerlab.org/rosetta/](http://boinc.bakerlab.org/rosetta/)

They do use RAM (~300mb per core). It's normal.

---

### Post by QIII on 2009-10-19
If anyone is interested ...

I did some research on this a while back.  There was, at that time, a regression in Xorg that caused a huge memory leak, particularly when certain types of graphical elements were displayed.

I have also surveyed my machines and found that, at least for my machine with an ATI GPU, Xorg used as much as 10 times the memory as my other machines.

I think this has already been submitted to launchpad.

---

### Post by P4man on 2009-10-19
> **Giblet5 said:**
> Great question.

JD?

cant you guys tell from the screenie ? Hes got enough monitors to give a few clues :p Its linux mint 7, 32 bit (based on jaunty)

---

### Post by Giblet5 on 2009-10-19
> **P4man said:**
> cant you guys tell from the screenie ? Hes got enough monitors to give a few clues :p Its linux mint 7, 32 bit (based on jaunty)

I've...uh...got nuthin.

Your KGO is mightier than mine. (Keen Grasp of Obvious)

---

### Post by QIII on 2009-10-19
Don't you just hate it when the most obvious thing is so obvious you see right past it?

I feel properly spanked, so I will go lick my wounds ...

---

### Post by -Zeus- on 2009-10-19
hostname: felipe-asusmint :D

---

### Post by P4man on 2009-10-19
I guess its not that obvious if you've never seen Mint. But that desktop has Mint written all over it (icons, start menu, panel layout and theme). Add to that the kernel given in top right and you know its gotta be the jaunty based one, which is mint 7. (in theory I guess it could have been any other gnome based distro heavily modded)

---

### Post by MiniZiper on 2009-10-19
> **-Zeus- said:**
> I assume you have tried logging out and back in?  What version/distro are you running?

Well, yes. When I restart everything is normal with swiftfox and rosetta taking up most of the RAM. But after a day or so Xorg takes the cake for RAM usage.

I thought it was something fixable.

---

### Post by P4man on 2009-10-19
> **-Zeus- said:**
> hostname: felipe-asusmint :D

 LOL. I even missed that obvious clue. I guess I gotta concur with QIII now :D

---

### Post by MiniZiper on 2009-10-19
> **P4man said:**
> I guess its not that obvious if you've never seen Mint. But that desktop has Mint written all over it (icons, start menu, panel layout and theme). Add to that the kernel given in top right and you know its gotta be the jaunty based one, which is mint 7. (in theory I guess it could have been any other gnome based distro heavily modded)

ah. yes. my redundant info on screen finally came thru useful :D

---

### Post by QIII on 2009-10-19
Check the lower left corner of the screeny...

---

### Post by dlzerocool on 2009-11-03
I've the same problem here, yesterday xorg goes up to 2gb of memory used.

I'm using kubuntu - Karmic koala x64 stable
Nvidia drivers from ubuntu rep : 185.18.36
(KDE settings -> Kwin -> Texture from pixmap, bilinear)

Thanks for any advice.

Any advice to report correctly this problem on ppa is welcome...
```
sudo lsof -p 1581     
COMMAND  PID USER   FD   TYPE             DEVICE SIZE/OFF       NODE NAME
Xorg    1581 root  cwd    DIR                8,1      480      11513 /etc/X11
Xorg    1581 root  rtd    DIR                8,1      688          2 /       
Xorg    1581 root  txt    REG                8,1  1897888      58108 /usr/bin/Xorg
Xorg    1581 root  mem    CHR                1,5                1484 /dev/zero    
Xorg    1581 root  DEL    REG                0,9            28278792 /SYSV00000000
Xorg    1581 root  DEL    REG                0,9            53444615 /SYSV00000000
Xorg    1581 root  DEL    REG                0,9            53379077 /SYSV00000000
Xorg    1581 root  mem    REG                8,1  4072612      88292 /usr/share/fonts/truetype/unfonts/UnBatangBold.ttf
Xorg    1581 root  mem    REG                8,1   301280      37962 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf                                                                                                               
Xorg    1581 root  DEL    REG                0,9              524290 /SYSV00000000                                      
Xorg    1581 root  mem    REG                8,1    56168      37754 /usr/lib/xorg/modules/input/synaptics_drv.so       
Xorg    1581 root  mem    REG                8,1    37504      80550 /usr/lib/xorg/modules/input/evdev_drv.so           
Xorg    1581 root  mem    REG                8,1   175080      58082 /usr/lib/xorg/modules/libwfb.so                    
Xorg    1581 root  mem    REG                8,1   134120      58073 /usr/lib/xorg/modules/libfb.so                     
Xorg    1581 root  mem    REG                8,1  4244608      99661 /usr/lib/xorg/modules/drivers/nvidia_drv.so        
Xorg    1581 root  mem    REG                8,1    14616      58090 /usr/lib/xorg/modules/extensions/libdri2.so        
Xorg    1581 root  mem    REG                8,1    43304      36916 /usr/lib/libdrm.so.2.4.0                           
Xorg    1581 root  mem    REG                8,1    43768      58088 /usr/lib/xorg/modules/extensions/libdri.so         
Xorg    1581 root  mem    REG                8,1    31232      58094 /usr/lib/xorg/modules/extensions/librecord.so      
Xorg    1581 root  mem    REG                8,1    18824      58087 /usr/lib/xorg/modules/extensions/libdbe.so         
Xorg    1581 root  mem    REG                8,1   106096      58091 /usr/lib/xorg/modules/extensions/libextmod.so      
Xorg    1581 root  mem    REG                8,1 18972488      99669 /usr/lib/libGLcore.so.185.18.36                    
Xorg    1581 root  mem    REG                8,1  1748816      99662 /usr/lib/xorg/modules/extensions/libglx.so.185.18.36                                                                                                                       
Xorg    1581 root  mem    REG                8,1    14256       8531 /lib/libgpg-error.so.0.4.0                         
Xorg    1581 root  mem    REG                8,1   542936      36971 /usr/lib/libfreetype.so.6.3.20                     
Xorg    1581 root  mem    REG                8,1    92752       4395 /lib/libz.so.1.2.3.3                               
Xorg    1581 root  mem    REG                8,1  1490312       1234 /lib/libc-2.10.1.so                                
Xorg    1581 root  mem    REG                8,1    31744       1251 /lib/librt-2.10.1.so                               
Xorg    1581 root  mem    REG                8,1   538920       1238 /lib/libm-2.10.1.so                                
Xorg    1581 root  mem    REG                8,1   490920       8517 /lib/libgcrypt.so.11.5.2                           
Xorg    1581 root  mem    REG                8,1    19640      35942 /usr/lib/libXdmcp.so.6.0.0                         
Xorg    1581 root  mem    REG                8,1   131174       1249 /lib/libpthread-2.10.1.so                          
Xorg    1581 root  mem    REG                8,1   256768      11098 /lib/libdbus-1.so.3.4.0                            
Xorg    1581 root  mem    REG                8,1    67888      36680 /usr/lib/libhal.so.1.0.0                           
Xorg    1581 root  mem    REG                8,1   282168      37017 /usr/lib/libpixman-1.so.0.14.0                     
Xorg    1581 root  mem    REG                8,1    27032      36960 /usr/lib/libfontenc.so.1.0.0                       
Xorg    1581 root  mem    REG                8,1    10288      35928 /usr/lib/libXau.so.6.0.0                           
Xorg    1581 root  mem    REG                8,1   249608      37043 /usr/lib/libXfont.so.1.4.1                         
Xorg    1581 root  mem    REG                8,1    14696       1237 /lib/libdl-2.10.1.so                               
Xorg    1581 root  mem    REG                8,1    26944      37186 /usr/lib/libpciaccess.so.0.10.2                    
Xorg    1581 root  mem    REG                8,1   131680       1231 /lib/ld-2.10.1.so                                  
Xorg    1581 root  mem    CHR              195,0                5819 /dev/nvidia0                                       
Xorg    1581 root  DEL    REG                0,9                   0 /SYSV00000000                                      
Xorg    1581 root  mem    REG                8,1     6136      99663 /usr/lib/tls/libnvidia-tls.so.185.18.36            
Xorg    1581 root    0w   REG                8,1    16740        266 /var/log/Xorg.0.log                                
Xorg    1581 root    1u  unix 0xffff880133d69e00      0t0       5602 socket                                             
Xorg    1581 root    2w   REG                8,1     4958      93043 /var/log/kdm.log                                   
Xorg    1581 root    3u  unix 0xffff880133d6a100      0t0       5603 /tmp/.X11-unix/X0                                  
Xorg    1581 root    4r   REG                8,1    30302      58036 /usr/lib/xorg/protocol.txt                         
Xorg    1581 root    5u   CHR                4,7      0t0       1753 /dev/tty7                                          
Xorg    1581 root    6w   REG                0,3        0 4026531909 /proc/mtrr                                         
Xorg    1581 root    7u  unix 0xffff880137071200      0t0       5718 socket                                             
Xorg    1581 root    8r  FIFO                0,6      0t0       5467 pipe                                               
Xorg    1581 root    9u   CHR            195,255      0t0       5817 /dev/nvidiactl                                     
Xorg    1581 root   10u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   11u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   12u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   13u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   14u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   15u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   16u  unix 0xffff88012f2e0900      0t0       5912 socket                                             
Xorg    1581 root   17u   CHR            195,255      0t0       5817 /dev/nvidiactl                                     
Xorg    1581 root   18u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   19r   REG                0,3        0 4026532192 /proc/acpi/video/VGA/LCDD/state                    
Xorg    1581 root   20r   REG                0,3        0 4026532191 /proc/acpi/video/VGA/LCDD/info                     
Xorg    1581 root   21r   REG                0,3        0 4026532186 /proc/acpi/video/VGA/DVID/state                    
Xorg    1581 root   22r   REG                0,3        0 4026532185 /proc/acpi/video/VGA/DVID/info                     
Xorg    1581 root   23r   REG                0,3        0 4026532181 /proc/acpi/video/VGA/TVOD/state                    
Xorg    1581 root   24r   REG                0,3        0 4026532180 /proc/acpi/video/VGA/TVOD/info                     
Xorg    1581 root   25r   REG                0,3        0 4026532176 /proc/acpi/video/VGA/CRTD/state                    
Xorg    1581 root   26r   REG                0,3        0 4026532175 /proc/acpi/video/VGA/CRTD/info                     
Xorg    1581 root   27u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   28u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   29u   CHR            195,255      0t0       5817 /dev/nvidiactl                                     
Xorg    1581 root   30u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   31u   CHR              195,0      0t0       5819 /dev/nvidia0                                       
Xorg    1581 root   32u  unix 0xffff880133d68000      0t0       6092 socket                                             
Xorg    1581 root   33u   CHR              13,68      0t0       1967 /dev/input/event4                                  
Xorg    1581 root   34u   CHR              13,65      0t0       1459 /dev/input/event1                                  
Xorg    1581 root   35u   CHR              13,72      0t0       4333 /dev/input/event8                                  
Xorg    1581 root   36u   CHR              13,71      0t0       2169 /dev/input/event7                                  
Xorg    1581 root   37u   CHR              13,73      0t0       4344 /dev/input/event9                                  
Xorg    1581 root   38u   CHR              13,69      0t0       1973 /dev/input/event5                                  
Xorg    1581 root   39u   CHR              13,64      0t0       1392 /dev/input/event0                                  
Xorg    1581 root   40u   CHR              13,67      0t0       1769 /dev/input/event3                                  
Xorg    1581 root   41u   CHR              13,74      0t0       4527 /dev/input/event10                                 
Xorg    1581 root   42u   CHR              13,70      0t0       2159 /dev/input/event6                                  
Xorg    1581 root   43u  unix 0xffff88012f2e0f00      0t0       6129 socket                                             
Xorg    1581 root   44u  unix 0xffff88012f2e3000      0t0      20694 socket                                             
Xorg    1581 root   45u  unix 0xffff88012f2e1b00      0t0      20708 socket                                             
Xorg    1581 root   46u  unix 0xffff88012f144c00      0t0       6191 socket                                             
Xorg    1581 root   47u  unix 0xffff88013a567600      0t0      21569 socket                                             
Xorg    1581 root   48u  unix 0xffff8801391b9500      0t0      20804 socket                                             
Xorg    1581 root   49u  unix 0xffff8801391ba100      0t0      20820 socket                                             
Xorg    1581 root   50u  unix 0xffff88013a564f00      0t0      21233 socket                                             
Xorg    1581 root   51u  unix 0xffff88012f144000      0t0      20945 socket
Xorg    1581 root   52u  unix 0xffff88013800c300      0t0      22268 socket
Xorg    1581 root   53u  unix 0xffff88012f2e1800      0t0      21006 socket
Xorg    1581 root   54u  unix 0xffff88013a564000      0t0      21041 socket
Xorg    1581 root   55u  unix 0xffff880100b9f000      0t0     305718 socket
Xorg    1581 root   56u  unix 0xffff8800855c1b00      0t0     305878 socket
Xorg    1581 root   57u  unix 0xffff88013a566400      0t0      21399 socket
Xorg    1581 root   58u  unix 0xffff88012316d800      0t0      21605 socket
Xorg    1581 root   59u  unix 0xffff88012316e700      0t0      21808 socket
Xorg    1581 root   60u  unix 0xffff88012316ed00      0t0      21829 socket
Xorg    1581 root   61u  unix 0xffff88013800e400      0t0      22418 socket
Xorg    1581 root   62u  unix 0xffff88012291b900      0t0      22158 socket
Xorg    1581 root   63u  unix 0xffff88012b5c0f00      0t0      22169 socket
Xorg    1581 root   64u  unix 0xffff88011c150600      0t0      22180 socket
Xorg    1581 root   65u  unix 0xffff880100b9ea00      0t0     206600 socket
Xorg    1581 root   66u  unix 0xffff88013800f300      0t0      25563 socket
Xorg    1581 root   67u  unix 0xffff88011c153600      0t0      22633 socket
Xorg    1581 root   68u  unix 0xffff88013800f000      0t0      27842 socket
Xorg    1581 root   69u  unix 0xffff880100b9c600      0t0      28681 socket
Xorg    1581 root   70u  unix 0xffff8800855c0900      0t0     305859 socket
Xorg    1581 root   71u  unix 0xffff88010fc0c300      0t0     296927 socket
Xorg    1581 root   72u  unix 0xffff8800855c0c00      0t0     300636 socket
Xorg    1581 root   74u  unix 0xffff88013800cf00      0t0     301609 socket
```

---

### Post by P4man on 2009-11-04
Its clearly a memory leak. Hard to say whats causing it, I suggest you experiment a bit,  disable anything you dont really need (desktop effects, any widgets/desklets whatever) keep top open after a fresh, . After trying to narrow it down file a bug report.

---

