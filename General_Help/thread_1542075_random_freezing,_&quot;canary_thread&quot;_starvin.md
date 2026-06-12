---
title: "random freezing, &quot;canary thread&quot; starving"
date: 2010-07-30
forum: General Help
---

### Post by AnWe on 2010-07-30
Hi!
I've got a problem were my laptop freezes from time to time. I can't really tell what causes the freezes, but every time i get a message like this in syslog:
```

Jul 30 16:05:04 localhost rtkit-daemon[1439]: The canary thread is apparently starving. Taking action.
Jul 30 16:05:04 localhost rtkit-daemon[1439]: Demoting known real-time threads.
Jul 30 16:05:04 localhost rtkit-daemon[1439]: Demoted 0 threads.

```Right now i'm running a realtime kernel (2.6.33-26-realtime, from [https://launchpad.net/~abogani/+archive/ppa/]("https://launchpad.net/%7Eabogani/+archive/ppa/")) but i think i have the same problem with the "generic" from lucid-backports (will confirm later today, it takes a while to test). I need the realtime for audio work, but it's useless if it's going to freeze randomly when recording.

Does anyone have similar problems? I tried googling and searching the forums, but came up with next to nothing. 

Is there any way to determine what *causes* the canary thread to starve? The log message is nearly useless. I suppose the 'starving' means that the thread is not getting access to the cpu in a timely manner and therefore indicates something is hogging it?

I've had a look in top and seem to get high load averages, but not high cpu-load. Theres not much %wa either, so disk access shouldn't be an issue. I did find some zombied npviewer.bin processess (flash if i remember correctly?), will investigate these first...

PS, I'm not running anything realtime at the times i get these errors, just some casual web browsing/e-mail.
PPS: I couldn't kill the zombies, even with -9, but they dissapeared when i closed firefox, as expected. Not sure these are what causes the freezing though. I'm using firefox 3.6.8 btw.

/Andreas

---

### Post by AnWe on 2010-07-30
Seems like firefox may be the culprit. I'm running 64-bit ubuntu and using the beta flash 10 r32 (no longer available apparantly). This has been working fine before, but i think it might have something to do with the new plugin-container thingy of recent firefox versions. I've now noticed CPU spiking (1000%!?) in top on this process, so I think i'll try a downgrade and see if things work better.

PS not going back to the 32-bit flash if i can help it, that one was even less reliable than my current situation.
/Andreas

---

### Post by AnWe on 2010-08-04
Update:
It is neither flash or firefox that *causes* the problem, they just load down the system to make the problem more apparent. I tried watching a movie last night, and got reoccurring freezes. Everytime i get a freeze, i can "unfreeze" just by making an interrupt (e.g. moving the mouse, pressing the keyboard).

I've tried a few different kernels since my last post:
2.6.32-24-generic
2.6.32-24-lowlatency
2.6.32-24-preempt
2.6.33-26-realtime

The generic one seems to be least bad, the freezes are further apart on that one, but they still occur. The other ones are more adapted for lowlatency audio work and for some reason exaggerate the problem, making the system barely usable.

I suspected the audio driver might be at fault (hda-intel) so i fiddled around with the module settings. Adding tsched=0 to pulseaudio "module-udev-detect" makes the audio skip very fast, so that was completely unusable. 

Making the prealloc buffer larger (echo 1024 > /proc/asound/card0/pcm0p/sub0/prealloc, default is 64) does not to have any noticable impact.
I changed the "model" parameter to "clevo-m720" (the model of my laptop) in alsa-base.conf, that didn't seem to make much of a difference. I tried position-fix=1, no difference.

I tried linux-alsa-driver-modules-2.6.32-24-generic from the ubuntu-audio-dev ppa but no luck.

