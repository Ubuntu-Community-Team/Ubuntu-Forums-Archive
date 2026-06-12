---
title: "Ubuntu just started freezing intermittently"
date: 2012-06-28
forum: General Help
---

### Post by osarusan on 2012-06-28
I've been using 12.04 since April with few problems, but something strange just started happening this week. Ubuntu has begun intermittently hanging up, and I can't really figure out what is going out.

The hangups are almost unnoticeable, and so I hadn't noticed them until very recently, and I can't really pinpoint when they started. I noticed them first when I was playing music recently, and the machine starts skipping exactly like a broken record. It remains skipping until I move the mouse or type on the keyboard, after which it resumes perfectly. The time between skips is unpredictable -- sometimes a minute, sometimes a few seconds, and sometimes even shorter than that. However, as long as I am typing on the keyboard or moving the mouse, there are no skips at all.

Recently I also discovered it's not just related to music. This morning while typing emails, I noticed that it locks up the same way when I hold a key down, such as backspace or the arrows. The keyboard registers a number of strokes, and then everything stops (including animated gifs, music, etc.) until I let go and type again. If I type nothing for a few seconds, the same thing happens -- the animated cursor disappears, the animated smiley gifs on this page freeze in place, and it all resumes again when I begin typing.

I'm running Ubuntu 12.04x64 on an AMD Athlon II, 16 gigs of RAM, ATI HD4775 with the fglrx drivers. Does anyone have any clue what this problem is, or how to fix it??

---

### Post by Hiéroglyphe on 2012-06-30
I have the same issue:

Since a few days (probably after a weekly update?), my system keep freezing for a couple of sec at random. sometimes it's every 2 minutes, sometimes there's nothing for 5 minutes.

