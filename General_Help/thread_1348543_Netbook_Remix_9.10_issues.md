---
title: "Netbook Remix 9.10 issues"
date: 2009-12-07
forum: General Help
---

### Post by rich4d on 2009-12-07
I have a Toshiba Portege M205-S810.  i recently installed a larger, 320GB hard drive in it and some more memory but other than that the system is stock.

Issue 1)  I installed remix using the windows installer and I could not use more than 30 GB for the install.  Other than that, it worked great in a dual boot mode.

Issue 2)  I installed remix using the iso image on a cd and was able to reformat and use the whole drive.  However, I had an error message when I rebooted after install saying:
error: no such device: f7248a82-ffeb-45e6-927c-8872b339b7df

I then used the edit feature in Grub and deleted the line that read no floppy and hit CTRL X to get into Ubuntu.  CPU is at 100% From there i used the terminal to gedit the grub file and removed any no floppy lines and saved the file.  Upon reboot, Issue 2 was no more.

Issue 3)  My CPU is constantly running at 79-100%.  It is very slow and cannot stand it.  I opened System Monitor and there are no processes that are out of the ordinary, i think.

Any help would be greatly appreciated.  I just installed Ubuntu 910 regular ver. and no CPU problems.  I want to use remix though.

---

### Post by arashiko28 on 2009-12-07
On terminal write: top

it will give you the list of the applications that use the most of the CPU.

> ~$ top

top - 12:05:51 up 8 min,  2 users,  load average: 0.79, 0.61, 0.30
Tasks: 151 total,   2 running, 148 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.0%us, 11.1%sy,  0.0%ni, 79.5%id,  1.0%wa,  3.3%hi,  0.2%si,  0.0%st
Mem:   2885692k total,   739456k used,  2146236k free,    40780k buffers
Swap:  3421804k total,        0k used,  3421804k free,   287056k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  905 root      16  -4 16792  600  292 S    2  0.0   0:03.88 udevd              
   40 root      15  -5     0    0    0 S    1  0.0   0:02.51 scsi_eh_1          
12213 root      20   0  518m  84m  28m S    1  3.0   0:11.11 Xorg               
 2477 syslog    20   0 12376  768  596 S    0  0.0   0:00.05 syslogd            
 2568 haldaemo  20   0 36572 5204 4044 S    0  0.2   0:01.25 hald               
 7272 arashiko  20   0  304m  15m  10m S    0  0.5   0:00.46 gnome-terminal     
 7582 arashiko  20   0 19116 1336  988 R    0  0.0   0:00.05 top                
    1 root      20   0  4104  924  632 S    0  0.0   0:01.14 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/1   

This might be helpful.

---

### Post by rich4d on 2009-12-07
I tried that and it says it is between 4-11% yet it is still super sluggish and the system monitor shows it at 90-100%.  No fix.

---

### Post by rich4d on 2009-12-07
Anyone else?

---

