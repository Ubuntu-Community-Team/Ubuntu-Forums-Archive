---
title: "Computer Lagging, CPU Spikes"
date: 2010-01-08
forum: General Help
---

### Post by warfacegod on 2010-01-08
Any help with this would be greatly appreciated because I have no idea how to diagnose let alone repair this issue, so thanks in advance.

For the last several days my laptop has been "lagging". When typing (such as now) the cursor will disappear and no letters will appear for a second or I get doubling letters. Example: the word "laptop" will come out as "laaptoppp". When I hover the cursor over a link it will sometimes not highlight it right away. When I scroll up or down in Fire Fox or in my folders the screen will move a little, freeze, and then shoot down (or up) very quickly. Often Ctrl-c simply won't work. Plus several other things that all add up to being very frustrating.

I have the system monitor applet on a panel and I've noticed my CPU spiking periodically to 100%. When it happens it's rythmic, like this: A....A....A....A....A.... and then stops after a while. I've watched the processes and I'm fairly sure it's xorg doing it. My wife complained to me about her desktop doing similar things about a day before I saw that my laptop is doing this.

I am fairly computer literate (no expert but no novice either) and I am totally stumped. Back in my Windows days (long, long ago in a...etc. etc.) I'd have said virus but here? Not so sure.

---

### Post by Sef on 2010-01-09
1) What are your system specs?

2) Application > Accessories > Terminal

then copy and paste (or type) in the terminal the word top.

---

### Post by warfacegod on 2010-01-09
Thanks for the reply.

```
warfacegod@warfacegod-laptop:~$ top

top - 01:11:56 up  5:43,  2 users,  load average: 0.05, 0.26, 0.25
Tasks: 153 total,   5 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.9%us,  6.8%sy,  0.0%ni, 70.9%id,  0.0%wa,  0.2%hi,  4.2%si,  0.0%st
Mem:   2061252k total,   948692k used,  1112560k free,    78892k buffers
Swap:   578300k total,        0k used,   578300k free,   454836k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3854 root      20   0  101m  33m  16m R   20  1.7   2:27.06 nautilus           
 1360 root      20   0  130m  64m  11m S   10  3.2  16:27.75 Xorg               
 1894 warfaceg  20   0 24916  10m 9020 S    6  0.5  19:34.47 multiload-apple    
 3695 warfaceg  20   0  122m  45m  10m R    6  2.3   2:14.85 compiz.real        
 4013 warfaceg  20   0 38160  13m  10m R    4  0.7   0:01.09 gnome-terminal     
 2870 warfaceg  20   0  387m 117m  44m R    3  5.9   7:36.34 swiftfox-bin       
 2050 warfaceg  20   0  146m  20m  15m S    2  1.0   0:01.84 kded4              
 2728 warfaceg  20   0 67800  16m  13m S    2  0.8   0:00.70 knotify4           
 2055 warfaceg  20   0 72068  17m  13m S    1  0.9   0:00.99 kglobalaccel       
 4034 warfaceg  20   0  2468 1180  884 R    1  0.1   0:00.27 top                
  854 messageb  20   0  3184 1464  748 S    0  0.1   0:04.07 dbus-daemon        
  870 haldaemo  20   0  6272 4188 3492 S    0  0.2   0:00.75 hald               
 1856 warfaceg  20   0 29792 2496 1984 S    0  0.1   0:20.04 gvfs-fuse-daemo    
 1876 warfaceg  20   0  3164  916  732 S    0  0.0   0:05.19 syndaemon          
 1877 warfaceg  20   0 47268  24m  14m S    0  1.2   1:01.65 gnome-panel        
 1882 warfaceg  20   0 34732  14m  10m S    0  0.7   0:05.47 nm-applet          
 3861 root      20   0  7320 4268 2112 S    0  0.2   0:02.06 gconfd-2           

```

---

### Post by warfacegod on 2010-01-09
2.8 Ghz P4 Hyper Thread / 2 GB RAM / 64 MB nVideo 5200Go

Toshiba Satellite P25-s607

---

### Post by warfacegod on 2010-01-09
I always try not *bump* a thread fo at least a day but I really need assistance with this.

---

### Post by muteXe on 2010-01-09
'top' updates itself every 5 seconds, so it might be worth staring at it for a while. You might spot a pattern of what's hogging your CPU.

---

### Post by Leppie on 2010-01-09
which nvidia drivers are you using?

---

### Post by Project PWNED on 2010-01-09
I have roughly the same specs on my machine. I ditched GNOME and installed IceWM. It took my RAM load, which was 20% with GNOME, and took it down to 8%.

---

### Post by warfacegod on 2010-01-09
muteXe
> 'top' updates itself every 5 seconds, so it might be worth staring at it for a while. You might spot a pattern of what's hogging your CPU.

I spent 10 minutes watching processes in System Mon. scrolling up and down in F.F. and Nautilus, and I'm almost totally convinced it's xorg. It would jump from 4 - 8% to 16 - 65%. The spiking started again also and it looked like xorg as well.


Leppie
> which nvidia drivers are you using?

NVIDIA accelerated graphics driver (version 173) [recommended]


Project PWNED
> I have roughly the same specs on my machine. I ditched GNOME and installed IceWM. It took my RAM load, which was 20% with GNOME, and took it down to 8%.

I like my desktop environment exactly the way it is (took years of learning and tinkering) and really would rather not have to give it up. I don't mind 24% RAM load when idle, that still leaves lots of overhead room.

---

### Post by Leppie on 2010-01-09
are you by any change browsing websites containing flash? e.g. do you also have this issue when all internet browsers are closed and you're using like openoffice writer?