My main activities are playing WoW (so it's maybe related to wine) and surfing (using Opera).

---

### Post by osarusan on 2012-06-30
I wonder if this is the same problem then...

My system isn't "freezing" for any amount of time -- it does freeze, but then the moment I move the mouse to type on the keyboard, it wakes up. It's a weird kind of hang that I've never experienced before.

My only guess is that this could be related to fglrx... as I recently updated from Catalyst 12.2 to 12.4, so I am going to downgrade fglrx and see if the same problem occurs.

---

### Post by osarusan on 2012-06-30
Okay, it's definitely not an fglrx problem. I am using the open source video drivers now, and I am still getting the same issue.

---

### Post by osarusan on 2012-06-30
The only other thing that changed with my PC last week was that I bought a USb wifi modem -- a Buffalo wli-uc-gnm. I'm beginning to suspect this might be the culprit.

---

### Post by osarusan on 2012-07-01
Well, I think I (possibly) solved the problem...

It appeared that the usb wifi modem was causing the problem, but just to be sure, I tried plugging it into a different port on the back of my tower. It worked fine after that...

Apparently the front USB ports on my tower were causing the performance issues. I have no idea why this could be, but that's a bummer. Yet also not a bummer, because the problem was fixed.

---

### Post by BingoRingo on 2012-07-01
I have a similar issue, that I have noticed when watching videos.

The video runs fine and then for maybe one second it skips like the old records and then playback resumes. It does that on YouTube using Chrome and I had the same problem with a 140MB mp4 video I made using my telephone.

It started yesterday, and I had the weekly updates done yesterday, so I guess it's linked.

So far I haven't seen the issue in Firefox but I'll try to watch more videos to see if it happens there too. Haven't noticed this issue running the computer itself.

My system is an Acer AX3950-EW10P with an i3 and the intel video card.

---

### Post by LeftFoot on 2012-07-01
Guys, can you to a 'top'in a terminal and look for 'load average' and '%id'

I have some kind of freezing issue like if the system is under heavy load (which it is since the load average spike). I wonder if you have the same issue or not.

Thx

LeftFoot

---

### Post by BingoRingo on 2012-07-01
> **LeftFoot said:**
> Guys, can you to a 'top'in a terminal and look for 'load average' and '%id'

I have some kind of freezing issue like if the system is under heavy load (which it is since the load average spike). I wonder if you have the same issue or not.

Thx

LeftFoot

Doing nothing else, my LoadAverage is always between .50 and .59; %id is +/- 97%

---

### Post by LeftFoot on 2012-07-01
> **BingoRingo said:**
> Doing nothing else, my LoadAverage is always between .50 and .59; %id is +/- 97%

Same issue as me, welcome to the club Bingo :-k
I don't think this is the same issue as the OP.

For information, here is the threat I started about it ([http://ubuntuforums.org/showthread.php?t=2014007](http://ubuntuforums.org/showthread.php?t=2014007)).

LeftFoot

---

### Post by osarusan on 2012-07-02
This happens for me regardless of the current cpu load.

I've been testing it with various devices and can confirm that it is the USB port... not sure why, but when I have something plugged into my front USB ports, these hangs occur. It doesn't happen with the back USB ports. I can't imagine why this just started happening in the past 2 weeks and never before...

---

### Post by osarusan on 2012-07-09
Okay, another week has gone by, I've stopped using the front USB ports... but the problem is still occurring. I was wrong -- it's not the USB ports.

Ubuntu is still freezing up intermittently, yet every time I am able to instantly unfreeze it by moving the mouse. The freeze doesn't come at a predictable interval, but usually within 10 seconds or so, or also whenever I hold a keyboard key down. It makes the system unable to play movies or videos, because the freezing causes them to loop like a scratched record.

I am not noticing any spike in memory, cpu, load, or anything out of the ordinary when this happens either. Does anyone else have any other ideas?

---

### Post by ozono on 2012-07-11
Hi guys,

Same here... It's really annoying.

I just upgraded my Ubuntu kernel to 3.4.0 trying to fix it, but the issue still persists.

In addition, I've experienced a weird situation (probably related to the same thing) when watching videos (Chrome and Firefox):

The video runs normally, but suddenly it gets kind of stuck and then it continues playing at a faster speed, as if it would have been fast-forwarded. After that, all videos play at the same speed until I click a couple of times through the timeline to fix it. Freaking weird...

Maybe we should report this. Does anyone did it already?

---

### Post by osarusan on 2012-07-11
Yep, that same thing happens to me when watching youtube/flash videos. It plays at extremely high speed and skips as if it were on fast forward.

---

### Post by ozono on 2012-07-11
Could this whole issue be related to the flash plugin itself? 

I'm now listening (trying to) to some music at grooveshark and it happens a lot. ](*,)

---

### Post by ezugaru on 2012-07-11
Hi guys, I had that problem too for the youtube 2x speed, however more than the flash plugin, my solution was to remove pulse audio from my system and letting total control to ALSA, I also stopped using rythmbox since it seems it doesn't work ok w/o pulse.

Right now I dont have any sound problems either web or desktop related.

---

### Post by rudregues on 2012-07-11
Same issue here, with some differences:
-It has started in my notebook some months ago, I was thinking about poor hardware, but started in my powerfull desktop too.
-I cannot stop the freeze moving the mouse or typing some key from keyboard
-The screen begins to darken, then I cannot move mouse/type in keyboard. I have to wait until screen starts to clear, then move again. 
-Yesterday and today the weird bug happened more than 20 times :(

 [ ]'s

---

### Post by ozono on 2012-09-13
Hi there,

I think I've fixed this annoying issue in my computer! Finally!
It seems that when using Alsa there is a config that tries to prevent high volume levels by auto-muting the sound. :confused:
In our case this ends up doing strange things such as freezing the sound every now and then.

In order to solve it, I've followed steps here: [http://www.taringa.net/posts/linux/15285865/Solucionar-audio-entrecortado-en-Ubuntu-12_04.html](http://www.taringa.net/posts/linux/15285865/Solucionar-audio-entrecortado-en-Ubuntu-12_04.html)


For non-Spanish people, here you are how to proceed:

1) Open a console terminal and type: **sudo alsamixer**

2) You'll get into a screen like the one in the article. You just have to navigate (using your left & right arrow keys) to the bar called **<auto-mut>** and change its value to *Disable* (by using the down arrow key)

3) Once you've finished, press ESC key and it will be saved.

From that point on, everything is working like a charm for me.

I hope it helps! ;)

---

### Post by ozono on 2012-09-13
By the way, in case it changes back to *Enabled* after rebooting your computer, follow these instructions (I didn't tried myself though):

1) Open a console terminal and type: **sudo alsactl store**

2) Create a new file for the new audio profile (in case you don't have it yet): **sudo nano /etc/rc.conf**

3) Add the following line to the file: **DAEMONS=(syslog-ng network crond alsa)** 
Save the changes (CTRL+O) and close the file (CTRL+X)

That's it! ;)

---

