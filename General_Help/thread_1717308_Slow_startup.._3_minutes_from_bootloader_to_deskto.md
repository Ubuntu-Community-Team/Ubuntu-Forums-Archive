---
title: "Slow startup.. 3 minutes from bootloader to desktop"
date: 2011-03-29
forum: General Help
---

### Post by goltoof on 2011-03-29
Ever since a standard update a couple weeks ago I've had a myriad of problems, the biggest one though being boot time.  Here's what happens when I turn on the machine:
From bootloader (splash) to kernel loader (blinking cursor) = 50 sec.
Kernel loader to splashscreen = 20 sec.
Splashscreen to login prompt = 55 sec.
login prompt to keyboard working = 26 sec. (wireless, wired works right away)
Logging in to Desktop = 25 sec.

176 secs = ALMOST 3 MINUTES UNTIL I'M IN THE DESKTOP!!

That's worse than Vista.   I've tried a number of things.  For the Bios I read disabling floppy helps.  I tried installing bootchart to see what's going on but it won't load save the .png file..? I installed bum and disabled some services.  I tried profiling in grub...  Nothing has made anything any better.  

No idea why it takes so long for my wireless keyboard to start working. I'm really not sure where to start here since it's loading so slow at every point of the startup process.

Running 10.04

---

### Post by lithopsian on 2011-03-29
It would help to identify the exact processes that are slow.  I'm guessing everything is fine once you get logged in?  That would be a job for bootchart.

---

### Post by goltoof on 2011-03-30
> **lithopsian said:**
> It would help to identify the exact processes that are slow.  I'm guessing everything is fine once you get logged in?  That would be a job for bootchart.

Yes the system runs fine once logged in. I installed bootchart but it's not saving anything.  I've searched through tens of pages for answers, nothing yet.

---

### Post by goltoof on 2011-03-30
Got bootchart working.  What do you make of this?

[http://img88.imageshack.us/i/leedesktoplucid20110330.png/](http://img88.imageshack.us/i/leedesktoplucid20110330.png/)

---

### Post by lithopsian on 2011-03-30
Nope, can't make head nor tail out of that.  Wayy too small:lolflag:  Looks like a lot of stuff starting up though.

---

### Post by goltoof on 2011-03-30
> **lithopsian said:**
> Nope, can't make head nor tail out of that.  Wayy too small:lolflag:  Looks like a lot of stuff starting up though.

Yeah I caught that.. try this
[http://img88.imageshack.us/i/leedesktoplucid20110330.png/](http://img88.imageshack.us/i/leedesktoplucid20110330.png/)

---

### Post by lithopsian on 2011-03-30
Still too small?  I don't think its just me but when I click to magnify nothing happens.  I think it is full size alreadty.

---

### Post by KegHead on 2011-03-30
Hi!

Goto:

System...preferences...start up applications.

Remove items you don't use I.E bluetooth & bluman if you don't use these apps.

KegHead

---

### Post by goltoof on 2011-03-31
> **lithopsian said:**
> Still too small?  I don't think its just me but when I click to magnify nothing happens.  I think it is full size alreadty.

This forum only allows 768 max height for images, this image is 800x6140 px.  

So I posted to imageshack (click image to enlarge).
[http://img88.imageshack.us/i/leedesktoplucid20110330.png/](http://img88.imageshack.us/i/leedesktoplucid20110330.png/)

---

### Post by goltoof on 2011-03-31
> **KegHead said:**
> Hi!
System...preferences...start up applications.
Remove items you don't use I.E bluetooth & bluman if you don't use these apps.



Did that already, disabled a lot of stuff, issue still remains.  Each time I reboot it takes almost exactly the same amount of time, 176 seconds.. ugh.

---

### Post by lithopsian on 2011-04-01
Did Imageshack resize it because it still shows up small for me.

---

### Post by JKyleOKC on 2011-04-01
Clicking the magnifying glass button at imageshack made it large enough to read, but it's showing only a bit over 27 seconds total.

It looks as if there are almost a dozen partitions to mount, and quite a few processes are shown running off the chart. My best guess from what is shown, and the original description, is that some of the listed partitions cannot be found and the boot code is doing a full timeout on each one of them. I've had something a bit similar happen, with a CD drive that's recognized but won't respond properly to some of the commands it receives. However this could just as easily be a red herring...

---

### Post by fela on 2011-04-01
I once had a PC that took 10 minutes to boot. What's wrong with 3 minutes? Sounds pretty quick to me. My server takes about 5 minutes to boot, but it's a rare occurrence, what with the stability of Debian :D

---

### Post by lithopsian on 2011-04-01
OK, got it.  Imageshack isn't working in Firefox 4.0.

Are you running a server farm?  That is a massive amount of hardware!  Network mounts too?

I notice that ureadahead does not seem to be working.  That would probably speed things up for you.  Your boot is heavily IO limited at the moment.

Other than that it doesn't look so bad.  Stuff happening for about 30 seconds, but you should have a desktop after about 20s.  Lots of people would love to have that.

Do you have two cores?  Might be able to sneak in some concurrency since your CPU is never more than half utilised right now.

---

