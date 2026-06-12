---
title: "64-bit freezing (Flash issue?)"
date: 2010-12-13
forum: General Help
---

### Post by aasmith on 2010-12-13
I'm having a problem with my 64-bit system, that looks a lot like this old issue: [http://ubuntuforums.org/showthread.php?t=1313536](http://ubuntuforums.org/showthread.php?t=1313536)

Once or twice a day, the entire system just locks up, and the only way I know to undo it is with a hard reset. (The mouse cursor still moves around--but it can't click on anything.) It did this with a clean Lucid install, and still does it with Maverick. Often, it's when I'm in Firefox (and usually a site with Flash), but I'm not 100% sure of that.

Now, one issue is that I don't know how to diagnose this issue. With the system frozen, it's hard to probe anything to see what went wrong. Is there a particular log file somewhere that I should check out, that may say what happened? (Keep in mind that while I'm competent with programming, I don't know Linux as intimately as some of you do.)

Thanks,
Adam

---

### Post by wojox on 2010-12-13
Install [Flash-Aid]("http://flash-aid-extension.blogspot.com/")

---

### Post by aasmith on 2010-12-13
Alas, it still crashed.

Here's another hint, though: the MP3 I was listening to at the time kept playing. The mouse cursors moves, and the sounds kept going (and I presume therefore that a lot of other programs kept running), but the screen became absolutely non-responsive. Plus, the monitors I have on my taskbar (e.g. memory, processor) froze too.

Thanks though--any other ideas?

Adam

---

### Post by wojox on 2010-12-14
You can look in /var/log/Xorg.0.log

Sounds like a video driver issue. What are you using?

```
lspci | grep VGA
```

---

### Post by aasmith on 2010-12-14
adam@bubo:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310] (rev a2)

---

### Post by dcstar on 2010-12-15
> **aasmith said:**
> 
Once or twice a day, the entire system just locks up, and the only way I know to undo it is with a hard reset. (The mouse cursor still moves around--but it can't click on anything.) It did this with a clean Lucid install, and still does it with Maverick. Often, it's when I'm in Firefox (and usually a site with Flash), but I'm not 100% sure of that.
..........

Do a full SMART test of your disk(s) in case you have some bad blocks.

---

### Post by aasmith on 2010-12-15
> **dcstar said:**
> Do a full SMART test of your disk(s) in case you have some bad blocks.

Done. Disk is fine. I just finished both the short and extended tests.

My best thought is that somehow Flash is doing something that the video drivers or Gnome don't like...but I have absolutely no knowledge of how to test this hypothesis.

Thanks,
Adam

---

### Post by Kranjak on 2011-01-01
I've the some problems, when I open a web page with flash, sometimes, my system freezes and I must reboot.:confused:

---

### Post by FrankT-Qc on 2011-03-01
Same thing here, using the same video controler GT218, GeForce 310.

It happens randomly, not only using flash, but definitively more often when using it.

It also happens on the same machine running Windows 7 64 bits... (Both using the nVidia driver)

I can go for hours without the problem but when it happens once, it starts happening every two minutes or so until I turn off the computer and let it "cool down" for something like an hour...

Definitely smells like a hardware bug...

---

### Post by Yellow Pasque on 2011-03-01
Your system is overheating (Flash is notorious for exposing inadequate cooling systems since it consumes so many CPU cycles). You should probably do something about that.

---

### Post by aasmith on 2011-05-11
I think I might have a happy ending?

I upgraded to Natty, but it said that I didn't have the proper hardware to run Unity. Tried just working with Gnome, but it crashed pretty frequently--I think it was 4 times in an hour. So then I looked at my drivers (System/Admin/Additional Drivers), and found that I wasn't using the proprietary one for my video card--I was using the generic Linux one. So I downloaded the new one, and ran Unity fine.

But then after a day of playing, I decided that I didn't like Unity, and went back to Gnome. It's been a couple of weeks since then, and it hasn't frozen once. But now here's the strange bit--the driver manager claims that "This driver is activated but not currently in use." So I'm not sure what happened...but something got rearranged properly somewhere.

Thanks everyone for your suggestions.

Adam

---

### Post by The Chef on 2011-05-13
For the record, I had this problem too with a 64 bit i5 Intel Shuttle that uses the i5 onboard graphics instead of a video card.  It would crash all the time when there was flash running.  The precise symptom was that the whole screen would go very dark and the whole Gnome desktop and panels would disappear and you could just make out the cursor, but it would not react to mousing.  I would have to power off with the front panel switch.  This would happen about 1 to 2 times a week under normal personal use.

I think (touch wood) that I fixed it.  In Bios, I set IGD Graphics Mode to 64 MB (the lowest) and DVMT Memory to 128 MB (the lowest) and Internal HDMI to "Enabled" (which I think is default).  I have had hundreds of hours of processing since with no crash.  I can still edit HD video and have not noticed any performance effects -- but I am not a gamer.

Hope this helps someone - I was pulling my hair out for weeks.

I wonder whether some combination of the Ubuntu graphics driver, the i5 onboard graphics processing and the Shuttle Bios (AMIBIOS v104 build 7/27/10) is the cause.  The very same machine never displayed this problem with Windows 7 (64 bit) and the higher IGD/DVMI settings.  So, I do not believe the issue is just Bios/Processor.

---

