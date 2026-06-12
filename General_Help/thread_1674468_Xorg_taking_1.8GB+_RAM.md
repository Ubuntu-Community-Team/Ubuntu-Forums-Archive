---
title: "Xorg taking 1.8GB+ RAM"
date: 2011-01-23
forum: General Help
---

### Post by kizi86 on 2011-01-23
hiya folkz, didnt exactly know where to put this thread so i just put it in general help..

so here goes my problem, lately I've noticed Xorg being taking way to much memory, up to 1+GB of ram (see output of "top":

Tasks: 200 total,   1 running, 199 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.2%us,  4.5%sy,  0.3%ni, 84.3%id,  0.6%wa,  0.0%hi,  0.2%si, 
Mem:   2060876k total,  2008992k used,    51884k free,    37704k buffer
Swap:  1502040k total,   896692k used,   605348k free,   382980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND   
23413 kizi      20   0  2616 1132  820 R    4  0.1   0:00.02 top       
 1320 root      20   0 1855m 1.1g 9312 S    2 54.7 551:47.41 Xorg      
 3491 kizi      20   0 35860 5480 4452 S    2  0.3  25:53.28 multiload-
 3567 kizi      20   0  7620 1788 1412 S    2  0.1   6:01.44 verlihub  
 3595 kizi      20   0  171m 9804 6972 S    2  0.5   0:14.28 xfce4-term


can somebody point me to what i can do to fix this?

---

### Post by tigerstripedcat on 2011-01-24
install and run the command 'xrestop' to see what is using all that memory.

---

### Post by kizi86 on 2011-01-24
here is the output of xrestop:
xrestop - Display: :0.0
          Monitoring 34 clients. XErrors: 0
          Pixmaps:    4366K total, Other:      47K total, All:    4413K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier    
1e00000     5   32    0    3   16     1875K      1K   1876K  3381 Desktop
1c00000     5   32    0    5   20      937K      1K    938K  3380 Desktop
2200000     5   32    1    9   30      881K      2K    883K 13756 Terminal
0000000     1    0    2    0  134      468K      5K    473K   ?   <unknown>
5000000    73   37    1  156  310      171K     10K    182K 28491 xfwm4
1600000    11   32    1   23   60       22K      3K     25K  3379 xfce4-panel
2e00000     4   34    0    5   11       10K      1K     11K  3491 Kerfisvakt
0e00000     8   37    1    1   11        4B      2K      2K  3351 scim-panel-gtk
2c00000     7   61    0    2   14        8B      1K      1K  3493 notification-a
3400000     2    4    1    6   25       12B      1K      1K  3532 polkit-gnome-a
1000000     3    3    1    2   25        2B      1K      1K  3357 xfce4-session
1a00000     3   30    0    1   31        4B      1K      1K  3383 xfce4-settings
2000000     7   33    0    4   18        7B      1K      1K  3433 xfce4-menu-plu
0200000     2    1    1    0    7        0B      1K      1K  1046 <unknown>
2400000     4   31    0    3   13        6B      1K      1K  3450 xfce4-sensors-
2600000     5   32    0    1    9        4B      1K      1K  3451 xfce4-xfapplet
3c00000     4   31    0    2   10        8B      1K      1K  3565 Sound

---

### Post by tigerstripedcat on 2011-01-24
Hmmm.  None of this sums up to anywhere close to 1.8 gig.  Can you copy and paste the 'top' output.  Does this happen when you first start the computer?  Have you applied all updates (apt-get update/upgrade)?  What version are you running? 10.10?

---

### Post by kizi86 on 2011-01-24
> **tigerstripedcat said:**
> Hmmm.  None of this sums up to anywhere close to 1.8 gig.  Can you copy and paste the 'top' output.  Does this happen when you first start the computer?  Have you applied all updates (apt-get update/upgrade)?  What version are you running? 10.10?
here is top:

top - 16:04:14 up 5 days, 22:20,  1 user,  load average: 1.24, 1.45, 1.
Tasks: 203 total,   1 running, 202 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.8%us,  4.3%sy,  0.3%ni, 84.8%id,  0.6%wa,  0.0%hi,  0.2%si, 
Mem:   2060876k total,  2010812k used,    50064k free,    23264k buffer
Swap:  1502040k total,   957232k used,   544808k free,   245368k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND   
13849 kizi      20   0  494m  81m  26m S   27  4.1  41:20.42 chrome    
13799 kizi      20   0  507m  93m  23m S   14  4.7   3:11.90 chrome    
 1320 root      20   0 1957m 1.1g  12m S    2 54.7 577:22.28 Xorg      
 3600 kizi       9 -11  152m 3528 2680 S    2  0.2 175:27.84 pulseaudio
13904 kizi      20   0  193m  28m  10m S    2  1.4   0:50.39 xchat     
13952 kizi      20   0  154m  37m  15m S    2  1.9   4:54.17 chrome    
14751 kizi      20   0  2616 1140  820 R    2  0.1   0:00.02 top       
    1 root      20   0  2876 1440 1024 S    0  0.1   0:02.04 init      
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd  
    3 root      20   0     0    0    0 S    0  0.0   0:14.05 ksoftirqd/
    4 root      RT   0     0    0    0 S    0  0.0   0:01.03 migration/
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.62 migration/
    7 root      20   0     0    0    0 S    0  0.0   0:21.43 ksoftirqd/
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1

