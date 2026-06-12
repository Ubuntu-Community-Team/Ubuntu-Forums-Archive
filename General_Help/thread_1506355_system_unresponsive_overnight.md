---
title: "system unresponsive overnight"
date: 2010-06-10
forum: General Help
---

### Post by ambroseya on 2010-06-10
OK, 

I have searched everything I can, and this is ultimately frustrating. I am used to a long up-time. I upgraded to Lucid Lynx on Tuesday, and beyond fighting with samba settings which I mostly ironed out, it's been working as normal. 

So, overnight Tuesday I woke up Weds morning and my computer would not respond. It was humming like the monitor was just off, but no mouse shaking, key pressing, power pressing, etc, would allow it to come back on. It required a hard reboot. I figured, one time fluke, right?

Well, this morning, same thing! Won't wake up. I checked syslog, etc, and all I can find is the last things I did before walking away last night, and then the results of booting up this morning. Nothing appears to have happened in between. No errors, nothing out of the ordinary, just NOTHING.

My monitor goes off after 15 min. If I leave it for periods during the day, it comes back to life quickly. So I think the 10 hours or so I left it might be part of the problem - but that's terrible if so - I use it as my print/file server and I want it to not die if I choose to be on a different computer most of a day.

Another (possible?!) contributing factor is that the internet did go off both nights. The first due to a tripped breaker the modem was on (we don't know how long it was out, discovered it in the morning) and the second night overnight due to a cable company issue. 

I've been googling around and the best I can find were issues similar in much earlier versions that don't seem to apply. I have checked all the settings I can find and it looks good. Anyone else having issues? (The system is set to never hibernate or turn off hard drives - only to cut to the monitor and it's the monitor waking up that appears to be the problem.)

---

### Post by ambroseya on 2010-06-10
bump? anyone?

---

### Post by ambroseya on 2010-06-10
After the last while of poking around, I have found that some other people seem to have trouble with the computer waking up from a 'suspend' cycle - but my computer is not supposed to go into suspend mode at all overnight. I've looked at every setting I can find but everything seems to be set so that I should NOT be going into suspend OR hibernate, so it shouldn't be a problem to wake up. 

And the suggestion in most of those problems was to upgrade - but I did upgrade to Lucid which started this whole issue.

---

### Post by ambroseya on 2010-06-11
Welll, I'm still here!!! Meaning, it did NOT go away, and the 3rd night in a row I woke up to unresponsive computer. I'm getting wise about not leaving anything running, but can someone please help me? I'm getting pretty desperate and I'm not finding anything.

---

### Post by warfacegod on 2010-06-11
When is the last time you cleaned the fan and heat sink for your CPU? This sounds like an overheating issue to me.

---

### Post by ambroseya on 2010-06-11
I would have considered that option if it was actually turning off. It still sounds like it is running, in every way, but will not communicate with the monitor in any fashion until it is hard rebooted. If it were overheating, I would expect it to not be running in the morning.

---

### Post by warfacegod on 2010-06-11
My laptop occasional freezes, due to overheating, instead of shutting down. I believe it is when I leave my torrent client running and the two happen to coincide.

---

### Post by ambroseya on 2010-06-11
OK, well, mine is not overheating. My computer is physically sitting right by an AC vent, feels cool to the touch and it's never had a problem until I upgraded earlier this week.

Now, I was off working on my laptop today and came back, and apparently it takes less than 5 hours to have the problem, because I came back and again - no display. Had to hard reboot. This is really annoying and I really have no idea.  I can't leave my computer on (and we're talking the only thing open was a browser- I didn't have my big downloads or anything running) for a few hours and just let it be. I've had this computer for 5 years, running ubuntu for 3.5 years, and never had anything like this occur. If anything, I'm using less processes right now. And when the heavy CPU using things are running, I don't have any errors or freezing. Only when it is left alone and nothing is actually occurring.

---

### Post by -kg- on 2010-06-11
> **ambroseya said:**
> I would have considered that option if it was actually turning off. It still sounds like it is running, in every way, but will not communicate with the monitor in any fashion until it is hard rebooted. If it were overheating, I would expect it to not be running in the morning.

Of course, you realize that, though the computer case might be cool to the touch, this doesn't mean that some internal component isn't overheating, and this problem isn't confined to the CPU.  It could be something on the graphics card or almost anything, including a hard drive getting ready to go.  It could also be something that didn't quite "take" in the upgrade process.  I've had *that* problem a few times! :roll:

Concerning the hard drive...I had an experience similar to what you describe some years back, using XP.  I could boot into XP normally, but after a little while XP would slow down (the rebooting process, too), and finally freeze, making it necessary to hard reboot.

It got bad enough that I could only run it for about 15-30 minutes at a time, so I got another hard drive (thank *goodness* I had the partition backed up!), created the partition scheme, loaded my backup copy to it, then copied my essential files off the old drive with it installed as the slave drive.

Do you think it might possibly be "runaway software" that might be causing the problem?  You might want to boot, pull up "System Monitor," put it on the "Resources" (or "Processes") tab, and notice what's happening at that time.  Then come back in a couple of hours and see if there's something or another that has changed, either in resource usage or a process that seems to be running an inordinate amount, depending on what tab you left System Monitor on.

You might even leave System Monitor on-screen until the freeze up occurs.  Even if the display freezes, you might be able to see events leading up to the freeze.  If nothing appears abnormal at that point, it's likely to be a hardware problem.

---

### Post by warfacegod on 2010-06-11
I wonder if the screen is set to lock when the screensaver activates and the loggin text simply isn't being displayed. This sort of thing your dealing with is exactly why I don't do upgrade installs and I use a separate /home partition. Cool to the touch doesn't mean it isn't overheating. Of course being near an AC does help.

---

### Post by ambroseya on 2010-06-12
Cool to the touch does not mean it is overheating. Correct. However, why would it only overheat after being alone for a certain amount of time (a few hours - I think it takes between 3 and 4 hours) and not when I have heavy processes running while I am using it?

Having a System Monitor running was useless - looked pretty normal, but since the problem is with the display and the display is not there (as in, monitor thinks there is no signal coming to it at all, not that it's frozen on the screen) it doesn't help.

Now, I did not have this problem ever before my upgrade - I had never had to hard-restart my system. Now I have rebooted that way about 6 times this week,, and that's not a good thing. 

Last night I left it doing some heavy image processing ( converting a large pdf to images in such a way that it should have still been going in the morning) and did determine that the images it was churning out one every two minutes quit about 2.5 hours after I left the computer. 

I don't know if it's related to being idle, or lack of input, or what is going on. Suppose, since all of you think so, that it is overheating. What is there in lucid that changed that much since the last version that all of a sudden my computer would do so, with or without heavy processes? 

Why is it that if I keep using my computer for 12-14 hours, it is fine, but it's when I leave it that something would happen?? yesterday I used my laptop, which made it have enough idletime to quit (and it sounds like the hard drive is still running when it does that, so it's not shutting down). Why would it require a certain amount of idle time to stop because of overheating? It's just not logical that it could be a problem here. 

It's this sort of problem: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=300251](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=300251)

The thing is, I do have the setting to turn the monitor off after 30 min - and it does frequently. And wakes up fine, it's after the 2-3 hour mark or so that it ceases to wake up fine.

---

### Post by warfacegod on 2010-06-12
I've had problems with my laptop switching to battery when I have it set to turn the screen off. I have not found a fix for this but I'm almost certain it has to do with the replacement AC adapter I had to buy. A decent work around is to set the monitor to "Blank Screen" after x minutes and disabled "Turn Monitor Off".

If this isn't an overheating issue then my best guess is that you need to do something similar. At least temporarily.

---

### Post by -kg- on 2010-06-12
I just had a thought...you said that the hard drive was still operating and all?  If it seems to be operating normally, and not consistently running, could it be the monitor itself? (It still might be the graphics card...it puts a signal out to the monitor whether there's a load on the CPU or not)

Here a while back, I had a monitor go out.  Of course, it didn't quit after a while...it just went out...but it's quite possible that, after a time, something in the monitor would finally shut itself down.

I had another monitor that was strange like that.  For instance, when rebooting, in the time between the video card shutting down (no signal to the monitor) and posting to begin, it would put itself to sleep.  I would have to turn the monitor off, then back on to bring it out of sleep mode.  The light was on and everything.

Another consideration:  I know you probably have all the time in the world to "watch paint dry", but have you ever been able to "catch it in the act" (i.e., catch it at the exact time that it freezes up)?  Sometimes that's the only way to determine what is happening when you have nothing in the debug logs with which to diagnose what is happening.

And a third:  You say you upgraded...was that via the Upgrade button in Synaptic?  Do (or did) you have any third party software installed; something that wouldn't be upgraded in the process due to the third party repos not being installed, or lack thereof?  Sometimes software that isn't written for the particular release will do something like this, though the effects are usually more immediate and visible. The same would apply to a clean install, but preserving your /home partition (with it's settings and configuration files).

While I can (and just have) upgrade(d) my desktop computer, I most certainly can't do so on my laptop.  Of course, almost all my desktop does is crunch BOINC work units.  Occasionally I'll go down and browse the Internet, but that's about all.  My laptop, however, is what I use for heavy experimentation (I have 3 Linux installations on it, besides Vista) and I can't upgrade or install preserving my /home partition.  I usually have too many settings and changes to the configuration files to allow it.

I know I'm kind of "flailing around" here, but sometimes that's all you've got.  If nothing else, I would still very much suspect your hard drive.  You say you can hear it whirring...is that a constant whirring, or operation as normal?  Does the whirring sound a little strange, possibly like bearings going out?

If you can afford it, you might want to burn a disk image (or back up your critical data), save it to another location, and install a new hard drive.  If nothing else, a good experiment would be to do an installation to a flash drive (around 8 GB would do it, but 16 would be nice) and boot to that and see if it still freezes up.

That would tell you if the problem was hardware based or in the installation itself.  If it's hardware based, the problem will still happen; if not, then the problem is in the installation (or the hard drive itself).

---

### Post by warfacegod on 2010-06-12
A thought of my own that has spawned from -kg-'s "flailing about". Did you have a Manufacturer's video driver installed right before you Upgraded? They don't survive kernel updates and can occasionally reek havoc afterward. I can't imagine (yes I can, I'm just being modest) what sort of bad things might crop up from an OS upgrade compared to a simple kernel update.

I kind of like the monitor idea too, now that I think about it. Monitors (LCD's especially) can get very hot. Perhaps it's the display that's overheating not the computer itself.

---

