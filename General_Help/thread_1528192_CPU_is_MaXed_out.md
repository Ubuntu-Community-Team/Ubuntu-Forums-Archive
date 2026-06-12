---
title: "CPU is MaXed out"
date: 2010-07-10
forum: General Help
---

### Post by complience on 2010-07-10
I installed ubuntu 9.10 desktop 32bit on a new build - started getting random application crashes across the board.

Decided to try 10.04 64bit instead - although there was some improvement im still getting applications randomly crashing and flash websites seem to crash my browsers.

Also 1 out of every 10 restarts I loose either sound or bluetooth or networking. The system just seems to decide it can't detect them.

Restart and they appear again.

Looking at system monitor the only possible issue I can identify is a large cpu load. Check out my screen shot below - does that look normal for a system not under any use?

I

---

### Post by quequotion on 2010-07-10
nothing looks abnormal in that screenshot... your cpu has a 93.18% *idle*, meaning more than 90 percent of it's cycles are used to count sheep. Almost nothing is using your CPU.

64bit and flash are "in a relationship, and it's complicated"

You should find the 64bit flash plugin from Adobe and put it in ```
~/.mozilla/plugins
``` make sure to remove any other versions of the flash plugin (installed by synaptic/apt or by hand)

This plugin was recalled due to a security flaw (basically every version of flash has had serious security flaws.. it isn't news). If you can't find the file anywhere else, there's a ppa out there somewhere. Adobe has said they will release an updated version, eventually.

As for your random crashes.. Is there no pattern at all? For example: all programs that make sound crash OR gtk programs crash OR programs that use the internet or network crash?

can you get a syslog?

1. Panel menu-> System -> Administration -> Log File Viewer

2. copy & paste all of "syslog"


Also, are you sure you aren't overheating? That could cause totally random crashes/freezes/shutdowns/fires.

---

### Post by complience on 2010-07-10
Its certainly NOT just flash that is crashing out, ALL applications are unreliable. 

And i dont understand why the audio is just disappearing

or the bluetooth now and again.. 

What part of the logs should i look in after a crash?

im not overheating

CPU = 54c
MB = 40c


Here are my systems specs


AMD Phenom II X4 955 Black Edition Socket AM3 3.2 GHz 8MB L3 Cache  Processor

ASUS M4A79T Deluxe 790FX Socket AM3 DDR3 8 channel audio ATX Motherboard
 
OCZ 4GB (2x2GB) DDR3 1333MHz/PC3-10666 Gold i5 Memory Kit 1.65V CL9(9-9-9-20)

---

### Post by complience on 2010-07-12
Another problem im noticing is I start watching a DIVX movie in Totem Movie Player.

It will start playing as expected, but after 10 - 15 minutes the playback starts to slow down until unwatchable.

suggests a memory leak

If i watch the same movie in VLC it seems to run okay without a problem.

---

### Post by complience on 2010-07-14
Okay so the previous screenshot showed the system stats when idle, this screenshot shows whats happening when its active (VLC is playing a movie)

The memory is completely maxing out.. I dont think its a VLC specific issue, something is causing me to loose memory in all applications.

---

### Post by quequotion on 2010-07-15
> **complience said:**
> The memory is completely maxing out..
Does the memory max out *only* when watching video?

That's definitely odd... I've tried very hard to max out memory usage before, and failed.

If it happens while watching video with players as different as those, it could be a driver problem. What kind of graphics card do you have? are you using open source or proprietary drivers?

How about your totem and vlc configuration? they should basically work out of the box, but you can sometimes get a lot better output by tinkering with some options.

In the logs I wondered if you might find repetitive messages about some kind of failure: ie. pulseaudio says it can't **x** 100 times and crashes, or the kernel can't find resource **y** so it unloads some module or kills a daemon. If you post it, someone with expertise might find something as well.

Also, are you running Mythbuntu?

---

### Post by complience on 2010-07-16
Interesting that you bring up pulseaudio.. i suspect it might be responsible.. because 1 out every 10 times I restart the box my motherboards sounddriver isnt detected and I have no audio.

If i restart, suddenly its okay..

The memory problem is most noticeable when watching a video on totem. VLC manages but I get the feeling - only just.

But I have problems with other applications crashing
Chrome, Firefox, Attitude 

Skype seems to have problems. Sound Play back is stuttered somtimes.

I am not running mythbuntu - I do have Myth installed but on ubuntu 10.04 64bit (it used to randomly crash)

My graphic card is an nvidia using the priority drivers (seemed to help playback)

---

