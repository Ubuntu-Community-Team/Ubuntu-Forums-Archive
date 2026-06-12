---
title: "Fire Fox goes B&amp;W and locks up temporarily when uploading"
date: 2011-03-06
forum: General Help
---

### Post by Gosport on 2011-03-06
Fire Fox goes black and white and locks up temporarily when uploading photos on Facebook or sometimes when I am listening to Pandora Radio and things like that.  Eventually the browser recovers but most of the time I give up and close the browser (if Pandora Radio is playing I often have to log out to stop the music from my now closed browser) and try again. I'm thinking Flash has something to do with it.  

Does anyone else have this problem?

---

### Post by Gosport on 2011-03-09
Nobody???

---

### Post by Gosport on 2011-03-13
Still nobody has any ideas??  Are there more details you need?  Thank you.

---

### Post by mörgæs on 2011-03-13
If Ubuntu is going black and white it means that there is 100 % CPU load. 

Running **top** will show which application is responsible for that. Press q for quitting top.

---

### Post by Gosport on 2011-03-17
Thank you!
I'll do that next time I see the problem and post what I see.

---

### Post by Gosport on 2011-03-17
michael@mj-desktop:~$ top

top - 22:40:00 up  2:40,  2 users,  load average: 1.37, 1.08, 0.69
Tasks: 183 total,   2 running, 181 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.9%us,  0.3%sy,  0.0%ni, 64.7%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   3538352k total,  1442088k used,  2096264k free,   141272k buffers
Swap: 10153040k total,        0k used, 10153040k free,   708040k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3320 root      20   0  121m  28m 8292 R   99  0.8   7:13.03 Xorg               
 3614 michael   20   0 76144  33m  13m S    8  1.0   0:56.86 npviewer.bin       
 3574 michael   20   0  752m 165m  32m S    2  4.8   4:00.61 firefox-bin        
 3930 michael   20   0 19224 1428 1028 R    1  0.0   0:01.08 top                
 1577 root      20   0 46696  924  564 S    0  0.0   0:01.86 udisks-daemon      
 3476 michael   20   0  288m  39m   9m S    0  1.1   0:07.97 compiz             
    1 root      20   0 23688 1932 1248 S    0  0.1   0:00.73 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
michael@mj-desktop:~$ q

---

### Post by mörgæs on 2011-03-17
Yes, Xorg is being greedy. It could sound like a Flash problem.

You have to do more tests in order to find out. 

What happens when only working in Facebook or only listening to internet radio? 
How does Chromium behave? 
have you installed Flashblock in all browsers? 
And so on...

Which version of Ubuntu are you using?

---

### Post by Zimmer on 2011-03-17
Not sure whether this may be related.

After recent Firefox update my wife's machine(on Win XP) is running a high CPU temperature when playing a Java Web game (POGO/Word Whomp). It is a Biostar system with liquid cooling so the fan only cuts in if there is heavy use: using Firefox it sounds like the machine is revving up for take off.

The problem is not there when she uses Opera browser to play the game:no fan at all. 
So, is the latest Firefox the problem?

---

### Post by grahammechanical on 2011-03-17
When I access the BBC news web site the screen sometimes goes grey as the BBC server uploads a large video to my machine. It is something I live with. It could be due to the connection speed being affected by a lot of people using my Internet Service Provider at the same time as me or the BBC site not being able to handle the traffic it is getting.

Regards.

---

