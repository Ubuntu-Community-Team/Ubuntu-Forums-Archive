---
title: "Ubuntu (Jaunty) goes to blank screen less than 10 minutes after logging in"
date: 2009-10-12
forum: General Help
---

### Post by d0ugal on 2009-10-12
After logging into Jaunty (9.04) everything seems to be going fine but after less than 10 minutes the screen goes blank and I'm unable to do anything. The system dual boots with Windows 7 and Windows 7 appears to have no problems.

The system was working fine for months and after being turned off over the weekend failed to start.

I have tried;

[LIST]
[*]Pressing ALT+CTRL+F1 after the blank screen doesn't work.
[*]Booting into the LiveCD - same problems
[*]Selecting different versions of the kernel in Grub
[*]Killing X when Ubuntu starts (so I'm only on the command prompt)
[/LIST]

Everything so far has the same problems except windows 7. If it were not for windows 7 I would have thought a hardware problem.

---

### Post by Giblet5 on 2009-10-12
It sounds like a hardware problem.

**Probably** overheating graphics card.

What happens when you start Windows and preview a 3D screensaver for 15 minutes?

You might also want to run memtest86 for a couple of hours. There should be no errors at all.

You can also grab "prime95" for Windows and run its burn-in test (default settings). It should be able to run for an hour w/o any errors at all.

A failure in memtest86 indicates either dodgy memory timing, overheating, or defective RAM.

A failure in prime95 indicates either dodgy CPU timing/voltages, or a defective motherboard or CPU.

A failure in BOTH tests indicates a probable weak power supply.

---

### Post by d0ugal on 2009-10-12
> **Giblet5 said:**
> 
What happens when you start Windows and preview a 3D screensaver for 15 minutes?
Since I mostly have Windows installed to play the odd game or two I had oportunity to test this easily. I ran the video stress test in counterstrike:Source and it all went fine. I then loaded up Team Fortress 2 and it played for about 30 mins no problems. 

> **Giblet5 said:**
> 
You might also want to run memtest86 for a couple of hours. There should be no errors at all.

This surprised me. I ran memtest86 as launched from Grub and all was going well - I took my eyes of for a minute and when I came back the screen was blank - 'the problem' had occured. So this suggests a memory problem but I'm not sure why windows isn't having it. I do have 6 gig of ram, so could it just be by chance windows isn't hitting a bad sector?


> **Giblet5 said:**
> 
You can also grab "prime95" for Windows and run its burn-in test (default settings). It should be able to run for an hour w/o any errors at all.

I'm running this at the moment. Although, I couldn't see 'burn-in' so I'm running the 'blend' 'torture test' which 'tests some of everything, lots of RAM tested' - it only seems to be using up to 1.5 gb of ram though (but I've no idea if its testing all of it or not.)

No problems so far. Will update in about 45 mins.

---

### Post by d0ugal on 2009-10-12
Something just occurred to me.

Ubuntu is installed on hd0 and windows hd1 - so they are on separate drives. This could suggest something funky with the HD however it doesn't explain why I have problems with the liveCD

---

### Post by Giblet5 on 2009-10-12
Memtest86 and linux won't use your hardware the same way that Windows does, but CounterStrike will beat the tar out of a PC for certain...

Windows won't crash just because your PC fails to add 2+2 correctly. Linux usually will. Memtest86 (a DOS program) will.

Does your BIOS setup screen provide a "Monitoring" option where you can see temps and voltages? If not, do you have a multimeter and a steady hand?

Your Vcore and +5VDC are pretty critical.

If something is causing the +5 to drop below 4.8V, that will cause trouble.

Do you have a dual GFX card for CS? SLI? Crossfire? Did you buy the inexpensive "700 watt" power supply?

---

### Post by Giblet5 on 2009-10-12
> **d0ugal said:**
> Something just occurred to me.

Ubuntu is installed on hd0 and windows hd1 - so they are on separate drives. This could suggest something funky with the HD however it doesn't explain why I have problems with the liveCD

It wouldn't affect memtest86 either.

That's not (likely) your problem unless the ATA cables have been chewed on by mice, but I'd expect Windows to have a big problem with that too (in Event Viewer/System).

---

### Post by d0ugal on 2009-10-12
> **Giblet5 said:**
>  Does your BIOS setup screen provide a "Monitoring" option where you can see temps and voltages? If not, do you have a multimeter and a steady hand?
Afraid not. I don't have anything handy to test this.

> **Giblet5 said:**
> 
Do you have a dual GFX card for CS? SLI? Crossfire? Did you buy the inexpensive "700 watt" power supply?

