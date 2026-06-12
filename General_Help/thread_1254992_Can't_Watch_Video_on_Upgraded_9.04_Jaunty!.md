---
title: "Can't Watch Video on Upgraded 9.04 Jaunty!"
date: 2009-08-31
forum: General Help
---

### Post by jackrednur on 2009-08-31
[edit]  I just upgraded ubuntu to version 9.04 and I cannot watch video.  Granted, the files will open...but they will either be incredibly choppy and impossible to watch, or the audio will be messed up, or the picture won't even show but the audio will be fine, etc.  I've googled and searched the forums but cannot find out how to remedy this, any help would be greatly appreciated as I am a complete ubuntu noob and I really don't know how to do anything with this OS other than copy and paste commands into the terminal, or update things with synaptic package manager.

If this is pertinent info, I am running a dell dimension 4200 and I have a geforce 6200 graphics card that...well, I only upgraded because it was rebooting my system every now and then for no particular reason (maybe I didn't install the drivers correctly?) so I figured that upgrading to Jaunty 9.02 would remedy that situation.  Well, the computer STILL reboots whenever it pleases (usually when I have a lot of programs running)...and now I can't even get video to work!!  Audio works fine with mp3's, but neither video nor audio work when trying to watch a movie.  This includes youtube.  Any advice?

---

### Post by Bucky Ball on 2009-08-31
Go to System->Administration->Hardware Drivers. Is there an entry for an Nvidia driver? 

In synaptics, try searching for and installing:

ubuntu-restricted-modules

Also, System->Administration->Update Manager and make sure you machine is up to date.


ps: I think you mean 9.04 (jaunty Jackalope) rather than 9.02. :)

---

### Post by jackrednur on 2009-08-31
Thanks for the quick response.  But yah, been through this process before in the hardware drivers.  It has a list of three NVIDIA drivers, none of which have worked for me previously.  It recommends version 180, and I'm gonna go ahead and try to activate that now as I haven't tried it on the upgraded ubuntu 9.04 yet, BUT....if it's anything like before, I'll restart the system to a low-res safemode for whatever reason, and only be able to get things back to normal by deactivating the driver.

[Edit]  Well, the switch to that driver seemed to go off smoothly.  However, video is still choppy/erratic and not at all like it was before I upgraded.  Anyone have any ideas what the problem is?

---

### Post by mc4man on 2009-09-01
Maybe not your issue but anyway..
many people have found that when going from 8.04, 8.10 to 9.04 that their systems can no longer use the default and preferred video output Xv and instead have to use X11