My next step is to go back to an older kernel (i'll try 2.6.32.21 first, then back further if possible) with vanilla ubuntu alsa-driver and have a look at the X graphics driver. 

To me this seems like an IRQ-issue or some kind of race-condition that i break when triggering an interrupt. The graphics card (i915), wlan (iwlagn), audio (hda-intel) and eth0 are all on MSI-edge interrupts though, so an IRQ-conflict seems unlikely.

I don't know how to proceed troubleshooting much further. Any help or hints would be greatly appreciated.

/Andreas

---

### Post by AnWe on 2010-08-05
Ok another update (not that anyone seems very interested):
I tried a more recent kernel (2.6.35.13-generic) but still have the same issues.
I tried an older kernel (2.6.32-21-generic), no joy.
I tried shutting of wlan (via killswitch), no difference

To describe the symptoms more accurately, this is what happens:
The X-display is stuck (clock does not update)
Audio (if any is playing) continues to play, but loops the same fragment over and over.
user input (mouse, keybd) unfreezes the system.
Video seems to either freeze completely or stop and then continue after a short while (depends on which kernel is used as far as i can tell).

Sometimes, but not always, this is accompanied by a "canary thread" or "pulseaudio[xxxx]: ratelimit.c: x events suppressed" entry in syslog. I now believe this to be a symptom and not the actual cause of the problem. Rarely i have also seen "alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large" messages with a following snd_pcm_dump(), but that seems related to only certain kernel versions.

After the freeze is cleared, top shows unreasonable load averages. The longer i let the system freeze, the higher the load average gets. 

The only luck i've had until now is using an older realtime kernel (2.6.31-12-realtime), which does not seem to "freeze" the same way. I do still get glitches and stutters in eg. video and audio, but no complete hangs. Haven't tested this extensively, it may just be a matter of time.

Edit: I Jinxed it, got a freeze with that one too now.

Will try an older kernel from Karmic next, and then perhaps from Maverick if nothing else helps. The symptoms change very much depending on which kernel i use, but none so far seem trouble free.

I'm a little curious if i could SSH into the system while in a freeze, will investigate this too. 

PS I've also tried getting xserver-xorg and related packages from the x-swat ppa, but seem to have problems seeing the packages in aptitude/apt. The correct key is installed and shows with an "apt-key list".

/Andreas who will soon abandon ubuntu for something more stable (Debian comes to mind :))

---

### Post by varunendra on 2010-08-05
Hi,
The details of your whole problem are absolutely above my head. But since no one else has jumped in for six days despite continuous inputs from you, and you are about to "abandon Ubuntu" now, I think it's not a bad idea to through in a wild guess.

Contrary to your initial guess:> **AnWe said:**
> I suppose the 'starving' means that the thread is not getting access to the cpu in a timely manner and therefore indicates something is hogging it?isn't it possible that 'starving' here means that the cpu is not getting input for further processing? Hence the incomplete loops?
But honestly, I've no idea myself that what I'm talking about, so I'll leave it to you for any consideration.
However I'd suspect RAM, HDD (why not? :)) or the channels through which the data flows (i.e., motherboard) - all hardware!!

> **AnWe said:**
> /Andreas who will soon abandon ubuntu for something more stable (Debian comes to mind :))
Sorry for not being very helpful, but if I were you, I'd have had first tried the whole setup on a different laptop or pc. But it's me! Different people, different approach,.... all is well if end is well.

Best of luck to you!

And oh, why don't you try replacing the RAM (or just cleaning - reinstalling it) if possible? As I said- just a wild guess before you leave us!! :(

---

### Post by AnWe on 2010-08-06
Hi Varunendra, thanks for the reply!

The last comment about abandoning ubuntu was (at least partially) a joke :).
I might try a Debian (or other dist) live CD just to troubleshoot, but switching dists would be too much pain right now. I've customized the system quite a bit to get jack2/ffado/realtime/32-bit chroot for VST and too many other things i can't remember right now.

I did run a quick memtest which didn't reveal any problems. I will run a longer one when i get an opportunity, but i don't think it's memory related. The HDD has passed all fsck's this far, and doesn't have any smart-errors, but i guess the sata-interface could be screwing up. Although, i think i would likely get other log-messages and corruption then, i've seen that kind of stuff before on other systems. 

I can't really test on another laptop, since i'm backpacking in australia. To be really useful, the tests would have to be on similar hardware anyway, since i suspect one of the hardware drivers to be at fault. I've googled the issue quite a lot, and there seems to be similar issues with "ratelimit.c", "canary thread" and the alsa crash, but i haven't found anything conclusive. 

Might be dodgy hardware though, i'm with you there. I have a slight suspicion about the cooling of the chipset, I've opened the laptop before and the cooling there looked quite flimsy. However, I would not expect a chipset cooling issue to change behaviour so much between different flavours of the same kernel. Might fix it anyway, just for peace of mind.

Too bad there doesn't seem to be a temp sensor for the chipset present. Using "sensors" I've got two readings for the cores and one "virtual" device, that i'm not sure where it comes from. In the gnome monitoring applet the only one that shows (except the harddrive) seems to be the "virtual" one, its under ACPI THRM.
This is a Clevo M72R laptop if anyone has any suggestions for fixing the cooling or sensor config.