No to dual GFX cards. It's actually a completely stock Dell machine, almost 4 months old. Here is the specs from the order sheet (with some of the cruft removed for readability).
[INDENT]Base : Studio XPS Intel Core i7 Processor 920 (2.66GHz, 8MB cache, 4.8GT/sec)
Memory : 6144MB (6x1024) 1067MHz DDR3 Tri Channel
Media Card Reader : 19-in-1 Media Card Reader
Hard Drive : 1TB (2x500GB) Serial ATA Raid 0 "Stripe" (7200RPM) Dual HDD
Optical Software : ROXIO Software for Vista - Creator / MYDVD 10.2 (software install, no media)
Optical Drive : 16X DVD+/-RW Drive
Display : Not Included
Graphics : 512 MB ATI Radeon HD 4670 Graphics Card
Audio Integrated HDA 7.1 Dolby Digital capability
[/INDENT]Ironically I decided not to build the system myself for the first time in years so I wouldn't have to worry about hardware problems. The issue, Dell don't specifically support Linux on this machine. So I don't suppose if I got to them and say it works in windows but not linux they will help me very much.

---

### Post by Giblet5 on 2009-10-12
Wow. Nice rig.

Try this:

Boot to linux and log in.
Wait until it does this thing it does.
Reboot to Linux and look though the last /var/log/syslog file that covers the problem.

Any clues? Errors?

---

### Post by d0ugal on 2009-10-12
> **Giblet5 said:**
> Wow. Nice rig.

Thanks. I've been very happy with it, until today.

> **Giblet5 said:**
> 
Boot to linux and log in.
Wait until it does this thing it does.
Reboot to Linux and look though the last /var/log/syslog file that covers the problem.

Any clues? Errors?

Sitting waiting for it to break is quite frustrating, it took a bit longer that time and interestingly sound continued for about 10 seconds after the screen went.

Nothing jumping out at me in the log. The only warning I can see by searching the file is;

[INDENT]'Couldn't read /proc/3292/environ: Failed to open file '/proc/3292/environ': No such file or directory'
[/INDENT]This happens at the end of the boot though so I guess its not related.

If it would help I could paste some of the log file?

p.s. thanks very much for the help so far.

---

### Post by d0ugal on 2009-10-12
Since I've got six different sticks of ram I was thinking about removing three of them and seeing how it goes and then swapping and trying out the other three.

Might give me a clue if its a ram problem. Since memtest failed I imagine this is the most likely, although it didn't fail in a conventional way. More like a power pull.

Maybe its time to phone dell and see what they can tell me.

---

### Post by d0ugal on 2009-10-12
Aha. This is interesting.

I tried the 32bit LiveCD just out of interest. It had the same problem but when I pushed the power button to turn it off I got the system beep. So I didn't hold it in.

Shortly after it popped the CD out and then I knew 'press enter to shutdown' - or whatever it says. So I pressed enter and it went off.

Could this then mean it is a graphics card problem? I'm going to play around and see if I can do a shutdown from inside ubuntu itself.

*edit* (as i should really stop replying to myself)

It is indeed just the output thats dead as far as I can tell. I just booted into ubuntu and waiting for it to go belly up and pushing the power button caused the system beep - presumably triggering a shutdown, although its not making much progress.

Is there a way to get memtest to save the output somewhere? I guess not but I'd kinda like to know if its still running and I just can't see it.

So, if this is a possible answer. Why would my computer be struggling to do ubuntu and even memtest but the gfx card plays well with a much more demanding 3D game.

---

### Post by Giblet5 on 2009-10-12
The Dell folks will be very resistant after you say "Ubuntu" or "Linux".

I would tell them "The computer crashes when running the MSDOS program, memtest86." You can easily put memtest86 on a DOS-boot USB stick and prove that it's not an Ubuntu thing, if you have scads of time and energy; however, I guess you already know that won't make any difference.

Testing 3G of 6 is worth a try, but make sure you pull the correct 3 sticks... Triple-channel and all that.

---

### Post by d0ugal on 2009-10-12
So just to follow up and put a close to this thread.

I spoke to dell for about 4 hours!!

I managed to avoid telling them i had installed ubuntu or windows 7 - just to keep them happy. 

For about 1.5 hours I had to keep telling them it wasn't a software problem. Since the machine wasn't any use to me and all my data is stored on the main server i done a recovery with the dell cd to please them... so they couldn't claim it was software.

Anyway, just to make it more fun the computer turned off mid windows install! So, that got me through to the hardware department. After another 1.5 hours they finally gave up when i told them py graphics card heat sink was too hot for me to even touch.

They are collecting my computer in two days and returning it within 7 working days.

Great.

So I suppose in summary, windows ignored the graphics card when it was too hot and ubuntu went belly up. Thats if that is the problem anyway.

---