---

### Post by warfacegod on 2010-01-09
> are you by any change browsing websites containing flash? e.g. do you also have this issue when all internet browsers are closed and you're using like openoffice writer?

I'm using this forum as a test base so I assume no flash. Net browsers can be closed with wireless disconnected and I get similar behaviors. I just watched System Mon. again and it's spiking even longer in OOo. In F.F. or Nautilus the spike would last call it .5 seconds in OOo it's 1.5 - 2 sec.

---

### Post by NoaHall on 2010-01-09
> **warfacegod said:**
> I'm using this forum as a test base so I assume no flash. Net browsers can be closed with wireless disconnected and I get similar behaviors. I just watched System Mon. again and it's spiking even longer in OOo. In F.F. or Nautilus the spike would last call it .5 seconds in OOo it's 1.5 - 2 sec.

Can you paste a screenshot of your desktop(with no windows open) please? It will help to see - sometimes folders or the image can cause problems.

---

### Post by warfacegod on 2010-01-09
You want a shot of just my desktop?

---

### Post by warfacegod on 2010-01-09
Is there a log file or terminal output that should post?

Thanks for all the help so far everyone.

---

### Post by NoaHall on 2010-01-09
> **warfacegod said:**
> You want a shot of just my desktop?

I expect, it may be due to the mounted hard drive appearing on the desktop. This has caused issues for others in the past, and the way to (temp) fix it is to
```

gconf-editor
```
Apps -> Nautilus -> Preferences -> Untick show_desktop

Or

Apps -> Nautilus -> Desktop -> Untick volumes_visible
Try that, and see if the CPU is still being taken up so much.

---

### Post by warfacegod on 2010-01-09
> I expect, it may be due to the mounted hard drive appearing on the desktop.

I had though it might be the external as well but dismissed the idea. It didn't make sense to me that his would star after two months of having the external.

I unmounted the drive and I get the same behaviors. If anything it's a tad worse at the moment.

---

### Post by NoaHall on 2010-01-09
> **warfacegod said:**
> I had though it might be the external as well but dismissed the idea. It didn't make sense to me that his would star after two months of having the external.

I unmounted the drive and I get the same behaviors. If anything it's a tad worse at the moment.

Try disabling the icons then, from above. I know it sounds weird, but it works sometimes.

---

### Post by warfacegod on 2010-01-09
I couldn't find Apps> Nautilus so I used Ubuntu Tweak to not display mounted volumes on desktop. I don't know if that does the same thing in the same way but it didn't change the issue.

I just typed a bunch of random numbers and letters into this box and xorg and swiftfox-bin both went to about 20%. I'm also seeing process phy0 go way up (once 200%) but only rarely.

---

### Post by warfacegod on 2010-01-09
I've rebooted and started up with Compiz off and the behavior persists.

Separately, my wife says her desktop is no longer misbehaving, we'll see.

---

### Post by Leppie on 2010-01-09
you could try running nvidia-xconfig again.

---

### Post by NoaHall on 2010-01-09
> **warfacegod said:**
> I couldn't find Apps> Nautilus so I used Ubuntu Tweak to not display mounted volumes on desktop. I don't know if that does the same thing in the same way but it didn't change the issue.

I just typed a bunch of random numbers and letters into this box and xorg and swiftfox-bin both went to about 20%. I'm also seeing process phy0 go way up (once 200%) but only rarely.

Yeah, it does that same thing.

---

### Post by warfacegod on 2010-01-09
```
warfacegod@warfacegod-laptop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
warfacegod@warfacegod-laptop:~$ sudo /etc/X11/xorg.conf
sudo: /etc/X11/xorg.conf: command not found
```

```
sudo nvidia-xconfig
```

Just gives me another prompt.

---

### Post by warfacegod on 2010-01-09
I think I ***_may_*** have found the culprit. I disabled a Firefox add-on called Ctrl-Fox 1.2.1 and my symptoms have stopped. I don't see how this explains my file browser behaving similarly or OOo or any of the other things, regardless of Firefox running or not.

For the moment, everything seems better. Although scrolling windows with my touchpad or the scroll bar is still causing, what seems to me, heavy CPU load.

---

### Post by Leppie on 2010-01-09
> **warfacegod said:**
> ```
sudo nvidia-xconfig
```

Just gives me another prompt.
i believe that's the correct behavior (i can't confirm this as i don't have a machine with nvidia graphics available).

---

### Post by warfacegod on 2010-01-09
> **Leppie said:**
> i believe that's the correct behavior (i can't confirm this as i don't have a machine with nvidia graphics available).

It still just gives me a command prompt. I tried sudo su and it says: Unknown id: nvidia-xconfig. gksudo also give me a prompt.

---

### Post by warfacegod on 2010-01-09
I'm marking this as solved. It's been several hours since I removed the Ctrl-Fox add-on and no further symptoms. Although scrolling is causing a higher CPU load than I recall, I can live with it. This laptop is nearing the end of it's useful life anyway and I'll be replacing it sometime this spring. (Don't worry laptop, I'll still love you.)

---

### Post by Leppie on 2010-01-09
> **warfacegod said:**
> I tried sudo su and it says: Unknown id: nvidia-xconfig. gksudo also give me a prompt.
sudo su? i just tried it like that (without the nvidia part) and it dropped me to the root shell (on this machine i don't have the root account enabled, yet...)

---

### Post by warfacegod on 2010-01-10
Still getting invalid id: or command not found, with sudo su -xconfig. and variations there of.

---