Oh well, i'll continue this thread until I make some progess, might help some other poor bastard in the same seat (that's really the point of these forums anyway). Going back to a karmic kernel next, i have a faint memory of things running really well about a half a year ago.

Also think i got the x-swat ppa working now, will try updating some of the xorg-stuff.


/Andreas

---

### Post by AnWe on 2010-08-06
Now trying 2.6.31-14-generic from Karmic, and Oh joy! It seems to work flawlessly. No glitches in audio. One log message about ALSA being woken up with nothing to write, but as long as sound is this good i don't care.

I might be too quick though, i've only tried for a few minutes.  Under load audio is playing without issues though (transfering 5G data via USB, lots of interrupts). 

Will try a minimal environment with just rythmbox and then some video next, but things seem much better. The system seems much snappier on the whole too, so i feel this was the trick. 

PS After reading the LKML, there seems to be alot of sound-changes in 2.6.36 so i will try that once its released.

/Andreas

---

### Post by AnWe on 2010-08-07
Just a correction: the problem is not completely gone with 2.6.31, but it is on a level where it is not completely frustrating. I can now watch an entire movie and not get more than a handful of barely noticable glitches. Before i had stutters and glitches every few minutes. 

I don't know how this will affect recording audio, haven't tried yet, but i can't use the generic kernel for that anyway. I think it will be ok, since i'm not using hda-intel at all for that, i have a saffire LE hooked up to ffado/jack2. Last time i tried i didn't get any artefacts, even though this was on a later kernel.

/Andreas

---

### Post by varunendra on 2010-08-07
Hmm.. seems like it is not yet time to congratulate you....

However, just to rule out the possibility of a hardware fault, why don't you try an entirely different OS.

I believe all the linux distros use different versions of the same kernel- 'Linux', so why not try something other than linux!

Yes, I remember you've done a lot of customization & stuff, but just for testing load-response, I think you should try that (If you already haven't of-course).

Well I personally don't have any suggestions for that other than windows (non-free, no LiveCD, virus-prone, ....etc....etc...., but rather stable for multimedia experience, and it'd be just for testing! Plus it is easy to find free cpu temp tools for it!).

But if it has to be a Linux distro (freedom of testing via LiveCD :D) then I would recommend (based on search & description, not experience) either [dyne:bolic]("http://www.dynebolic.org/") or [AVLinux]("http://www.bandshed.net/AVLinux.html"). Both of these are said to have powerful audio/video tools in live environment. You can choose from some other ones [here]("http://cinelerra.org/getting_cinelerra.php").

---

### Post by calin ardelean on 2010-09-03
I have the same problem with my fresh Lucid installation on a HP Compaq 6005 Pro SFF. Same hangs which go away by mouse/kbd, gaps when playing mp3 or xvid encoded videos (yet web videos work fine).

The system is dual-boot, there is an Windows 7 installed from HP CDs which works fine.

This is what I did:

1. I changed from pulse to ALSA sound in gstreamer-properties, which reduces gaps somewhat.

2. I thought it is the Logitech wireless/usb mouse/kb so I switched to PS2 ones with no change.

3. I thought it is the opensource ATI drivers (videocard: integrated ATI Radeon HD 4200), so I installed the proprietary Catalyst 10.8, also no change (except glxgears tests improve from around 5000 frames/5 secs to around 10000).

Besides the canary thread starvation errors, I noticed in the kern.log these ACPI errors (on boot):
```
Sep  3 14:30:01 calin-hp kernel: [    0.257270] ACPI: EC: Look up EC in DSDT
Sep  3 14:30:01 calin-hp kernel: [    0.261251] ACPI: Interpreter enabled
Sep  3 14:30:01 calin-hp kernel: [    0.261258] ACPI: (supports S0 S3 S4 S5)
Sep  3 14:30:01 calin-hp kernel: [    0.261272] ACPI: Using IOAPIC for interrupt routing
Sep  3 14:30:01 calin-hp kernel: [    0.263852] ACPI: No dock devices found.
Sep  3 14:30:01 calin-hp kernel: [    0.264152] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep  3 14:30:01 calin-hp kernel: [    0.264157] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015588), AE_ALREADY_EXISTS
Sep  3 14:30:01 calin-hp kernel: [    0.264162] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Sep  3 14:30:01 calin-hp kernel: [    0.264176] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Sep  3 14:30:01 calin-hp kernel: [    0.264180] ACPI: PCI Root Bridge [PCI0] (0000:00)
```

followed shortly by

