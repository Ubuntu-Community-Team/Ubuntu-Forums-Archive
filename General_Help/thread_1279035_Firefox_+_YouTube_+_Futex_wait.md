---
title: "Firefox + YouTube + Futex_wait"
date: 2009-09-30
forum: General Help
---

### Post by p0st_n00bz on 2009-09-30
Hi,
I'm having an annoying problem with Firefox (both 3.0 and 3.5). If my browser is open for a while and I try to watch a Youtube video, there is no sound. If I just quit Firefox and restart it doesn't fix it, because I get a "Firefox is already running" error. I need to go into the System Monitor and kill the process, which always has "futex_wait" as its status. I updated to Firefox 3.5 hoping it would fix this, but it didn't. I have also reinstalled Flash. Is there anything I can do about this? It's really annoying, as I tend to watch a lot of videos.

---

### Post by Lekensteyn on 2009-09-30
Open Bash, and enter this command:
```
sudo alsamixer
```
Use arrows to asjust it.
(this is for sound)

---

### Post by p0st_n00bz on 2009-09-30
The sound itself is fine. It's only in Firefox that it stops working. 

Of course, right now it's working so I can't test out your suggestion anyway, but it's definitely a Firefox issue and not a system sound issue.

---

### Post by p0st_n00bz on 2009-10-01
Ok, it just happened again, and the alsa mixer didn't help. My volume is up, but no sound in Youtube. The video works fine. If I quit Firefox, I have to kill the process, which says "futex_wait." However, if I leave Firefox running, it looks normal.

---

### Post by p0st_n00bz on 2009-10-02
In looking for other people having this issue, I found a post that said to edit /etc/mozilla-firefox/mozilla-firefoxrc, but when I open that in gedit, it is a blank file. Could this have something to do with it?

I can't find anything about this exact issue I am seeing though.

---

### Post by p0st_n00bz on 2009-10-03
No one else has experienced this?

---

### Post by Ella Huovinen on 2009-10-06
I have the same problem with XMMS. When I run xmms I don't get youtube videos. When I close xmms, then the youtube videos load normally. IRRITATING.

I just installed ubuntu jaunty 64-bit. I have alsa packages installed and set (in the sound settings). I also removed pulseaudio.
With intrepid (32-bit) i was able to fix the same problem by going to xmms settings and "Clicking the ALSA output plugin and ensuring the 'Audio Device' is set to 'default' and not the name of your actual sound chipset". 
Now, no such luck.. maybe i should do cartwheels ;)?

THOUGHTS anyone?

---

### Post by Ella Huovinen on 2009-10-07
Don't know what solved it, but now everything seems to be working. Maybbe the imaginary cartwheels :) .

---

### Post by guaka on 2009-10-29
I'm experiencing a very similar problem, but worse: It happens on an LTSP network.

Many users are experiencing applications that block. In the system monitor the status is "futex_wait".  Is there a way to kill processes that have this status for longer than about 10 seconds?  Or is there a way to avoid the problem in the first place?

---

### Post by guaka on 2009-10-29
I found this [http://fingergeek.blogspot.com/2009/05/cure-of-notorious-ubuntu-futexwait-bug.html](http://fingergeek.blogspot.com/2009/05/cure-of-notorious-ubuntu-futexwait-bug.html)

But that's not the problem in this case.

---

### Post by guaka on 2009-10-29
I came up with this to kill all processes with the futex_wait signal:

[FONT=Courier New]ps -eopid,wchan|gr[/FONT][FONT=Courier New]ep futex_wait|awk '{print $1}'|xargs kill[/FONT]

---

### Post by foxymoron on 2010-03-16
Same issues here with Karmic and FF 3.5.8 -  Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.8) 

1) no sound in YouTube when FF has been running for a while
2) can't re-open FF after closing

The only way to get FF running again is to kill the process and restart. On every occasion the process is in [FONT=Courier New]futex_wait_queue_me[/FONT] state. 

Now, I also have a NetBook with UNR running. And guess what: same issue with FF. But now even Google Chrome loses sound after a while on whatever site that has video. 

Could it be Flash that is the problem...?

Any help is appreciated.

---

### Post by qbe9584 on 2010-03-20
Same problem with Firefox in Ubuntu 9.10. Any help is appreciated.

---

