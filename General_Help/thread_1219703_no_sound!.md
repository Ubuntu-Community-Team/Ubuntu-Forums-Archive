---
title: "no sound!"
date: 2009-07-22
forum: General Help
---

### Post by langyaw on 2009-07-22
at first the problem was the inability to install new programs. that's solved now, but I noticed that my machine is very quiet. tried Internet radio, and the player indicated that I was streaming music, but nothing. I tried playing a DVD. the video plays, but no sound. 
I tried opening System, Sound Preferences. The default settings on "Sound Events", "Music and Movies" & "Audio Conferencing", were "Autodetect", but when I click on the "Test" button, the "Testing Pipeline" window just said "Testing" with the indicator bar going back and forth endlessly. 
the volume control in the taskbar is at 100%
I've also tried recording, but apparently Ubuntu does not recognize the mic.
I've also tried "Administration", Hardware Drivers, but it shows "Alternate Atheros "madwifi" driver" which I'm not supposed to install unless I have problems with wireless LAN, and "ATI/AMD proprietary FGLRX graphics driver", which I'm not concerned about.
what am I missing? :confused: I'm a newbie in Ubuntu, but not in Windows.
when I go back to Vista, everything is fine.
my laptop is HP Pavilion dv5, with built-in cam, mic, CD/DVD-RW.
BTW, when I first installed Ubuntu 8.1, I could hear startup and shutdown sounds in it. After I upgraded to 9.04, they were gone.

---

### Post by j7%&lt;RmUg on 2009-07-22
Ubuntu by default usually doesnt have the correct packages installed to play and record sound. It will say it is playing something when in fact it is but just without the sound.

To get sound working try running this command in a terminal:

```

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```

You will need a net connection to install these. Also set all the options in System > Preferences > Sounds to your sound card or onboard sound chip.

Post here with what you come up with.

---

### Post by bobnutfield on 2009-07-22
Sound is also sometimes muted on a new install or upgrade from one release to another.  You could open a terminal and run:

> alsamixer

just to make sure that the speakers are not muted.

---

### Post by irv on 2009-07-22
You can also right click on the little speaker in the panel and open the Volume Control. See screen shot.
[ATTACH]121996[/ATTACH]

---

### Post by langyaw on 2009-07-23
> **irv said:**
> You can also right click on the little speaker in the panel and open the Volume Control. See screen shot.
[ATTACH]121996[/ATTACH]

did that already, irv, and played around with it, but nothing.
I'll try the other methods suggested above. I just don't have my Ubuntu laptop with me now.
I'll update you with how I progress.
TIA!

---

### Post by langyaw on 2009-07-23
> **bobnutfield said:**
> Sound is also sometimes muted on a new install or upgrade from one release to another.  You could open a terminal and run:



just to make sure that the speakers are not muted.

I think you failed to type the terminal command(s) there?
no, my speakers are not muted.

---

### Post by irv on 2009-07-23
Do you have your sound set at "ALSA"?
That's the only thing that works for me.

---

### Post by langyaw on 2009-07-25
> **nisshh said:**
> Ubuntu by default usually doesnt have the correct packages installed to play and record sound. It will say it is playing something when in fact it is but just without the sound.

To get sound working try running this command in a terminal:

```

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```

You will need a net connection to install these. Also set all the options in System > Preferences > Sounds to your sound card or onboard sound chip.

Post here with what you come up with.

after asking for my password and pressing <Enter>, here is the response:
Reading package lists... Done
Building dependency tree
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-ffmpeg set to manually installed.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
E: Couldn't find package gstreamer0.10-plugs-base
-=-=-=-
What do you mean by "set all the options in System > Preferences > Sounds to your sound card or onboard sound chip."? Will "AUTODETECT" not do that, as well? Or do I need to go back to Windows to find out the sound card specs?
SURPRISE! I plugged in my earphones to the laptop, and I can hear the sounds. but why isn't it coming out from the main speakers? HELP!

---

### Post by manualqr on 2009-07-25
Worked for me (and a ton of other people):
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

good luck

---

### Post by langyaw on 2009-07-27
> **manualqr said:**
> Worked for me (and a ton of other people):
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

good luck

manualqr, the page has not been helpful. I think it applies only to PC / desktops, not laptops. I tried those checks, but I can only hear the pink noise through the earphones, not from the laptop speakers.:confused:
I think my case resembles that of installing an OS to a laptop other than its OEM OS. months ago, I tried installing a Vista Home Premium in an attempt to re-install Windows, but the new system could not recognize my devices. good thing I used the recovery disc to restore it to factory condition.
I hope you Linux experts would have something to help me in this problem. I really want to gain proficiency in Ubuntu / Linux.

---

### Post by irv on 2009-07-27
My laptop (Dell Inspiron 1521) has buttons on the laptop for sound. If you have any on yours, did you try playing around with them?

---

### Post by langyaw on 2009-07-28
> **irv said:**
> My laptop (Dell Inspiron 1521) has buttons on the laptop for sound. If you have any on yours, did you try playing around with them?

