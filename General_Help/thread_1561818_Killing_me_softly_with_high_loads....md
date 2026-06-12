---
title: "Killing me softly with high loads..."
date: 2010-08-26
forum: General Help
---

### Post by k999 on 2010-08-26
Hi,

I've read a lot of the posts on high CPU loads and overheated laptops. I am currently running a Karmic kernel on my Lucid Lynx 10.04 system, after also testing a [newer kernel with some patches applied]("http://ubuntuforums.org/showpost.php?p=9603087&postcount=40").

The Karmic kernel is better than the Lucid kernel, but I have similar issues using both, and I'm just wondering what has happened to my laptop. It's still a Toshiba Portege R500, an it still has a dual core Intel U7600 1.2GHz CPU, and 1GB of RAM. Not amazing by any standards, but I'm old enough to remember that this worked fine 6 months ago.

The loads just go mad, almost for nothing. I'm working my way off "high tech" GUI stuff as I get in trouble, because generally that is nicer on the system... I've even been checking my mail with lynx, and that works great! :p

For example, I run mpg321 to listen to some music. That works great, and top shows mpg321 and pulseaudio using about 3% CPU each. This is fine. Then I start Firefox and open a page with some graphics (like an online newspaper), or maybe even lots of javascript (gmail). Then Firefox obviously starts using lots of CPU. But so do mpg321 and pulseaudio, suddenly using up to 30% CPU each. What's up with that? This compounds the problem. So I'm running Firefox and mpg321 and some terminals (to run ssh and top, mostly), and the load on my laptop is suddenly 3 or 4. At this point everything gets super sluggish, so I have to start closing applications.

If I kill mpg321, sometimes I can wait a bit and firefox starts behaving again. Likewise, if I kill firefox, mpg321 (and pulseaudio) calm down again after a while, relaxing down to about 2-3% cpu each.

Here's a snapshot when things are bad:
```

top - 23:52:46 up  8:02,  5 users,  load average: 4.39, 1.53, 0.80
Tasks: 200 total,   6 running, 194 sleeping,   0 stopped,   0 zombie
Cpu(s): 61.1%us, 26.1%sy,  0.0%ni,  8.8%id,  0.7%wa,  2.4%hi,  0.8%si,  0.0%st
Mem:   1017776k total,   968300k used,    49476k free,    81968k buffers
Swap:  2980016k total,     8020k used,  2971996k free,   478952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
12634 ubuntu    20   0 94348 9.8m 9084 R   39  1.0   1:05.52 mpg321
12367 ubuntu    20   0  348m  97m  28m R   35  9.9   2:39.68 firefox-bin
 3645 root      20   0 53800  22m  12m R   34  2.3  15:58.25 Xorg
 4329 ubuntu    20   0  157m 5444 4288 S   26  0.5   2:18.32 pulseaudio
 5139 ubuntu    20   0 51064  14m 9720 R   19  1.5   1:29.51 gnome-terminal
12715 ubuntu    20   0 86848  19m  12m S   12  2.0   0:25.39 plugin-containe

```

and when they are good:
```

top - 23:59:07 up  8:09,  5 users,  load average: 0.44, 1.32, 1.01
Tasks: 200 total,   4 running, 196 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.8%us,  3.9%sy,  0.0%ni, 89.7%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1017776k total,   980252k used,    37524k free,    82628k buffers
Swap:  2980016k total,     8012k used,  2972004k free,   513092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3645 root      20   0 54768  22m  12m S    6  2.3  16:55.02 Xorg
12367 ubuntu    20   0  345m  78m  28m S    3  7.9   4:25.33 firefox-bin
13068 ubuntu    20   0 97908 5640 4904 R    3  0.6   0:02.28 mpg321
 4329 ubuntu    20   0  157m 5284 4124 S    2  0.5   3:18.78 pulseaudio
 4315 ubuntu    20   0  113m  13m  10m S    1  1.3   3:14.90 metacity
12628 ubuntu    20   0  2544 1260  924 R    1  0.1   0:35.98 top

```

OK, so I can accept that firefox is a CPU hog at times. But when that causes other unrelated processes to use more CPU at the same time, it's a system issue! I understand that mpg321 and pulseaudio are related, but when firefox calms down by killing mpg321, something is wrong.