To test
for the system setting  (gstreamer players

```
gstreamer-properties
```

Under the video tab change output to X Window System (No Xv)

For third party player change in the players preferences or settings or if using a cli use x11 (mplayer -vo x11 ect., ect.

---

### Post by jackrednur on 2009-09-01
Okay, well....I'm still having the same problem, but perhaps I should clarify.  It's the audio that's the problem.  Save for youtube, where I can hear the audio and can't see the video, every other movie file is having problems with the audio which I can't fix.  Crackling, popping noises along with the actual audio, it sounds a lot like what ZSNES audio sounds like when I try to run that program.  

Please help, video is basically all I use my computer for.

---

### Post by P4man on 2009-09-01
I think you should investigate that rebooting before doing anything else.
Does your log file show something useful or interesting ? (system > administration > log file viewer). Have a look at "messages" and perhaps post your dmesg.

Did you check your RAM for errors?

---

### Post by jackrednur on 2009-09-01
Hmm, as I said, ubuntu noob...never checked that before.  This is interesting, as my comp always restarts whenever it pleases for no discernible reason.  It's gotten worse with the upgrade to Jaunty 9.04.  Maybe that has something to do with the problem?


ubuntu kernel: [10746.262069] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Sep  1 12:35:48 ubuntu bonobo-activation-server (jackrednur-11025): could not associate with desktop session: Failed to connect to socket /tmp/dbus-XNQAK9Ewdo: Connection refused
Sep  1 12:35:52 ubuntu pulseaudio[11115]: pid.c: Stale PID file, overwriting.

---

### Post by QIII on 2009-09-01
You're saying the restart occurred in an older version as well?

Did you upgrade or do a fresh install of Jaunty?

---

### Post by jackrednur on 2009-09-01
I upgraded, and yah...the incessant restarting occurred before I upgraded as well.  I figured it had something to do with the graphic card drivers, as my computer never used to do this before I replaced the graphics card with a NVIDIA geforce 6200.

Someone recommended that the restarts would be taken care of by upgrading to the newer release of ubuntu and so I did, but now the audio in my video is messed up, and the restarts are more common than ever before.   :(

---

### Post by P4man on 2009-09-01
those logs you posted may be an indication indeed. For sure the pulseaudio error has something to do with your sound not working, or not working properly.

Can you post the full output of:

```
dmesg
```

and

```
lspci
```

---

### Post by jackrednur on 2009-09-01
I've included my dmesg (part 1 of two) in case anyone can find the errors which are forcing my computer to reboot occasionally for no reason, and why I can't watch videos without them being choppy or freezing, and with the audio making popping, erratic sounds.

---

### Post by jackrednur on 2009-09-01
And here's the dmesg part 2 and the lspci.  Thanks in advance to everyone who checks it out.

---

### Post by P4man on 2009-09-01
anyone else looking at that dmesg, the rather weird > "  30.291229] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   30.291232]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   30.291234]  you are certain that your <4>intel_rng: system has a functional
[   30.291235]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option."

that apparently relates to a dysfunctional hardware random generator, and that message can be safely ignored. 

The rest of the log looks fairly clean to me. 

The only other thing striking me is that you're using a relatively old kernel. 

for now, i would suggest you do a few things:
1) boot from the live CD and run the memory test overnight
2a) assuming you get no errors, try disabling your sound in the bios. see if that improves stability.
and/or
2b) Follow these instructions to fix pulseaudio:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
3) upgrade your kernel (and the rest of the system while you're at it).

---

### Post by jackrednur on 2009-09-01
I tested the memory, came out fine.....went through the pulseaudio instructions, nothing wrong there.  Here's another stupid question, but how can I upgrade my kernel?  I just installed Jaunty yesterday, and I did an upgrade earlier today...so I figured my kernel was upgraded along with that, but you're saying you can see it's old sooo......what code should I type to update that?  Thanks again for everything.

---

### Post by StuartN on 2009-09-01
> **jackrednur said:**
> I upgraded, and yah...the incessant restarting occurred before I upgraded as well.  I figured it had something to do with the graphic card drivers, as my computer never used to do this before I replaced the graphics card with an ATI geforce 6200.

I had a similar issue of "random" reboots which occasionally occurred immediately after a boot from cold and occasionally just out of the blue while working. My problem started after upgrading a CD-RW/DVD to DVD-RW drive and appears to have been due to exceeding the available output of the power supply. Since replacing the power supply it has never had a random reboot.

---

### Post by P4man on 2009-09-01
> **jackrednur said:**
> I tested the memory, came out fine.....went through the pulseaudio instructions, nothing wrong there.  Here's another stupid question, but how can I upgrade my kernel?  I just installed Jaunty yesterday, and I did an upgrade earlier today...so I figured my kernel was upgraded along with that, but you're saying you can see it's old sooo......what code should I type to update that?  Thanks again for everything.

You're running 2.6.22-16-generic according to the logs (you can check by typing "uname -a" in a terminal). 2.6.28-15-generic would be the current release I think. To update, just run update manager, it should list the new kernel(s) along with all other updates.

also see:
[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

---

### Post by jackrednur on 2009-09-01
Ahh yes, thank you.  Thing is, it's either load on this kernel or a previous kernel version, which doesn't register with my graphics card and causes me to go into "safe" mode.  It's weird, I have a list of kernels to boot from when I start my computer, but all of them are either the one you mentioned or prior releases, with none of the recent upgraded kernels (though I have and do upgrade them daily).  There's not even an option to boot into any other kernel, and maybe that right there is my problem....I'm running in an antiquated kernel.  

Any ideas on how to remedy this problem, as you've been most helpful so far?

---

### Post by Bucky Ball on 2009-09-02
> **StuartN said:**
> My problem started after upgrading a CD-RW/DVD to DVD-RW drive and appears to have been due to exceeding the available output of the power supply. Since replacing the power supply it has never had a random reboot.

The most sensible suggestion so far. This is almost definitely a hardware issue. Random restarts are never a good sign. I would check what power supply you are using (no doubt generic silver box) and its wattage and also stick your hand back there and check how hot your box is (particularly the power supply). Also, if you boot to BIOS, there should be a PC health section there which gives CPU and MB temperatures. Please find out what they are and post back.

Whilst the old graphics card was just tickling the PSU occasionally, inserting the new graphics card could well have pushed your power supply to the limit (which is why it's happening more often now). Graphics cards are notoriously power hungry (but have improved slightly recently) and this could well be the problem.

You say it was doing the random restarting before? A pretty sure sign the random reboots have nothing whatever to do with software issues. I'd liked to be proved wrong but I doubt I will be. Even though the memory test proved positive, it ain't gospel. Put one stick of RAM in slot one and run the machine for awhile and see if it still reboots. If it's stable, you have found your problem: One of the RAM sticks. You will find that if you go through them one by one in slot one, there will be one that the machine won't boot from (or will cause the crash).

Good luck with it. :)

(ps: tips on power supplies can be found at the link in my signature)

---

### Post by P4man on 2009-09-02
try this:
```

sudo apt-get install --reinstall linux-image-2.6.28-15-generic
```

That said, I wouldn't dismiss the suggestion of checking your powersupply. If you can check the 3.3, 5 and 12v voltages in the bios, if they are too low, then you got a likely cause.  (and even if they aren't it doesn't mean your PSU is good).

---

### Post by filip007 on 2009-09-02
Backup data to USB flash key and do fresh install

---

### Post by Bucky Ball on 2009-09-02
> **filip007 said:**
> Backup data to USB flash key and do fresh install

I do wish people would read threads properly. 

OP installed Jaunty yesterday. :confused:

---