when i start the computer xorg usually takes around 20-30MB, and then gradually increases in size up to 1.9GB..
and yes i have applied all updates and i am running ubuntu 10.10 and i am using the xfce DE

---

### Post by migs73 on 2011-01-24
try reading this; [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

See if it helps make sense of the numbers you are seeing. Especially try,

```
free -m
```

And compare to the webpage.

---

### Post by kizi86 on 2011-01-24
> **migs73 said:**
> try reading this; [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

See if it helps make sense of the numbers you are seeing. Especially try,

```
free -m
```

And compare to the webpage.
i have read that stuff about linux and memory.. but here is the output of free:

free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1905        106          0         24        240
-/+ buffers/cache:       1641        371
Swap:         1466        934        531


how to check whats causing this high memory usage of Xorg?

---

### Post by tigerstripedcat on 2011-01-24
This is absurd there is no way that linux should be taking 1.8 gigs of ram just  for the room to grow.  

Have you ever modified /etc/X11/xorg.conf?

Here is something similar
[http://www.linuxquestions.org/questions/linux-software-2/xorg-using-over-3-gb-of-ram-533450/](http://www.linuxquestions.org/questions/linux-software-2/xorg-using-over-3-gb-of-ram-533450/)

Do you have any special 3d effects running? How about xinerama?

Try rebooting with a live cd and make sure it doesn't happen. It better not.

---

### Post by kizi86 on 2011-01-24
xinerama is turned off, no 3d or special graphics effects, as im trying to run a pretty minimalistic setup..

---

### Post by tigerstripedcat on 2011-01-24
And did you ever modify xorg.conf?  Did you try restarting with a live cd?

---

### Post by kizi86 on 2011-01-24
yes i have modified xorg.conf, as my setup wouldnt boot into x without it, as i got the no screens found error if i didnt.. but i dont have a liveCD at hand at the moment so i cant try that out now...

---

### Post by tigerstripedcat on 2011-01-24
Is 10.10 a fresh install for you, or have you been upgrading from previous versions of ubuntu?  How old is your hardware?  Most hardware should be supported under ubuntu, so "no screens found" should also be rare.  Try a liveCD and see if you A) still get a 'no screens found' error and B) if you get this crazy xorg problem.  

Also note that you can run a liveCD off of a usb drive:

[www.pendrivelinux.com](www.pendrivelinux.com)

---

### Post by kizi86 on 2011-01-24
> **tigerstripedcat said:**
> Is 10.10 a fresh install for you, or have you been upgrading from previous versions of ubuntu?  How old is your hardware?  Most hardware should be supported under ubuntu, so "no screens found" should also be rare.  Try a liveCD and see if you A) still get a 'no screens found' error and B) if you get this crazy xorg problem.  

Also note that you can run a liveCD off of a usb drive:

[www.pendrivelinux.com](www.pendrivelinux.com)
its an upgrade from 10.04, (i upgraded the same day 10.10 was released) but this issue just recently showed up, that no screens found is somewhat related to the fact that my monitor is abit <snip> and doesnt "announce" its edid, so i have to manually add all the metamodes and stuff for the monitor via xorg.conf .. funny stuff.. when i installed the OS in the first place, i tried it with a liveCD and no problem, but as soon as it was installed and logged into my new system, no X for me becuz of that no screens found error, so i had to make a xorg.conf .. and sowwy i cant do a pendrive liveCD as i dont own one :P

---

### Post by tigerstripedcat on 2011-01-24
Ok, well if you boot with a liveCD now it works ok?   What does the xorg.conf look like when you boot with the liveCD.  Can you just copy that over (after making a backup of your current xorg.conf).  I know they have done fancy stuff with xorg.conf in the live cds these days, but ATM it seems to be related to something from the upgrade/your configuration.

Just copy/paste your xorg.conf here and then booth with the liveCD and copy/paste that one here too.

Do you have an ATI card?
It seems like other people were having similar problems with you:

[http://www.google.com/search?aq=f&sourceid=chrome&ie=UTF-8&q=xorg+using+1+gb+of+memory#sclient=psy&hl=en&q=xorg%20using%20gb%20OR%20gigs%20or%20gbs%20%20memory%20OR%20ram%20ubuntu%20&aq=&aqi=&aql=&oq=&pbx=1&fp=7f8f799ac13308b3&pf=p&pdl=500](http://www.google.com/search?aq=f&sourceid=chrome&ie=UTF-8&q=xorg+using+1+gb+of+memory#sclient=psy&hl=en&q=xorg%20using%20gb%20OR%20gigs%20or%20gbs%20%20memory%20OR%20ram%20ubuntu%20&aq=&aqi=&aql=&oq=&pbx=1&fp=7f8f799ac13308b3&pf=p&pdl=500)

But this was with around version 9.  

How did you do your upgrade?

---

