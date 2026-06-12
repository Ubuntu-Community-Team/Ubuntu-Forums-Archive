---
title: "Firefox 3.6 Memory usage"
date: 2010-02-19
forum: General Help
---

### Post by tanha on 2010-02-19
I'm using Firefox 3.6 from [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) . Its memory usage is usually around 230MB, which is fine. 

But, recently its memory usage for some reason just jumps to about 800-900MB. I don't know why. I close it, open it, and its at about 200MB again. Then a (short?) while later it goes to almost a GB. 

Is this "memory leaking" or a bug that should be filed or something? Has anyone else experienced this? I know that the memory usage has jumped because FF gets laggy when scrolling, for example.

---

### Post by lovinglinux on 2010-02-19
I was experiencing the exact same problem, with the same FF version, from the same ppa. Additionally, I was experiencing problems with firefox-bin process using too much CPU cycles and not shutting down properly when closing Firefox.

I don't know how exactly the problem went away, because I have upgraded to KDE 4.4 and re-installed Ubuntu twice last week (due to excessive tinkering on my part). But I suspect the problem could be caused by an extension, since I have 50 installed and some have the compatibility overridden.

So, try to update Ubuntu and also update your extensions. You could also disable the extensions and check if the problem persists.

---

### Post by tanha on 2010-02-19
Thanks a lot for the suggestion; extensions seem to have been the culprit. I disabled one extension (Gmail Notifier 0.6.4.1) and checked FF's memory usage; it was 180MB. FF has been running for a bit now and there hasn't been any increase in memory usage.

EDIT: It turns out that Gmail Notifier 0.6.4.1 was not the culprit.

---

### Post by tanha on 2010-02-22
Looks like I spoke too soon. The extensions did help, but after a few days, FF is now using 840MB (from the 180MB from which it started and stayed at for a while). It's almost using a quarter of my 4GB of RAM. Is this something I should report / a bug?

from top:

PR  NI  VIRT  RES  SHR   S  %CPU  %MEM    TIME+       COMMAND
20  0  1408m  839m  24m  S    1    21.2   16:27.81    firefox-bin

BTW, when I close and restart FF, it only uses 220MB with the exact same tabs and windows open as before.

Trying FF in safe-mode... will update.

---

### Post by no2498 on 2010-02-22
must be why i use opera now this is all i have running 
looked in htop 167 mb's

---

### Post by tanha on 2010-02-23
OK. So, ran FF in safe-mode... no dice.

Same as before, 846MB:

[FONT="Courier New"]
PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
20   0 1434m 846m  23m R   23 21.4  50:08.05 firefox-bin
[/FONT]

So, this is definitely FF (and memory leak?) should this be reported as a bug?

---

### Post by lovinglinux on 2010-02-23
> **tanha said:**
> OK. So, ran FF in safe-mode... no dice.

Same as before, 846MB:

[FONT="Courier New"]
PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
20   0 1434m 846m  23m R   23 21.4  50:08.05 firefox-bin
[/FONT]

So, this is definitely FF (and memory leak?) should this be reported as a bug?

I would suggest starting Firefox in safe mode and testing it for a while, to see if it is not another extension.

---

### Post by tanha on 2010-02-23
> **lovinglinux said:**
> I would suggest starting Firefox in safe mode and testing it for a while, to see if it is not another extension.

That's what I did :)

---

### Post by lovinglinux on 2010-02-23
> **tanha said:**
> That's what I did :)

Still using too much RAM?

---

### Post by tanha on 2010-02-23
I'd say so at 850MB.

Edit: I mean it starts out fine at about 200MB. Nothing but time changes and it spikes to 800MB.

---

### Post by lovinglinux on 2010-02-23
> **tanha said:**
> I'd say so at 850MB.

I guess the bug report is the way to go then.

---

### Post by tanha on 2010-02-23
> **lovinglinux said:**
> I guess the bug report is the way to go then.

Done.

Thank you.

---

### Post by c0rrupt0r on 2010-03-09
I am having the same problem exactly and I have disabled all my extentions and add-ons just to make sure It wasn't any of those but the problem just keeps showing up no matter what. Has anyone found out anything on this problem and a fix?
Thank you

---

### Post by camaron1 on 2010-03-09
I know it is not exactly help but anyway: you refer to firefox starting on 200 MB as fine but my firefox has always started on 70-80 MB and maybe never go as high as 200 MB even with lots of tabs open. Just a thought.

---

### Post by c0rrupt0r on 2010-03-09
mine is going way above 200MB with only 2 Tabs opened and no more then that, I do not feel I need to be browsing that much on the net to have more then 2 Opened at a time and It gets up to approx. 1GB at times and It has done this to me since Firefox 3.5 has had its problems and It did stop for a few weeks and just recently came back this last week when I got an update to Firefox. I guess maybe I should fall back a version and see what may happen then.

