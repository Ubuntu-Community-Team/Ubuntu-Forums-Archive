---
title: "Audio is moving too fast"
date: 2010-10-10
forum: General Help
---

### Post by sparks40 on 2010-10-10
My install of 10.10 went fine with the exception of Audio. If I attempt to use audio with the Rythmbox application or through Adobe Flash (in firefox), it sounds like an old fashioned 33 1/3 rpm phonograph record playing at 45 rpms. This problem has been around for a while and I had hoped that it would be cleaned up by now.

I'm running an AMD 64 processor (in 32 bit mode) and my audio card is a "Sound Blaster Live Value" (EMU10k1X). My on-board sound card is turned off in the bios. It works beautifully under Ubuntu 10.04 and FC13 with Pulse Audio.

Originally I thought that it might be a problem with Rythmbox which is now at v 0.13.1, a later version then I have been using in 10.04. However, with the Rhythmbox application off, I still get the same effect when trying to use audio in firefox. I also noticed that my cpu utilization climbs to about 80% when Rhythmbox is on.

Any help would be appreciated.

TNX

---

### Post by sstruhar on 2010-10-11
I have the exact same issue and sent a problem report.  I believe the sample rate is being incorrectly reported/calculated.

---

### Post by sparks40 on 2010-10-11
Thanks for your response. 

I was beginning to think that I was the only Ubuntu 10.10 user in the world experiencing this problem. 

Interestingly enough, I got the same results from the latest beta release of Fedora 14, which leads me to believe that it's a system/kernel related problem. I even tried changing my sound card to a newer Sound Blaster model, as well as deleting the stock Rhythmbox application and reinstalling it.... and still got the same results. 

I'm amazed that no one else has commented on this problem. Although I'm sorry to hear that you are also having trouble with your system, it does confirm that we are not alone! Lets hope that it's an easy fix, as I am lost without audio.

---

### Post by tawfiqh on 2010-10-11
My sound is also playing way too fast. This happens with local audio files, youtube (flash) and streaming WMVs. Also running 10.10 Maverick Meerkat

---

### Post by sparks40 on 2010-10-11
Did you try anything to correct the situation, (i.e. trying a new audio card, reinstalling Rhythmbox, etc.)?

What sound card and cpu are you using, (Intel or AMD)???

---

### Post by coprolites on 2010-10-12
Hey Sparks40,
I also have the exact same problem and coincidently (or not?) the exact same sound card (Sound Blaster Live! Value - EMU10k1X).
Another thing I noticed is all videos are playing fast as well - I've tried .avi's and youtube.

I hope someone can help us out!

---

### Post by ersin2k on 2010-10-12
I have same issue.

I have SB Live! value 5.1
and sounds are creepy, and on movies they are faster than images.

Intel Dual Core CPU+ubuntu 10.10 and 3 GB Ram

I installed both of general and PAE kernel. That doesnt matter.

it seems a generally issue on kernel :S

---

### Post by disco_stew on 2010-10-13
Exact same problem here. Audio (and video) plays too fast regardless of what application is used and my system becomes unresponsive. Running top in a terminal shows that pulseaudio is using 100% CPU. I'm running Maverick AMD64 with a SB Live! Value (EMU10k1X) just like the OP.

Interestingly, this issue does not occur if I boot to the 2.6.32 kernel that was left-over during the upgrade from Lucid. I think you may be on to something when you suspected it was a kernel related issue.

Has anyone found a bug report related to this? If not we should open one.

---

### Post by sparks40 on 2010-10-13
Thanks for the reply. I took a quick look at the bug reports this morning and didn't see anything relating to this issue. I am a bit puzzled... if it is a kernel problem why are there so few reports concerning this obvious bug? It would seem that the other 99.999% of the ubuntu population isn't experiencing what we are experiencing. I've been looking for system similarities but can't seem to find one.

I have not filed a report to date. By the way, everything works fine under 10.04. I am using an AMD64 (in 32 bit mode) with 2 gigs of ram and an Asus M2N-MX motherboard.

