---
title: "xorg spikes CPU usage , system stalls"
date: 2010-02-15
forum: General Help
---

### Post by Starman~ on 2010-02-15
I've been searching for a solution for this for a couple weeks. Similar problems describe high or 100% CPU usage, or at least continuous. I have tried many of the suggestions found around Google already. 

Edit: This all started after I upgraded to Karmic. It is a fresh install.
The problem is this. While using a browser (and I'm not talking about loading a page) I get regular CPU usage spikes that cause my system to hesitate. The hesitation shows up in any manner of ways - menus don't popup, entering text is several keystrokes behind, browser won't scroll momentarily, cursor doesn't show, etc.. It lasts a second or two, but happens every 10-20 seconds. 

Solutions already attempted:
Installed Swiftfox
Minimized the number of add-ons
using flashblock
tried to minimize number of processes running
changes to nvidia settings
reloaded nvidia drivers
different versions of flash
basically any solution that looked applicable I've tried.

Here's the typical TOP display during a stall
```
Tasks: 136 total,   4 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 93.7%us,  4.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  2.0%si,  0.0%st
Mem:   1026560k total,   903252k used,   123308k free,    80120k buffers
Swap:   779112k total,      236k used,   778876k free,   472636k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  949 root      20   0  105m  54m  11m R 83.8  5.4  30:53.45 Xorg               
 6022 rick      20   0  371m 125m  42m R 14.0 12.5  27:33.84 swiftfox-bin       
 1638 rick      20   0 78316  42m  10m S  1.3  4.2   7:09.41 compiz.real        
 1639 rick      20   0 80504  25m  14m S  0.3  2.5   0:30.33 gnome-panel        
 1716 rick      20   0 19860 9.9m 7816 S  0.3  1.0   0:09.73 gtk-window-deco    
 8321 rick      20   0 37944  13m  10m S  0.3  1.3   0:00.77 gnome-terminal     
    1 root      20   0  2532 1520 1128 S  0.0  0.1   0:01.04 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
```

I have been able to improve things slightly but the problem is not solved. The CPU% spikes betwwen 45% and 75%, never 100%, but my system locks up briefly.
System info
```

AMD Athlon(tm) XP 2600+
MemTotal:        1026560 kB
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:0a.0 Communication controller: Agere Systems 56k WinModem (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (re

```
I don't know if I got the appropriate info in there but 
I hope someone can assist in trouble shooting this. Its really an annoyance, and its really hard to make it my primary system. I have a dual boot with W2K.

---

### Post by Starman~ on 2010-02-16
can someone recommend where or how I might find help?

---

### Post by Starman~ on 2010-02-22
Still looking for an answer, or an assist.

---

### Post by Starman~ on 2010-02-26
Talking to myself again. Anyone? Suggestions? Wrong forum?

---

### Post by Starman~ on 2010-03-12
Its a real challenge to get any responses, but I am still looking for suggestions.

---

### Post by mcoleman44 on 2010-03-12
First of all, I apologize that no one has responded to this yet.
I take it that your using Firefox. Have you tried a different browser? Chrome or Opera maybe?

Have you installed all of the updates from the update manager? It could just be a bug that has been fixed.

Does it only spike when using a browser or does it spike when you are using the Internet in general?

---

### Post by Starman~ on 2010-03-15
Thank you! A response :)

I listed everything I have tried in the first post. Updates, kernels, etc.
Ya its only when the browser is running, I'm using Swiftfox now, instead of Fx. 

I have not tried another browser. I've tried Chrome in the past but much prefer Mozilla, which is why I'm still using it (and trying to solve the prob).

With so much chat about similar issues around the web I hoped someone would have come up with a solution, but I've tried most of the things recommended. (See first post) What I need is guidance to troubleshoot it.

And thanx for the reply, was beginning to think this forum a hoax, perpetrated on unsuspecting noobs. :popcorn:

---

### Post by Technoviking on 2010-03-15
Flash can cause big spikes in browsers in Linux. This is true of the current flash or the new 10.1 beta.

T-V

---

### Post by mockdeep on 2010-03-17
I've been having this same problem for the last week or so.  I notice it most often when I'm using firefox, but I'm usually using firefox.  I also noticed it today using GIMP.  It cripples my computer and is driving me back to Windows to get productive work done.  It doesn't seem to be limited to Flash.  I have two processors (Dell XPS M1710) and it ate up both of them only in gmail.  Then when the processors hit the top [this happens]("http://ubuntuforums.org/showthread.php?t=1115546").  I've read about the recent NVidia problem, so I'm wondering if that has anything to do with it.  I'm using version 183 I think.

---

### Post by no2498 on 2010-03-17
open a terminal type gstreamer-properties click enter
click video set the plugin to, x window system (no xv)
you can set it back the same way if it does not help
you do need to restart the computer
this worked for me 
hope it helps you

---