Please note that these two "snapshots" from top are just minutes apart. All I had to do to calm the system down was kill mpg321, and firefox settled down so I could finish this post. I also restarted mpg321 playing the same track - no worries there.

Agony! Anyone have a clue? Does anyone know Linus' emergency hotline number? ;)

---

### Post by grandtoubab on 2010-08-26
this is not an answer but I dont understand what is the benefit to use such program when VLC exists  :=)

---

### Post by AlphaLexman on 2010-08-26
What is your 'swap' to 'memory' ratio?

It should be 1:1 at minimum.

---

### Post by k999 on 2010-08-26
That actually shows in my output from top. As you can see, it's 2:1 swap to memory.

Edit: Actually closer to 3:1.

---

### Post by AlphaLexman on 2010-08-26
Sorry, I didn't see that...

Have you tried 'mpg123' instead of 'mpg321'

...they are slightly different!

---

### Post by k999 on 2010-08-26
I haven't tried mpg123, but I can easily reproduce this with the text mode version of vlc, for example. I think this issue lies deeper than the user space software, because unrelated programs are affecting each other by pushing each other's CPU usage up, increasing the system load a lot when one program has some work to do.

Edit:

Here's what it looks like with vlc (vlc-nox, so no GUI) instead:
```

top - 02:04:43 up 10:14,  6 users,  load average: 3.75, 1.63, 0.75
Tasks: 201 total,   5 running, 196 sleeping,   0 stopped,   0 zombie
Cpu(s): 67.4%us, 25.1%sy,  0.0%ni,  5.2%id,  0.1%wa,  0.9%hi,  1.3%si,  0.0%st
Mem:   1017776k total,   866492k used,   151284k free,    53120k buffers
Swap:  2980016k total,    15392k used,  2964624k free,   372060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
15492 ubuntu    20   0  111m  12m 6204 S   66  1.3   1:37.00 vlc
14742 ubuntu    20   0  281m 108m  28m R   37 10.9   5:39.78 firefox-bin
 3645 root      20   0 53928  21m  11m R   18  2.1  22:48.28 Xorg
 4329 ubuntu    20   0  157m 5604 4440 R   15  0.6   5:53.87 pulseaudio
14424 ubuntu    20   0  2544 1256  924 R    6  0.1   0:52.58 top

```

It's playing an ordinary mp3 file... God knows what it's doing with it. ;) Incidentally, mpg321 handles high load much better than vlc - vlc skips all the time.

---

### Post by AlphaLexman on 2010-08-26
Maybe the culprit is 'pulseaudio' have you tried 'alsa'?

---

### Post by k999 on 2010-08-26
Yes, I have read about pulseaudio causing trouble for some, or at least appearing to. I did "apt-get remove pulseaudio" (which pulled with it a few related packages). Then I tried playing an mp3 with mpg321, and mpg321 pulls about 16-20% cpu all the time. Interesting, because that is quite a lot more than mpg321+pulseaudio used to (when behaving). And if the load rose a bit, the music started "chopping", and I got lots of these:

ALSA: underrun, at least 0ms.

Also tried again with vlc, but I wonder what vlc is doing to this mp3:
```

top - 02:36:01 up 10:46,  6 users,  load average: 2.98, 1.75, 1.06
Tasks: 199 total,   4 running, 195 sleeping,   0 stopped,   0 zombie
Cpu(s): 76.4%us, 16.6%sy,  0.0%ni,  3.5%id,  0.0%wa,  2.4%hi,  1.1%si,  0.0%st
Mem:   1017776k total,   898884k used,   118892k free,    78476k buffers
Swap:  2980016k total,    15324k used,  2964692k free,   440804k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
16541 ubuntu    20   0 37864 9872 5420 S   91  1.0   1:13.99 vlc
 3645 root      20   0 54072  21m  11m R   35  2.1  25:04.03 Xorg
 4315 ubuntu    20   0  113m  13m  10m S   17  1.3   4:27.00 metacity
 5139 ubuntu    20   0 51064  14m 9736 R   17  1.5   2:21.92 gnome-terminal
16286 ubuntu    20   0  2544 1252  924 R    6  0.1   0:19.43 top
16455 ubuntu    20   0  257m  69m  27m S    3  7.0   1:13.36 firefox-bin

```
Tried again with vlc a bit later, then it used only 16% or so... weird.