---

### Post by skymera on 2010-03-09
Strange.

IceCat 3.6 is hovering at 98MB.
I'll keep an eye on it and see if it creeps up to silly levels.

---

### Post by tanha on 2010-03-09
> **c0rrupt0r said:**
> I am having the same problem exactly and I have disabled all my extentions and add-ons just to make sure It wasn't any of those but the problem just keeps showing up no matter what. Has anyone found out anything on this problem and a fix?
Thank you

Nothing yet. Here is the bug page [https://bugzilla.mozilla.org/show_bug.cgi?id=548179](https://bugzilla.mozilla.org/show_bug.cgi?id=548179) .

---

### Post by UnrealMiniMe on 2010-03-16
Interestingly, I seem to have the same problem in Firefox 3.5.8 (for Ubuntu 9.10, 64-bit).  I wonder if the memory leak issue crept into a version prior to 3.6?  Mine is leaking like crazy, and it's not a disk caching issue either.

I just left it on overnight, and it ballooned to over 3 gigs.  Here's my free -m from a couple of minutes ago:
[QUOTE=terminal]name@COMPNAME:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3907         54          0         21        244
-/+ buffers/cache:       3641        320
Swap:         4102        486       3616[/QUOTE]

Here are the top lines from top, taken just after that:
[QUOTE=terminal]name@COMPNAME:~$ top

top - 17:30:04 up 10 days, 23:30,  5 users,  load average: 0.16, 3.30, 3.83
Tasks: 197 total,   1 running, 195 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.0%us,  2.4%sy,  0.0%ni, 92.0%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4057192k total,  4006280k used,    50912k free,    23176k buffers
Swap:  4200956k total,   497364k used,  3703592k free,   250580k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
27868 name      20   0 3777m 3.0g  21m S   14 78.2 170:37.00 firefox            
28088 name      20   0  241m  18m  11m S    9  0.5 105:00.57 gnome-system-mo    
 1378 root      20   0  798m  44m 8200 S    3  1.1 471:18.44 Xorg               
25643 name      20   0  473m  39m  10m S    2  1.0   7:55.49 transmission       
 1909 name      20   0  324m  12m 6556 S    1  0.3  35:25.98 compiz.real        
27971 name      20   0  287m  27m 9712 S    1  0.7  25:38.27 npviewer.bin       
27493 name      20   0  226m  13m 8396 S    1  0.3   1:33.69 gnome-terminal     
    1 root      20   0 19456 1000  468 S    0  0.0   0:01.11 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd[/QUOTE]

You can see above that there's technically some free memory left...about 50 megs...but that didn't do me any good when I tried to copy a 1 gig directory in Nautilus and the whole computer froze for over five minutes! :o

I just closed Firefox down again and reloaded my tabs, and it's starting out at a reasonable level again.  Here's free -m:
[QUOTE=terminal]name@COMPNAME:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1062       2900          0         30        270
-/+ buffers/cache:        761       3200
Swap:         4102        326       3776[/QUOTE]

Here's top:
[QUOTE=terminal]name@COMPNAME:~$ top

top - 17:40:00 up 10 days, 23:40,  5 users,  load average: 0.08, 0.62, 2.10
Tasks: 197 total,   1 running, 195 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.9%us,  2.4%sy,  0.0%ni, 92.4%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4057192k total,  1093436k used,  2963756k free,    31356k buffers
Swap:  4200956k total,   334116k used,  3866840k free,   280652k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
32007 name      20   0  740m 290m  27m S   14  7.3   1:29.79 firefox            
28088 name      20   0  241m  18m  11m S   11  0.5 106:08.97 gnome-system-mo    
 1378 root      20   0  798m  44m 8236 S    2  1.1 472:29.15 Xorg               
32143 name      20   0 92620  28m  12m S    2  0.7   0:03.79 npviewer.bin       
27493 name      20   0  227m  13m 8396 S    1  0.3   1:34.13 gnome-terminal     
   74 root      15  -5     0    0    0 S    1  0.0   2:20.08 scsi_eh_4          
25643 name      20   0  473m  39m  10m S    0  1.0   8:00.37 transmission       
31888 name      20   0 19132 1392  980 R    0  0.0   0:02.01 top                
    1 root      20   0 19456 1000  468 S    0  0.0   0:01.11 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd[/QUOTE]

It's only a matter of time before I have to restart Firefox again though, considering it has already allocated dozens of extra megs just since starting this post.  It even continually allocates when I'm not using the computer.  It could be an extension problem, but I'm not exactly heavy on them...these are the ones I have installed:
[LIST][*]Adblock Plus
[*]Session Manager
[*]DownloadHelper
[*]BetterPrivacy
[*]Ubuntu Firefox Modifications
[*]Flash plugin[/LIST]
I think we can rule out the Flash plugin, since its memory consumption is listed separately under npviewer.  The other five could conceivably be the issue, but...given my own experience with 3.5.8 and the OP's with 3.6, I'm not convinced.

---

### Post by tanha on 2010-03-16
> **UnrealMiniMe said:**
> Interestingly, I seem to have the same problem in Firefox 3.5.8 (for Ubuntu 9.10, 64-bit).  I wonder if the memory leak issue crept into a version prior to 3.6?  Mine is leaking like crazy, and it's not a disk caching issue either.

I just left it on overnight, and it ballooned to over 3 gigs.  Here's my free -m from a couple of minutes ago:


Here are the top lines from top, taken just after that:


You can see above that there's technically some free memory left...about 50 megs...but that didn't do me any good when I tried to copy a 1 gig directory in Nautilus and the whole computer froze for over five minutes! :o

I just closed Firefox down again and reloaded my tabs, and it's starting out at a reasonable level again.  Here's free -m:


Here's top:


It's only a matter of time before I have to restart Firefox again though, considering it has already allocated dozens of extra megs just since starting this post.  It even continually allocates when I'm not using the computer.  It could be an extension problem, but I'm not exactly heavy on them...these are the ones I have installed:
[LIST][*]Adblock Plus
[*]Session Manager
[*]DownloadHelper
[*]Flash plugin[/LIST]
I think we can rule out the Flash plugin, since its memory consumption is listed separately under npviewer.  The other three could conceivably be the issue, but...given my own experience with 3.5.8 and the OP's with 3.6, I'm not convinced.

You can try FF in safe mode if you'd like, to see if it's something to do with the add-ons. 

There is no change of status for the bug that I filed with Mozilla; it's still "unconfirmed."

---

### Post by t54 on 2010-04-26
Running Firefox 3.63 on karmic with 3GB RAM. FF starts off using 200MB on loading, then gobbles up 1GB with lightening speed. Karmic gradually slows to crawl then will not run any major apps after FF has been running for a while.

PS
Gnome panel and Nautilus are by far the 2nd and 3rd biggest memory hogs after FF.

---

### Post by v1ad on 2010-04-26
try chrome

---

### Post by lovinglinux on 2010-04-27
> **t54 said:**
> Running Firefox 3.63 on karmic with 3GB RAM. FF starts off using 200MB on loading, then gobbles up 1GB with lightening speed. Karmic gradually slows to crawl then will not run any major apps after FF has been running for a while.

PS
Gnome panel and Nautilus are by far the 2nd and 3rd biggest memory hogs after FF.

I would start it in safe mode and check if the problem persists. If not, then is probably an extension leaking memory.

```
firefox -safe-mode
```

---

### Post by jobix on 2010-04-27
> **v1ad said:**
> try chrome

I tried but Firefox still leaks memory ;-)