---

### Post by happyhamster on 2010-10-13
I could be way off here, but is EMU10k1X the correct module for the card? Perhaps it should be EMU10k1 (without the trailing "X"). Could be that the newer kernel is loading the wrong module.

From Maverick's ALSA-configuration.txt file :
```

  Module snd-emu10k1
  ------------------

    Module for EMU10K1/EMU10k2 based PCI sound cards.
			* Sound Blaster Live!
			* Sound Blaster PCI 512
			* Emu APS (partially supported)
			* Sound Blaster Audigy

    extin   - bitmap of available external inputs for FX8010 (see bellow)
    extout  - bitmap of available external outputs for FX8010 (see bellow)
    seq_ports - allocated sequencer ports (4 by default)
    max_synth_voices - limit of voices used for wavetable (64 by default)
    max_buffer_size  - specifies the maximum size of wavetable/pcm buffers
                       given in MB unit.  Default value is 128.
    enable_ir - enable IR

    This module supports multiple cards and autoprobe.

    Input & Output configurations 			[extin/extout]
	* Creative Card wo/Digital out			[0x0003/0x1f03]
	* Creative Card w/Digital out			[0x0003/0x1f0f]
	* Creative Card w/Digital CD in			[0x000f/0x1f0f]
	* Creative Card wo/Digital out + LiveDrive	[0x3fc3/0x1fc3]
	* Creative Card w/Digital out + LiveDrive	[0x3fc3/0x1fcf]
	* Creative Card w/Digital CD in + LiveDrive	[0x3fcf/0x1fcf]
	* Creative Card wo/Digital out + Digital I/O 2  [0x0fc3/0x1f0f]
	* Creative Card w/Digital out + Digital I/O 2	[0x0fc3/0x1f0f]
	* Creative Card w/Digital CD in + Digital I/O 2	[0x0fcf/0x1f0f]
        * Creative Card 5.1/w Digital out + LiveDrive	[0x3fc3/0x1fff]
	* Creative Card 5.1 (c) 2003			[0x3fc3/0x7cff]
        * Creative Card all ins and outs		[0x3fff/0x7fff]
    
    The power-management is supported.

  Module snd-emu10k1x
  -------------------

    Module for Creative Emu10k1X (SB Live Dell OEM version)

    This module supports multiple cards.

```
Doesn't look like a lot of cards use snd-emu10k1x. 

@disco_stew: a good test would be to boot the 2.6.32 kernel and see which module is loaded for the card (in a terminal: lsmod | grep emu -i). Good luck.

---

### Post by sparks40 on 2010-10-13
Sounds to me like you may have hit on a potential solution to the problem. 

How do I remove the existing driver and replace it with a non-X varient? Should I black-list the "X" varient?

I assume that the modprobe command will be required but I have never used it before. Any suggestions on how to go about it?

TNX for taking the time to assist, I appreciate it.

---

### Post by happyhamster on 2010-10-13
> **sparks40 said:**
> Sounds to me like you may have hit on a potential solution to the problem.
Mind you, I'm not sure if choosing another module will solve anything. It's possible that the same thing that causes the wrong* module to load will cause the hardware to not even recognize/talk to the correct one.

*And we still don't know if snd-emu10k1x is the wrong module. Another way of testing this is booting from a live-cd (Lucid or older) to see which module is loaded, and what the hardware is recognized as.

> 
How do I remove the existing driver and replace it with a non-X varient? Should I black-list the "X" varient?
Yes, that's the easiest way I think. Open up /etc/modprobe.d/blacklist.conf and add:

```

blacklist snd-emu10k1x

```

> 
I assume that the modprobe command will be required but I have never used it before. Any suggestions on how to go about it?
Just add the module name to /etc/modules.
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
snd-emu10k1

