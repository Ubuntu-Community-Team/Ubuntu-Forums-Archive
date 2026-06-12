---
title: "System is super slow and almost freezes!!!!"
date: 2011-02-18
forum: General Help
---

### Post by redenex on 2011-02-18
Hey guys, I run Ubuntu 10.10 64 bit on an HP TouchSmart TX-1005 AU laptop. I have 4 GB  RAM. But I find that the response time for the system gets slow, especially when I open some sites (firefox browser) eg: facebook, youtube gmail etc...... I have a 2 MBPS Cable Connection for internet and the slowness is not due to the net issues. But what I find is that the system as a whole almost freeze occassionally, and for the most part is damn too slow. Even changing between firefox tabs is cumbersome. Does anyone know what could be the problem, any idea what I should do? My SWAP memory is 10 GB.

---

### Post by maghoxfr on 2011-02-18
I've been having extremely slow performance as well and it's very annoying. I'll follow this thread.

---

### Post by redenex on 2011-02-18
I really do not know what went wrong, it has been this way for the past 3 weeks or so. It is not the browser alone, even other applications I open, tends to be dead slow.:confused:

---

### Post by heyho on 2011-02-18
Have you tried opening a terminal and using:

```
top
```

to see if you have anything hogging resources?

---

### Post by NightwishFan on 2011-02-18
They really need to fix the swap in the installer to not use so much. :) At the most you probably need 3gb, but I doubt this is what is causing the problems. Now on topic.

Try collecting data on the issue. The program top in the terminal is good for this. Open a terminal and run the command: top  Once you do so, check if any processes are using an unusual amount of cpu (it is sorted highest cpu is at the top). If you notice a process consistently using more than 80-100 then make a note of what it is.

Also paste the output of the command: free -m

Also important is the model of graphic card you have (ati/nvidia/intel)

---

### Post by redenex on 2011-02-18
> **heyho said:**
> Have you tried opening a terminal and using:

```
top
```

to see if you have anything hogging resources?

No, but now I did. Here is the output:

```

top - 00:57:58 up  3:13,  2 users,  load average: 1.39, 1.41, 1.44
Tasks: 167 total,   2 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.3%us, 10.1%sy,  0.0%ni, 62.5%id,  0.0%wa,  0.0%hi,  3.1%si,  0.0%st
Mem:   3796764k total,  1687972k used,  2108792k free,   175084k buffers
Swap:  9764860k total,        0k used,  9764860k free,   817056k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2366 teddy     20   0  505m  20m  13m S   36  0.5  22:58.36 audacious2                                                                                      
 1489 root      20   0  428m  74m  12m S   18  2.0  27:02.11 Xorg                                                                                            
 3897 teddy     20   0  312m  15m  11m R   13  0.4   0:02.35 gnome-terminal                                                                                  
 1999 teddy     20   0  892m 187m  34m S    8  5.0  70:07.68 firefox-bin                                                                                     
 1788 teddy      9 -11  342m 6440 4736 S    7  0.2   7:10.00 pulseaudio                                                                                      
 1885 teddy     20   0  201m   9m 7788 S    3  0.3   2:03.95 geyes_applet2                                                                                   
   50 root      20   0     0    0    0 S    2  0.0   2:42.97 kondemand/0                                                                                     
    3 root      20   0     0    0    0 S    2  0.0   1:25.52 ksoftirqd/0                                                                                     
    7 root      20   0     0    0    0 S    2  0.0   0:45.42 ksoftirqd/1                                                                                     
 3815 teddy     20   0 82696  15m  10m S    2  0.4   0:14.11 npviewer.bin                                                                                    
 3920 teddy     20   0 19276 1328  944 R    1  0.0   0:00.28 top                                                                                             
 1886 teddy     20   0  349m  18m  13m S    1  0.5   1:13.80 clock-applet                                                                                    
   51 root      20   0     0    0    0 S    1  0.0   1:27.08 kondemand/1                                                                                     
    9 root      20   0     0    0    0 S    0  0.0   0:02.80 events/0                                                                                        
  934 root      20   0 88240 4632 3668 S    0  0.1   0:05.02 NetworkManager                                                                                  
 1153 mysql     20   0  183m  23m 6580 S    0  0.6   0:43.27 mysqld                                                                                          
 1766 teddy     20   0  319m  14m 9536 S    0  0.4   0:15.21 gnome-settings-                                                                                 
 1847 teddy     20   0 29180 1056  832 S    0  0.0   0:11.65 syndaemon                                                                                       
    1 root      20   0 23884 2052 1296 S    0  0.1   0:00.84 init                                                                                            
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/0                                                                                     
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT   0     0    0    0 S    0  0.0   0:00.25 migration/1                                                                                     
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
   10 root      20   0     0    0    0 S    0  0.0   0:01.35 events/1                                                                                        
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                          
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                           
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                       
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                              
   17 root      20   0     0    0    0 S    0  0.0   0:00.05 sync_supers                                                                                     
   18 root      20   0     0    0    0 S    0  0.0   0:00.21 bdi-default 
```