To the OP,  I used to have this problem in 8.04. I recently upgraded to 10.04 RC and so far it seems to be okay. I typically have anywhere from 20 to 50 tabs open.

---

### Post by burgechris on 2010-05-08
Wow!  I almost forgot this issue because I went on to other browsers back in 9.10.  My firefox shot up to using 4 gigs vurtual and 3 gigs resident on a 16 gig machine.  I do a LOT of surfing and it is not unusual for me to have up to around 200 tabs open as I do research for a given project and do life.  I spent a little time on it and discovered that if I disabled javascript that the resources went down to about 3 gigs virtual and 2 gigs resident.

I just tried with 10.04 and the latest firefox from the install in safe mode.  After about 10 minutes into it, I get 2.4 gigs virtual and 1.3 gigs resident.  Pages may still be loading as the cpu is at 23%. Memory is at 1.6 gigs.

Would love to see some fixes to this or discover what I can do to fix it.  I miss my firefox but it just doesn't seem able to hang with the big dogs just yet.

---

### Post by burgechris on 2010-05-08
One more thing.  I just tried this link: [http://ubuntuforums.org/showthread.php?t=103930](http://ubuntuforums.org/showthread.php?t=103930) and the restarted it in safe-mode.  Therefore, I have only 2 tabs showing which point to mozilla.  Virtual Memory is 842.8 megs, resident is 77.7 megs and memory is 50.4.

I really don't know what all of that means but there you have it!

---

### Post by Copernicus1234 on 2010-05-08
Usually it has to do with extensions like other people have pointed out. Firefox gets a bad reputation for being a memory hog which is kind of unfair since its not the browser using the memory, its poorly written extensions.

Chrome is no fun. It may be slightly faster to start and have slightly better javascript performance, but its not noticeable in daily use. Firefox with its extensions is still king to me. :)

---

