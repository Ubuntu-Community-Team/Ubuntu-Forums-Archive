---
title: "high cpu usage when checking updates"
date: 2012-01-04
forum: General Help
---

### Post by boregard on 2012-01-04
hi all, when i open update manager & check for updates i can hear  the fan getting really loud, same thing when i open software center. so i  checked it with system monitor and cpu goes up to 100%. as you can see  in screen shot below. anyways is this normal or is something wrong? i  have a acer aspire 5735 laptop with 11.10 installed on it. any advice or  help would be greatly appreciated. thanks.

---

### Post by 2F4U on 2012-01-04
If you look at the graph you see that only one core of your CPU is going up to 100% while the other is doing almost nothing. Also, this peak is for a rather short period of time. I can't say much about the fan but the cheaper Acer notebooks have a pretty small cache and a rather poor thermal management, which is driven by the firmware. I have an Acer similar to yours and the fans are acting similar to yours independent of what OS is used.

---

### Post by Cookieh on 2012-01-04
Same thing happens to me, when my PC is not in use it is mostly 100 % but then after a wile it goes down.. Think its a bug as I have quite a powerful CPU, dont worry about it, doesnt affect the actual performance

---

### Post by boregard on 2012-01-04
thanks for quick reply 2F4U, my suspicion was that it might be the hardware as it made same sounds when i was running vista. maybe i should  try a distro thats lighter on resources. have a good one.

---

### Post by Cookieh on 2012-01-04
Which distro are you running?
11.10 is more lightweight than 10.10 but adds more work on the hardware, so it requires it to lets say HD to run at higher RPM...
Would recommend you to get 10.10 but 11.10 would work best... 
(11.10 is my opinion and would suggest it...):D

---

### Post by boregard on 2012-01-04
> **Cookieh said:**
> Which distro are you running?
11.10 is more lightweight than 10.10 but adds more work on the hardware, so it requires it to lets say HD to run at higher RPM...
Would recommend you to get 10.10 but 11.10 would work best... 
(11.10 is my opinion and would suggest it...):D i'm running 11.10 oneiric. i was thinking maybe kubuntu would be better to run on my computer.

---

### Post by Cookieh on 2012-01-04
If youre going for Kbuntu, I would suggest 10.10 KDE 4.5 Beta if its still on release...
It is known that the most newest version has a lot of bugs

---

### Post by boregard on 2012-01-04
thanks Cookieh, thats something i might try. anyways i'll mark this thread as solved.

---

### Post by 2F4U on 2012-01-04
In my experience, Kubuntu takes even more recource than Unity. If you want something lighter, try Xubuntu or Lubuntu. With respect to Update manager, I usually try to avoid it and even remove it from the auto started applications. I use 

sudo apt-get update
sudo apt-get dist-upgrade

in a terminal to install updates.

---

### Post by sj1410 on 2012-01-04
use commands like top or htop to find top CPU processes

---

### Post by mcduck on 2012-01-04
> **boregard said:**
> hi all, when i open update manager & check for updates i can hear  the fan getting really loud, same thing when i open software center. so i  checked it with system monitor and cpu goes up to 100%. as you can see  in screen shot below. anyways is this normal or is something wrong? i  have a acer aspire 5735 laptop with 11.10 installed on it. any advice or  help would be greatly appreciated. thanks.

It's perfectly normal for the package management to have high CPU usage for a while while checking the updates. It's actually lots of work to do to compare all the installed application data with the latest data of available package versions, and since you'd want the update check completed as quickly as possible it's *supposed to* use as much CPU power as it can during that stage of the update check.

High CPU usage isn't always a bad thing. When you actually want something done quickly, having your CPU idle definitely wouldn't help anything.  ;)

---

### Post by boregard on 2012-01-04
i used the 2 update commands in the terminal & never even heard computer make a noise. i new you could update using terminal but i never knew it would make that much difference. thanks to all who replied!

---

### Post by imachavel on 2012-01-04
> **sj1410 said:**
> use commands like top or htop to find top CPU processes

works for me:

top - 19:19:38 up  2:32,  2 users,  load average: 0.01, 0.08, 0.09
Tasks: 154 total,   2 running, 152 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.1%us,  1.8%sy,  0.0%ni, 92.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3097008k total,  1908472k used,  1188536k free,    43388k buffers
Swap: 33554428k total,       28k used, 33554400k free,  1133924k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1161 root      20   0  246m  95m  57m R    6  3.2   3:06.32 Xorg               
 1786 danel     20   0  204m  91m  28m S    5  3.0   4:45.03 compiz             
 2670 danel     20   0 81244  14m  10m S    5  0.5   0:01.80 gnome-terminal     
 2273 danel     20   0  211m  52m  16m S    4  1.7   7:31.49 plugin-containe    
 2240 danel     20   0  586m 242m  27m S    1  8.0  15:38.60 firefox            
 1704 danel     20   0  6668 3012  892 S    0  0.1   0:28.89 dbus-daemon        
 2730 danel     20   0  2820 1156  856 R    0  0.0   0:00.22 top                
    1 root      20   0  3328 1716 1124 S    0  0.1   0:01.32 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:02.84 ksoftirqd/0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.74 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:01.52 ksoftirqd/1        
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns

---

### Post by DS McGuire on 2012-01-04
I would think, because it is the lightest, Lubuntu should be the best on system hardware.

---