```

Sep  3 14:30:01 calin-hp kernel: [    0.265539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  3 14:30:01 calin-hp kernel: [    0.265652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IGFX._PRT]
Sep  3 14:30:01 calin-hp kernel: [    0.265689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX3._PRT]
Sep  3 14:30:01 calin-hp kernel: [    0.265734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
Sep  3 14:30:01 calin-hp kernel: [    0.265840] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep  3 14:30:01 calin-hp kernel: [    0.265844] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015588), AE_ALREADY_EXISTS
Sep  3 14:30:01 calin-hp kernel: [    0.265858] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Sep  3 14:30:01 calin-hp kernel: [    0.280210] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280270] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280329] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280387] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280449] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280507] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280566] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Sep  3 14:30:01 calin-hp kernel: [    0.280624] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.

```

Now I will try to disable ACPI from BIOS or something, will keep this thread updated.

---

### Post by calin ardelean on 2010-09-03
This happens over and over again:
```

Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: The canary thread is apparently starving. Taking action.
Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: Demoting known real-time threads.
Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: Successfully demoted thread 1361 of process 1332 (n/a).
Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: Successfully demoted thread 1360 of process 1332 (n/a).
Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: Successfully demoted thread 1332 of process 1332 (n/a).
Sep  3 15:02:13 calin-hp rtkit-daemon[1334]: Demoted 3 threads.

```

NOTE: the demoted 1332 process is the pulseaudio process.

---

### Post by calin ardelean on 2010-09-03
Ok, so I did as I said: goto BIOS, changed ACPI power save options from "Extended" to "Normal" (those were the only options), and ... problem solved.

Sound is ok, although there still seem to be some small short gaps in the interface (the clock's seconds sometimes skip 1 second, strange), videos are acceptable (still not as smooth as in windoze but ok).

ACPI errors still appear at boot time and "pulseaudio[1306]: ratelimit.c: 3 events suppressed" still appear once in a while, but no more thread starvation and screen freeze.

I will try to update BIOS from HP site.

---

### Post by calin ardelean on 2010-09-03
So this was for sure a BIOS problem. After BIOS update to v1.10 07/13/2010 problem was solved and I could put power save option back to "Extended".

Now all it remains for me to solve is the xorg/fglrx memory leak problem (unrelated).

I hope this info helps somebody.

---

### Post by varunendra on 2010-09-03
> **calin ardelean said:**
> So this was for sure a BIOS problem. After BIOS update to v1.10 07/13/2010 problem was solved and I could put power save option back to "Extended".

Ahh.... finally someone at least ! Congrats for victory in the long, exciting, **single-player** match ! :D

> **calin ardelean said:**
> I hope this info helps somebody.
I hope it helps AnWe !

I'm gonna keep this for reference.

Thanks for the contribution Calin.

---

### Post by calin ardelean on 2010-09-03
Sorry, the BIOS update DIN NOT solve the problem. At a subsequent reboot it came back... So I had to revert to "Normal" power option in BIOS to fix it, as stated earlier. Damn this single player game.

---

### Post by varunendra on 2010-09-03
> **calin ardelean said:**
> Sorry, the BIOS update DIN NOT solve the problem. At a subsequent reboot it came back... So I had to revert to "Normal" power option in BIOS to fix it, as stated earlier. Damn this single player game.

Thanx for this contribution too! :lol:

At least we know now that earlier **victory** was fake, it is yet to come.

---

### Post by nalcomis on 2010-10-17
I am experiencing the exact same thing while streaming video to my popcorn hour media player.  Very frustrating.  It appears to have started after an automatic Ubuntu update 6 months or so back...  I haven't been able to track down the exact upgrade that started the problem.  Has your bios fix still been working for you?

> **calin ardelean said:**
> Sorry, the BIOS update DIN NOT solve the problem. At a subsequent reboot it came back... So I had to revert to "Normal" power option in BIOS to fix it, as stated earlier. Damn this single player game.

---

### Post by calin ardelean on 2010-10-17
> **nalcomis said:**
> I am experiencing the exact same thing while streaming video to my popcorn hour media player.  Very frustrating.  It appears to have started after an automatic Ubuntu update 6 months or so back...  I haven't been able to track down the exact upgrade that started the problem.  Has your bios fix still been working for you?

The BIOS update did not solve the problem, but changing the ACPI power save option from "Extended" to "Normal" (in BIOS). I think the problem is with the Linux kernel, since Windows 7 work ok, with "Extended" on. You should also try to disable BIOS power save, and tell us if it worked.

---

