---
title: "CPU Usage and Firefox"
date: 2009-09-30
forum: General Help
---

### Post by Romala on 2009-09-30
Dear friends,
how to make lower CPU Usage, it is a screen-shot in time of ordinary browsing.  2.6.24-24-386 

> top - 21:27:14 up  1:01,  4 users,  load average: 0.79, 0.63, 0.52
Tasks: 101 total,   3 running,  98 sleeping,   0 stopped,   0 zombie
Cpu(s): 57.3%us,  2.3%sy,  0.0%ni, 40.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1554804k total,   869100k used,   685704k free,    67760k buffers
Swap:  7598704k total,        0k used,  7598704k free,   527212k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6147 roman     20   0  244m 109m  26m R 57.3  7.2  15:46.65 firefox            
 5397 root      20   0  294m  27m 8872 S  4.7  1.8   3:12.01 Xorg               
 6245 roman     20   0 93344  20m  11m R  2.0  1.4   0:11.08 gnome-terminal     
 6066 roman     20   0 21384  12m 7812 S  0.7  0.8   0:07.66 metacity           
 6103 roman     20   0 44828  11m 9480 S  0.7  0.8   0:01.78 nm-applet          
    1 root      20   0  2980 1868  544 S  0.0  0.1   0:01.60 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   40 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  169 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  207 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  208 root      20   0     0    0    0 S  0.0  0.0   0:00.08 pdflush            


Thank you

---

### Post by Giblet5 on 2009-09-30
Define "ordinary browsing".

This forum is very light and efficient, while MarketWatch.com will hammer your browser and make your CPU cry.

Flash is a HUGE cpu hog, but so too are Javascript and Java apps (when they're written by people with teensy tiny little brains that look a lot like cat yarp).

Install the AdBlock, NoScript, and FlashBlock plugins and I'll wager your cpu will sit idle most of the time.

---

### Post by QIII on 2009-09-30
AdBlock is good, but once the ads that would have been loaded are done (assuming they don't use Flash or Java) the CPU load would drop anyway.

I use AdBlock because I don't like door-to-door salesmen or the time they take to load while I want other more important stuff to load.

The problem with FlashBlock and NoScript is, of course, that if you want to view media using Flash and Java, you have to turn them off.

Trade offs...

But for the purposes of testing, I suggest you do exactly that and take a look at top again.

---

### Post by Giblet5 on 2009-09-30
> **QIII said:**
> The problem with FlashBlock and NoScript is, of course, that if you want to view media using Flash and Java, you have to turn them off.

That's why FlashBlock and NoScript provide the ability to permanently allow whole or partial sites full access.

I see no drawback to this, other than a 30-second learning curve, and it might just keep a web vendor from sniffing your cookies ... or beans.

---

### Post by QIII on 2009-09-30
I guess I wasn't clear, and you said it better.  I should have said "...for that page."

AdBlock, likewise, allows you to make adjustments by website.

For instance, to view content on Hulu, you have to allow ads (AdBlock) and Flash (FlashBlock).

National Geographic is the same, if you want to watch some of the content on their main page.

---

### Post by Romala on 2009-09-30
Giblet5, QIII, thank you,
could you explain, why "4 users" in top - there's only one on a computer?

---