Is there anything that is taking up memory?

---

### Post by NightwishFan on 2011-02-18
Your cpu is more than half idle and you have 0k swap used. Nothing seems to be hogging resources. I have a suspicion.. Try going to appearance settings and choosing "clearlooks" as your theme. Does this improve performance?

---

### Post by redenex on 2011-02-18
thank you, I would try to make SWAP 3GB in my next clean install.

> **NightwishFan said:**
> 
Also paste the output of the command: free -m

teddy@HP-TX:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3707       1645       2062          0        173        790
-/+ buffers/cache:        681       3026
Swap:         9535          0       9535


> **NightwishFan said:**
> 
Also important is the model of graphic card you have (exati/nvidia/intel)

teddy@HP-TX:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by redenex on 2011-02-18
> **NightwishFan said:**
> Your cpu is more than half idle and you have 0k swap used. Nothing seems to be hogging resources. I have a suspicion.. Try going to appearance settings and choosing "clearlooks" as your theme. Does this improve performance?

Doesn't help. But I noticed something now. I had actually enabled the "desktop effects" in the "appearance" tab, but now is is disabled automatically. When I try to enable, it searches for available drivers, but says the effects cannot be enabled.

---

### Post by NightwishFan on 2011-02-18
Are you using the ATI driver from Administration -> Additional Drivers? If so, the open source one might be better.

---

### Post by maghoxfr on 2011-02-18
> **redenex said:**
> Doesn't help. But I noticed something now. I had actually enabled the "desktop effects" in the "appearance" tab, but now is is disabled automatically. When I try to enable, it searches for available drivers, but says the effects cannot be enabled.

That happened to me when I had installed the worng drivers or when I had no drivers at all. It doesn't llow you to enable the fx because it can't handle them without graphic card. Look for the right drivers and activate them.

---

### Post by redenex on 2011-02-18
> **NightwishFan said:**
> Are you using the ATI driver from Administration -> Additional Drivers? If so, the open source one might be better.

I was using the open source one till now, currently I am trying to install the Administration --> Additional Drivers version. Just trying out, if that helps. What is surprising is that, even the song that is played in Audacious seems to be affected. And as I type in these, each letter takes a long time to be displayed in the edit box!!! Perplexing indeed!

---

### Post by maghoxfr on 2011-02-18
Deleted

---

### Post by maghoxfr on 2011-02-18
> **redenex said:**
> I was using the open source one till now, currently I am trying to install the Administration --> Additional Drivers version. Just trying out, if that helps. What is surprising is that, even the song that is played in Audacious seems to be affected. And as I type in these, each letter takes a long time to be displayed in the edit box!!! Perplexing indeed!

Question: does it happen to you all the time or it happens in cycles? Because my pc runs awesome, but all of a sudden it runs slow for a couple of minutes, then it runs great again, and so on...

---

### Post by redenex on 2011-02-18
> **maghoxfr said:**
> Question: does it happen to you all the time or it happens in cycles? Because my pc runs awesome, but all of a sudden it runs slow for a couple of minutes, then it runs great again, and so on...

Well, as a start it works fine, but soon it gets slow and clogged.


Now that I have installed the ATI Driver from Administration-->Additional Drivers, I could enable the special effects. Time now is 1:30 AM and need to sleep. Will try to run more applications and browser events tomorrow and shall keep you updated if anything has changed 9for good or bad).

Thanks for the help everyone, have a shining day! Rock on! :guitar:

---

### Post by redenex on 2011-02-18
As of now everything seems to be okay. Shall over load my system tomorrow and see if the problem is still around or rectified.

---

### Post by redenex on 2011-02-19
Well, everything is working good so I assume the issue was the disabled ATI driver, could have been disabled when the new kernel was installed few weeks ago.

---

### Post by NightwishFan on 2011-02-19
Ah excellent I am glad you got it working! Generally such blatant slow downs have to be graphics struggling, unless you have something way out of control Ubuntu should never be slow on 4gb. :)

---

### Post by cottfcfan on 2011-02-19
I would just check your cpu usage now.
From the "top" chart you give, the programs you have open seem to be using an unusually high amount of cpu.
I have 3 gig of memory, less than you, but compare your chart with my attachment.
I'm using the ATI driver as well, so your installing that may have resolved the problem.

---

### Post by redenex on 2011-02-19
@cottfcfan

Thank you, shall keep an eye on that. But as of today, things are good and fast.



@Nightwish Fan

Thank you, I am a Nightwish fan too! keep rocking!:guitar:

---

