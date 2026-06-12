---
title: "left mouse button"
date: 2010-05-19
forum: General Help
---

### Post by roadtrash on 2010-05-19
Hello everybody, I finaly made the leap from windows to linux. I got tired of my laptop getting bogged down by spyware. 

I downloaded, and installed ubuntu yesterday and love the way it looks. That was short lived. My left mouse button quits. I can serf the internet for a long time and everything is fine, but if I leave it idle for a few minutes the left button wont respond. The curser moves about the screen, and the right button works, but not the left. I can restart and everthing is fine until left idle for any lenth of time.

I have search all over today reading everything I could find, but no joy. Does anybody have a workaround for this problem? Ovbiously this is a dealbreaker for me if I can not get it resolved. If that is the case can someone suggest anoter distro to try. This is a coffee table laptop that is used for web serfing email, and some video watching. 


Thanks

---

### Post by lisati on 2010-05-19
I've been experiencing a similar effect from time to time with my USB mouse. I initially thought it was a freeze until I realized that moving the cursor round and right-click still worked. 

The workaround I've been using is to use my laptop's touchpad to do something, after which the left-click on the mouse seems to work again.

For me, it's more of an annoyance than a full-time problem, and I haven't bothered looking into a proper fix yet.

edit: I'm using 10.04, installed and fully upgraded from a beta 2 (?) ISO

---

### Post by CFury on 2010-05-19
> **roadtrash said:**
> Hello everybody, I finaly made the leap from windows to linux. I got tired of my laptop getting bogged down by spyware. 

I downloaded, and installed ubuntu yesterday and love the way it looks. That was short lived. My left mouse button quits. I can serf the internet for a long time and everything is fine, but if I leave it idle for a few minutes the left button wont respond. The curser moves about the screen, and the right button works, but not the left. I can restart and everthing is fine until left idle for any lenth of time.

I have search all over today reading everything I could find, but no joy. Does anybody have a workaround for this problem? Ovbiously this is a dealbreaker for me if I can not get it resolved. If that is the case can someone suggest anoter distro to try. This is a coffee table laptop that is used for web serfing email, and some video watching. 


Thanks


Which version of Ubuntu are you using?  What model notebook?  Don't loose hope, I'm sure this is an easily rectifiable issue.  

Oh, and welcome aboard.

Cheers,
C

---

### Post by roadtrash on 2010-05-19
Thanks for the replies. I installed ubuntu 10.04. My laptop is a Sony Vaio PCG-8Y1L. The left button on my touchpad also does'nt work.

I realy don't want to move on but as you can understand this is very frustrating.

---

### Post by QIII on 2010-05-19
Step away from "Post Hoc Ergo Propter Hoc" for a moment and consider coincidental conditions.

Do you have a mouse you could connect to it to see if the behavior affects the mouse?  What I am getting at is eliminating an incidental hardware failure before moving on to possible problems with the OS.

---

### Post by roadtrash on 2010-05-19
I admit I had to look up "Post Hoc Ergo Propter Hoc". I have been messing with this since the AM. I have tried two USB wireless mice, and an old wired one, no luck. 

You may have missed the "touchpad is also doing it" part. I try to be thourough before I make a new thread. I'm not trying to blame the OS, I really like it, but I have had to restart this thing at least 20 times today. Most of the time right in the middle of something. Just call me frustrated

---

### Post by QIII on 2010-05-20
OK.

Let's call it a possible bug then.

If I get the chance (don't know that I will), I'll look up some specs on your machine and prowl through launchpad to see if there is something there.

Would be nice to put a "Solved" by this thread for others who are having the same problem.

---

### Post by roadtrash on 2010-05-20
From my reading about others having the same problem the common denominator seems to be nvidia graphics. I trying mint on a live CD now. On mint my left button is stuck, can't do anything. Man, this is a real dissapointment, I'm so sick of windows. Any suggestions on any other distros to try

---

### Post by roadtrash on 2010-05-20
after looking closer the model number an the bezel is VGN-AR550E

PCG-8Y1L is the model number on the back POS

---

### Post by QIII on 2010-05-20
Hmmm.  Video driver and input device issue.  Could be.  I/O is interrelated, of course.  Xorg may be puking altogether.

Are you running the nVidia proprietary driver on your installed  Ubuntu?

What happens when you deactivate it?

If you are running the open source driver, install the appropriate on for you card.

Give Fedora a try.  But if the problem is a proprietary driver, I don't  know that any distro will work.

---

### Post by roadtrash on 2010-05-20
still trying to get it to work. I thought for sure you guys could help with a seemingly simple but realistically catastrophic problem.

pasted from linuxquestions.org

The problem with this lap is the video card, Nvidia is not supporting the GeForce Go 8400 due to the fact that this video card has so many features.

[http://www.linuxquestions.org/questions/linux-hardware-18/sony-vaio-and-linux-128860/](http://www.linuxquestions.org/questions/linux-hardware-18/sony-vaio-and-linux-128860/)

last post

---

### Post by roadtrash on 2010-05-20
Under hardware drivers there are two choices. I have tried them both. The recommended one works better for this particular problem but does pixilate some.

I have noticed that if I don't connect to a network or open Firefox everything seems fine. I have looked around the OS and even burned a data disk with no problems. When I connect to my WIFI and open Firefox I can surf for an hour as long as I don't leave it idle for a couple of minutes. If left idle BOOM no left click

This truly is a pain in the.........

---

### Post by roadtrash on 2010-05-20
I have Fedora and Mandriva downloading, will post results when available

any more suggestions. I'll try anything

---

### Post by roadtrash on 2010-05-20
nobody?

---

### Post by roadtrash on 2010-05-20
installed windows 7 for now, guess there's no fix. Thanks everybody.

Is there a forum that will actually help support this software?

---

### Post by QIII on 2010-05-20
You said yourself that nVidia is not supporting the card.  If the OEM does not support the card, none of us can do much about it.  OEM's write drivers.  Not Ubuntu.  Not Fedora.  Not Microsoft.   It's not a software problem on the part of the OS.

If the OEM does not write a driver for a particular OS, users of that OS must make do as best they can. 

If they don't have a driver for the card that works with Linux, there is no magic wand.  But there might be a work-around.  Somebody may have found it.  He or she may not be on the forum right now.

We are trying to help.

This is a volunteer operation.  We come here as we can to help.  We  aren't paid to do this.  You can't expect an answer in 5 minutes.  Some  of us have to work, we get home, we spend time with the wife and kids.   We do the laundry, mow the lawn.  And we spend the time we can here.

There may be someone who knows exactly what to do, but hasn't yet seen  your post.  He may be asleep in Madrid or Bangalore.

Failing that, diagnosis takes some time.  I did tell you I would try to  see if I could find something on launchpad regarding your laptop.  I can  look now, since dinner is done, the dishes are put away and the foster  kids are happily sitting on my lap right now watching Transformers on  another monitor.

---

### Post by QIII on 2010-05-20
OK.

If it is actually an nVidia driver problem, please see this:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

According to nVidia's documentation, the GeForce 8400M (which seems to be what came with your laptop) is supported by their driver.

---

### Post by roadtrash on 2010-05-20
sorry if I came of pissy, it's just really  aggravating. I figured this would be an easy fix. The more I got caught up in it, the more of a pain it's been. This is one of the first things, computer related that I have'nt been able to fix[with online help] 


QIII thanks for your help, and more important, thanks for your service both here and there  *salute*

---

### Post by jtravisp on 2010-06-06
For what it's worth, I'm having the same problem- no left mouse button. If I uninstall the nvidia driver, it works again. Frustrating...

---