mine has like a touchscreen slider. it behaves the same as when maximizing the volume from the taskbar, that is, if you maximize the volume from the task bar, the slider also moves up to maximum. so, that doesn't work, too.
maybe I need to install ALSA drivers for this. :confused:
dunno.
still looking.

---

### Post by irv on 2009-07-28
The Alsa should already be part of the sound. Here is my screen shot of my volume control. [ATTACH]122712[/ATTACH]
You can see I have it set to Alsa mixer.
Go to the package manager and mark sure you have installed the alsa-base driver package for your sound. [ATTACH]122713[/ATTACH]

---

### Post by langyaw on 2009-07-29
> **irv said:**
> The Alsa should already be part of the sound. Here is my screen shot of my volume control. [ATTACH]122712[/ATTACH]
You can see I have it set to Alsa mixer.
Go to the package manager and mark sure you have installed the alsa-base driver package for your sound. [ATTACH]122713[/ATTACH]

I wanted to post my screenshots, but it's proving to be a hassle. anyway, your Mixer has additional tabs but mine has only 2 (Playback & Sound Theme). Under Playback, I have Master, Headphone, PCM & Front.
In Sound Theme, my Sound Theme is "Ubuntu" & alert sound is "default".

For the Synaptic Package Manager, I noticed immediately that you under alsa-base (which I already have), you also had "alsa-firmware-loaders" which I did not have. I immediately installed this, but still no sound.
I rebooted, still nothing. (but I still have sound through the earphones.)

---

### Post by irv on 2009-07-29
> your Mixer has additional tabs but mine has only 2 (Playback & Sound Theme). Under Playback, I have Master, Headphone, PCM & Front.
In Sound Theme, my Sound Theme is "Ubuntu" & alert sound is "default".
In your volume control select preferences and put checks in the boxes in the next window for the options you want. As far as the sound set on "default", try changing it and see if anything happens. You can always change it back.
[ATTACH]122813[/ATTACH]
As far as having sound with earphones and not speakers, that is a hardware thing. Either the speakers are turn off, not working because there is something wrong with them. Maybe you should check the list of hardware to see if there is a issue with you make and model.

---

### Post by langyaw on 2009-08-06
> **bobnutfield said:**
> Sound is also sometimes muted on a new install or upgrade from one release to another.  You could open a terminal and run:



just to make sure that the speakers are not muted.

hi bob,
I ran "alsamixer" in the terminal, and it showed the bars full:
Master=97; Headphone=100<>100; PCM=100<>100; Front=100<>100.
Card: HDA ATI SB
Chip: IDT 92HD71B7X
View: [Playback] Capture All
Item: Master [dB gain=3.00]

what now?

---

### Post by langyaw on 2009-08-08
> **irv said:**
> In your volume control select preferences and put checks in the boxes in the next window for the options you want. As far as the sound set on "default", try changing it and see if anything happens. You can always change it back.
[ATTACH]122813[/ATTACH]
As far as having sound with earphones and not speakers, that is a hardware thing. Either the speakers are turn off, not working because there is something wrong with them. Maybe you should check the list of hardware to see if there is a issue with you make and model.

hi irv, there's nothing wrong with my hardware, as when I switch to Windows, the sound is there.

---

### Post by langyaw on 2009-11-22
> **langyaw said:**
> at first the problem was the inability to install new programs. that's solved now, but I noticed that my machine is very quiet. tried Internet radio, and the player indicated that I was streaming music, but nothing. I tried playing a DVD. the video plays, but no sound. 
I tried opening System, Sound Preferences. The default settings on "Sound Events", "Music and Movies" & "Audio Conferencing", were "Autodetect", but when I click on the "Test" button, the "Testing Pipeline" window just said "Testing" with the indicator bar going back and forth endlessly. 
the volume control in the taskbar is at 100%
I've also tried recording, but apparently Ubuntu does not recognize the mic.
I've also tried "Administration", Hardware Drivers, but it shows "Alternate Atheros "madwifi" driver" which I'm not supposed to install unless I have problems with wireless LAN, and "ATI/AMD proprietary FGLRX graphics driver", which I'm not concerned about.
what am I missing? :confused: I'm a newbie in Ubuntu, but not in Windows.
when I go back to Vista, everything is fine.
my laptop is HP Pavilion dv5, with built-in cam, mic, CD/DVD-RW.
BTW, when I first installed Ubuntu 8.1, I could hear startup and shutdown sounds in it. After I upgraded to 9.04, they were gone.

finally, this is SOLVED! 
how?
I just updated to Ubuntu 9.1!
anyway, thanks to all you guys who responded.

---

### Post by Digikid on 2009-11-22
I am noticing a thread here regarding HP Laptops.  Try this.  Disable your 56K modem driver and reboot.  You SHOULD have sound as long as you do not activate that modem.

At least that is how it is on my HP Laptops.  Weird.

---

### Post by garvinrick4 on 2009-11-22
With exact same problems this worked for me. And I tried a lot of fixes.

Fix for my HP G71-340 Laptop sound 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