```
Again, even if snd-emu10k1 is indeed the correct module, this might not work (no sound at all). Good luck.

---

### Post by sparks40 on 2010-10-13
I checked with lsmod and the sound module has the same "X" designation in both 10.04 (which works) and 10.10 (which does not). Unfortunately, after trying your suggestion the situation is the same. I was looking for version numbers on the output of lsmod but there are none... to see if a regression might be necessary.

---

### Post by sstruhar on 2010-10-13
as a simple work around, I had one of these lying around:

[http://www.griffintechnology.com/products/imic](http://www.griffintechnology.com/products/imic) 

and it works fine (as it always does with a good quality phillips chipset).  Hopefully somone will get to the bottom of this...

---

### Post by Robsy1 on 2010-10-15
Just to say I have the same problem since upgrading to 1010, and I'm a novice when it comes to repair.

---

### Post by disco_stew on 2010-10-18
@happyhampster: it is the snd-emu10k1x module that is loaded on both kernels (working and not working). The "x" version of the module is specific to the Dell OEM version of the SB card, but that's what I have, and I'm guessing sparks40 too.

Although pulseaudio appears to be the offending process, this really does seem to be a kernel bug in the end.

---

### Post by sparks40 on 2010-10-18
TNX disco_stew. Running lspci definitely shows up as the "X" version. However, it has worked in Ubuntu 10.04 since April. 

Just for fun, I tried the new Mint 10 this morning and I have the same results. I realise that Mint uses Ubuntu as it's base but I thought there just might be enough of a difference between the two that it might work.

I also have a Sound Blaster Audigy PCI card that I was going to reinstall, but as I recall this does not work under Skype, and I do need Skype.

I guess I'll just have to wait until someone out there comes up with a fix.

---

### Post by disco_stew on 2010-10-20
I filed a bug report against pulseaudio on Launchpad. Here is the link: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/663876](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/663876)

Please mark the bug as affecting you and add any comments you might have, so that we can get this noticed by the devs.

---

### Post by wjhildreth on 2010-10-20
I have the same issue and have marked the bug report as such.  Thanks for opening it.

Joe

---

### Post by mwa_023 on 2010-10-20
I am also having this problem too, in 10.10- after upgrading from 10.04.

I did not have this issue in 10.04



Dell Dimension 4600
Pentium4 2.8ghz
4gb of ram

Sound Card:

SB Live! EMU10k1x

Thanks!

---

### Post by sparks40 on 2010-10-21
I finally changed the audio card to a Sound Blaster Audigy, which previously did NOT work for me, and it works fine. 

For some reason the driver for the Sound Blaster Live is corrupted or at least not configured properly. I appreciate the frustration of all those who have responded and hope that the situation will be corrected for you soon.

---

### Post by disco_stew on 2010-10-21
sparks 40 is right; it appears as though all (?) of us are using the same module snd-emu10k1x. I added this to the bug report.

---

### Post by paranoid_humanoid on 2010-10-22
Same problem. Same sound card. Same frustration :(

---

### Post by IHeartGaming on 2010-10-22
I have this same sound card. I an new to forums.
I have a workaround to this problem.

In Ubuntu 10.10; go to:
System>Preferences>Sound.
Click the Hardware tab.
Under "Settings for the selected device:" choose the profile "Analog Surround 4.0 Output + Analog Stereo Input".
Click the Close button.

The sound works perfectly!!

---

### Post by ersin2k on 2010-10-26
Thank you IHeartGaming

this is great tip :)
it worked and
you saved my ubuntu 10.10 ;)
:guitar:


> **IHeartGaming said:**
> I have this same sound card. I an new to forums.
I have a workaround to this problem.

In Ubuntu 10.10; go to:
System>Preferences>Sound.
Click the Hardware tab.
Under "Settings for the selected device:" choose the profile "Analog Surround 4.0 Output + Analog Stereo Input".
Click the Close button.

The sound works perfectly!!

---

### Post by sparks40 on 2010-10-26
IHeartGaming... thanks for your solution. I appreciate your taking the time to help all of us out of this dilema.

---

### Post by wjhildreth on 2010-10-27
IHeartGaming

Looks like your suggestion is working for me too.  Should this be mentioned in the bug report? Or has it already been done?

Thanks again.  I was starting to miss Boxee and my 4K plus video library.

Your the bomb!

Joe

---

### Post by wjhildreth on 2010-10-27
I think I jumped the gun.

When trying to play a video (divx) through media player I get the following message:

pa_stream_writable_size() failed: connection terminated.

VLC will play the video but with no sound.

:-(

Joe

PS, the fix causes boxee to terminate.

---

### Post by dyetheskin on 2010-11-01
I got the same issue with the same card,the fix didn't work for me whether I used it for the sb card or the internal audio :(.   Hopefully the devs are fixing this.

---

### Post by vanessaezekowitz on 2010-11-05
Many thanks, IHeartGaming, one of my machines was having this exact issue and your solution got the audio into a working state again.

---

### Post by srikar on 2010-12-19
Thanks I heart Gaming :D

---

### Post by aJayRoo on 2011-01-22
> **IHeartGaming said:**
> I have this same sound card. I an new to forums.
I have a workaround to this problem.

In Ubuntu 10.10; go to:
System>Preferences>Sound.
Click the Hardware tab.
Under "Settings for the selected device:" choose the profile "Analog Surround 4.0 Output + Analog Stereo Input".
Click the Close button.

The sound works perfectly!!

This workaround did the trick for me with Ubuntu 10.10. However, I have Kubuntu 10.10 installed now and am suffering the same problem, but since it is KDE I don't have the same options available in audio preferences. Does anyone know how to perform this workaround in Kubuntu?

[EDIT] I think I have fixed this using the command line interface to pulseaudio:
```
pacmd
```
Then changing the default profile of my card (card index 0):
```
>>> set-card-profile 0 output:analog-surround-40+input:analog-stereo
```
The fix appears to persist after a reboot.

---

### Post by AlFrugal on 2011-01-27
I've been having the same problem with Ubuntu 10.10 and Fedora 14. My sound card is a SB Live! Value scavenged from a Dell Dimension 4600. LSPCI says that I'm using the EMU10K1X driver on both Ubuntu and Fedora.

What I wanted to add to this thread, is that I also booted a Lubuntu 10.10 live-CD and the SB Live! card outputs fine. Lubuntu 10.10 does not have Pulseaudio installed. The Lubuntu CD is using kernel 2.6.35-22-generic.

The solution recommended in this thread, changing the output profile to "Analog Surround 4.0 Output - Analog Stereo Input" produces at least a partial solution for me. At least some of the time, I can play a downloaded MP3 at normal speed. Playing a live stream radio station (through "Movie Player") produces no sound output for me. I don't know if that's related to the sound card problem or is something else.

---

### Post by nickbnf on 2011-02-11
> **aJayRoo said:**
> 
Then changing the default profile of my card (card index 0):
```
>>> set-card-profile 0 output:analog-surround-40+input:analog-stereo
```

That sounds great, but "output:analog-surround-40+input:analog-stereo" gives a "Failed to set card profile to..." error for my card. Do you know how to have the list of valid profiles for set-card-profile?

---

### Post by woodmaster on 2011-03-14
> **ersin2k said:**
> Thank you IHeartGaming

this is great tip :)
it worked and
you saved my ubuntu 10.10 ;)
:guitar:
+1...it's fixed!!!

---

### Post by DrPhuzzichtkeit on 2011-12-29
This post solved it for me:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/508099](https://bugs.launchpad.net/ubuntu/+s...er/+bug/508099)

"trashanken" says:
"[FONT="Courier New"]The default sample rate is set to 48000 kHz which makes music play too fast.

Solution:
Open a console window and run the command

alsamixer

Use the right arrow key and move far right until you get to 'Clock In', change 48000 to 44100 with the down arrow key. Exit the console window - you're done and the music plays correctly![/FONT]"

---