Edit:

I discovered a curious artifact of uninstalling pulseaudio and the packages that went with it. I have a touchpad on my laptop, and I have disabled "tap to click" on the touchpad, because I find I tap all the time by mistake, which interrupts what I do all the time. Uninstalling pulseaudio caused the "tap to click" to start again, even though it was still disabled under System -> Preferences -> Mouse -> Touchpad. I tried disabling and enabling again, to no avail. I have reinstalled "ubuntu-desktop", which brings pulseaudio back, and now it's disabled again..

---

### Post by k999 on 2010-08-28
As we're speaking of high loads, can someone tell me what "update-apt-xapian-index" is doing? Here's the last listing from "top" I was able to capture:

```

top - 12:46:19 up 13:18,  2 users,  load average: 2.00, 1.90, 1.43
Tasks: 182 total,   2 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  7.9%sy, 45.3%ni, 40.3%id,  0.6%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   1017776k total,   862528k used,   155248k free,    98948k buffers
Swap:  2980016k total,        0k used,  2980016k free,   415360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8393 root      30  10 84304  65m 4740 R   93  6.6  18:37.05 update-apt-xapi
 3704 root      20   0 47264  19m 9080 S    8  1.9   7:22.52 Xorg
 8704 ubuntu    20   0  2544 1244  924 R    7  0.1   0:31.87 top
 4419 ubuntu    20   0 32808  13m  10m S    2  1.3   0:58.42 clock-applet
 8427 ubuntu    20   0 48252  12m 9668 S    2  1.2   0:53.24 gnome-terminal
 3079 root      24   4     0    0    0 S    1  0.0   0:22.24 ktoshkeyd
 4413 ubuntu    20   0 39352  21m  13m S    1  2.1   0:18.05 python
 4585 ubuntu    20   0 32900  18m 4192 S    1  1.8   0:46.71 ubuntuone-syncd
    4 root      15  -5     0    0    0 S    0  0.0   0:00.84 ksoftirqd/0
    9 root      15  -5     0    0    0 S    0  0.0   0:12.48 events/0

```

Why on earth does update-apt-xapian-index need 20 minutes of CPU time? 20 minutes is enough time for a heck of a lot of work on any semi-modern CPU. It single handedly pushes the system load to about 2. That's just antisocial. apt-get update / apt-get upgrade only takes a few seconds. It's forcing high loads on my poor laptop, and if I had been doing anything else, like reading and writing email, it would probably have been going for 30-40 minutes... When I type and the screen is several words behind me, or changing desktops takes several seconds, it actually kills my productivity. Is that just me?

---

### Post by k999 on 2010-09-08
Seems I've worked this one out!

The problem appears to have been an overheating CPU. I have an Intel® Core™2 Duo Processor U7600, which changes frequency as required. It usually runs at 800MHz, but steps up to 1200MHz as required. When it was hot, however, I guess it didn't step up as a measure to avoid overheating.

What set me on the right track were some sudden (clean) shutdowns during high load, specifically while running VMware Player. I looked in dmesg and /var/log/messages, to no avail. But in /var/log/syslog, I found:

```

... kernel: [ 2736.917579] Critical temperature reached (103 C), shutting down.

```

I wish this would have been reported to me better on the next login, so that I could understand why the shutdown had happened. Another suspect I had was that under high loads power management got confused, in case it got too little CPU time because of the high loads. This was a stretch, I know, and as it turns out, the problem was something else.

So I opened my laptop, disassembled the CPU fan rig, and found that the grid the fan blows air out through was pretty clogged with dust. I got that out, recollected the thermal grease over the CPU (didn't have any fresh around) and reassembled everything, and now it's like a new laptop. I can actually watch a youtube video again! The difference is striking. And another example, update-apt-xapian-index runs in just over a minute or so now. That's compared to 20 minutes CPU time last time I checked.

Just thought I'd share in case anyone else came across this thread with a couple of years old laptop that seems to be misbehaving. :)

---

### Post by no2498 on 2010-09-08
you may also try this just remember your settings if you need to set them back

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope that helps you

---

