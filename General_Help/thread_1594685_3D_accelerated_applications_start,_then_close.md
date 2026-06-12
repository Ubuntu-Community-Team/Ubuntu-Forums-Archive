---
title: "3D accelerated applications start, then close"
date: 2010-10-12
forum: General Help
---

### Post by Alan|Cvette on 2010-10-12
Hey folks! I'm running the latest 10.10 and loving it, former Windows user :)

I noticed just shortly after installing 10.4, that a few select applications would open and I would see "Starting (application name)" and then it would close and nothing else would happen. I suspect this is related to the fact that I recently took my Video Card out of my PC and Ubuntu is not detecting my Intel Chip? Any help is mucho appreciated! : )

---

### Post by Alan|Cvette on 2010-10-13
Though I hate to do this, I feel I am already left in the dust haha. Bump.

---

### Post by coldraven on 2010-10-13
Don't feel left out! :P
It is possible that your onboard Intel chipset is not supported very well.
The only reason that I know this is because I installed 10.04 on a PC that worked perfectly with 8.04 and afterwards it crashed when anything using OpenGL started to run. It had a slightly old Intel chipset but I don't know which one. I reinstalled 8.04!
Put your video card back in!

---

### Post by Alan|Cvette on 2010-10-13
> **coldraven said:**
> Don't feel left out! :P
It is possible that your onboard Intel chipset is not supported very well.
The only reason that I know this is because I installed 10.04 on a PC that worked perfectly with 8.04 and afterwards it crashed when anything using OpenGL started to run. It had a slightly old Intel chipset but I don't know which one. I reinstalled 8.04!
Put your video card back in!

Don't laugh, but I can't. For whatever reason both ATI and HP are clueless as to why, but both the monitor and card aren't fully compatible. Every now-and-then the monitor won't come on, so I have to reboot, reboot, reboot, presto! 

This is strange though, my PC is only about oh say a year old. I first noticed this when Frets on Fire wouldn't load, then I tried Moovida Media Center and that wouldn't load either. Perhaps I should move this into a video/hardware section? I have no clue :)

---

### Post by Alan|Cvette on 2010-10-14
Perhaps of further help, I found out today that it is the Intel 82G33/G31 accelerator .

---

### Post by Alan|Cvette on 2010-10-15
Bump :(

---

### Post by Alan|Cvette on 2010-10-27
Bump

---

### Post by 3rdalbum on 2010-10-27
Try removing the Xorg.conf file:

```
sudo rm /etc/X11/xorg.conf
```

This forces X to detect your settings whenever it starts up, which should definitely get the Intel graphics working and hopefully use whatever information the monitor provides regarding resolution.

---

### Post by Alan|Cvette on 2010-10-27
> **3rdalbum said:**
> Try removing the Xorg.conf file:

```
sudo rm /etc/X11/xorg.conf
```

This forces X to detect your settings whenever it starts up, which should definitely get the Intel graphics working and hopefully use whatever information the monitor provides regarding resolution.

Thank you so much for the reply! The output of that code is

```
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
```

---

### Post by Alan|Cvette on 2010-10-27
Maybe this will be of some help:

```
alan@alan-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
```

```
alan@alan-desktop:~$ sudo lshw -C video
[sudo] password for alan: 
  *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fe900000-fe97ffff ioport:c080(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff

```

---

### Post by mcoleman44 on 2010-10-27
You might want to try checking your xorg.0.log System < Administration < LogFileViewer

This might give you a hint as to what going on. Look for EE

Also, have you tried going to system < admin < hardware Drivers?

---

### Post by Alan|Cvette on 2010-10-27
> **mcoleman44 said:**
> You might want to try checking your xorg.0.log System < Administration < LogFileViewer

This might give you a hint as to what going on. Look for EE

Also, have you tried going to system < admin < hardware Drivers?

I did a search in that log and found: 
(EE) GLX error: Can not get required symbols.

Yes I've tried looking in the Hardware Drivers, but it is blank, no drivers found for my system.

---

### Post by mcoleman44 on 2010-10-27
What do you have your effect settings on? Are you using compositing?

---

### Post by Alan|Cvette on 2010-10-27
I have 5 Xorg.(#) logs. Only one different mention of EE which is:

```
(EE) No supported AMD display adapters were found
```

Which is weird as I took my ATI video card out a few weeks ago.

---

### Post by Alan|Cvette on 2010-10-27
Visual Effects are set to "none". And in Ubuntu Tweak "use metacity's compositing feature" is turned off.

---

### Post by mcoleman44 on 2010-10-27
hmm... well just try reseting your xserver settings. Did your problem begin after you changed video cards?

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Alan|Cvette on 2010-10-27
I can't really say, I never tried any 3D games/applications when I had my ATI card in. I just tried that code, do I need to restart now? (I'm too use to windows :) )

---

### Post by mcoleman44 on 2010-10-27
Well all you have to do is restart the xserver but a full restart wouldnt hurt

---

### Post by mcoleman44 on 2010-10-27
you know.. I dont know why I havent asked this yet, but is it all the applications wont work or just a few? if just a few, which ones?

---

### Post by Alan|Cvette on 2010-10-27
Just rebooted. No change at all. I downloaded Ubuntu Netbook Edition last night, I can try installing and testing out a 3D application on there if you think it would help narrow down the problem.

---

### Post by Alan|Cvette on 2010-10-27
About every 3D application from Assault Cube, Frets on Fire, to 3D Chess, and even the Moovida Media Center don't work. I click on the application and nothing happens, nothing at all.

---

### Post by mcoleman44 on 2010-10-27
Have you tried updating yet?
if you just recently installed then try this
```
sudo apt-get update && sudo apt-get upgrade
```

after doing this check hardware drivers again

---

### Post by Alan|Cvette on 2010-10-27
It just performed a small update which was for Firefox, and then checked again but there is still nothing in Additional Drivers.

---

### Post by ubunterooster on 2010-10-27
This is not an isolated problem with this card; I see several instances of this exact problem on this card. It does not enable the proper drivers by default.

[http://ubuntuforums.org/showthread.php?t=1602665&highlight=82G33%2FG31]("http://ubuntuforums.org/showthread.php?t=1602665&highlight=82G33%2FG31")
> **zonemikel said:**
> I  used this xorg and restarted gdm; its working great. 

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ca"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver "intel"
        Option "DPMS"
        Option  "NoDDC"
        Option "XaaNoOffscreenPixmaps" "1"
        Option "AccelMethod" "exa"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     340    270  
        HorizSync 30-97
        VertRefresh 50-180
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection



```

---

### Post by Alan|Cvette on 2010-10-27
Hi there! Thanks for the reply, that looks promising! The x11 directory appears to be read-only, and I do not have an xorg.config. Should I create one from a standard text file?

---

### Post by ubunterooster on 2010-10-27
use ```
gksu nautilus
``` to allow permissions to write to the directory. Yes, I think you make a text file but instead of "untitled1.txt" (default) name it xorg.config

---

### Post by 3rdalbum on 2010-10-27
> **Alan|Cvette said:**
> Hi there! Thanks for the reply, that looks promising! The x11 directory appears to be read-only, and I do not have an xorg.config. Should I create one from a standard text file?

It's "xorg.conf", the directory is "X11" (with a capital X, it's important) and it's read-only for your ordinary user account; only root can modify system directories. So if you hit Alt-F2 and type in the following:

```
gksudo gedit /etc/X11/xorg.conf
```

it will open a text editor as root, create the file, and all you need to do is copy and paste in what you need to, and then click the Save button.

---

### Post by Alan|Cvette on 2010-10-27
Okay, just created the xorg.conf with those settings. Rebooted for safe measure. And still nothing working :(

EDIT: Not even the official System Test from Ubuntu to confirm 3D acceleration is working properly passes.

---

### Post by mcoleman44 on 2010-10-27
What exactly did u put in the xorg.conf. Also try checking your log files again and see of u have any new errors

---

### Post by Alan|Cvette on 2010-10-27
> **mcoleman44 said:**
> What exactly did u put in the xorg.conf. Also try checking your log files again and see of u have any new errors

I copy/pasted the entire block that ubunturooster posted. There is one new error I hadn't seen before, in Xorg.log 2, 3, 4, and 5. It says "(EE) No devices detected."

---

### Post by mcoleman44 on 2010-10-27
Try this:  [http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100)

If u need any help with the instructions let me know

---

### Post by Alan|Cvette on 2010-10-28
> **mcoleman44 said:**
> Try this:  [http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100)

If u need any help with the instructions let me know

Darn, I ran across that earlier actually. No 64-bit package :(

Mucho thanks for all the help so far folks!!! I thought I would never get this worked out.

---

### Post by mcoleman44 on 2010-10-28
Ohh... You dont have 32bit... That does create a problem. Haha. I'm thinking.

---

### Post by Alan|Cvette on 2010-10-28
I can upload the output of that system test if that'll help?

---

### Post by mcoleman44 on 2010-10-28
Have you installed this: xserver-xorg-video-intel 
If not then:
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by Alan|Cvette on 2010-10-28
> **mcoleman44 said:**
> Have you installed this: xserver-xorg-video-intel 
If not then:
```
sudo apt-get install xserver-xorg-video-intel
```

Yes, it was already installed.

---

### Post by mcoleman44 on 2010-10-28
Ohh a after you install that try deleting the xorg conf file and restarting.

---

### Post by mcoleman44 on 2010-10-28
Well darn...

---

### Post by mcoleman44 on 2010-10-28
Try the fourth paragraph down: [http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html](http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html)

---

### Post by Alan|Cvette on 2010-10-28
> **mcoleman44 said:**
> Well darn...

This is a tough little buggah.

---

### Post by Alan|Cvette on 2010-10-28
> **mcoleman44 said:**
> Try the fourth paragraph down: [http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html](http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html)

No luck there either :(

---

### Post by mcoleman44 on 2010-10-28
OMG! ok, try uploading the results of the test. We've tried everything else

---

### Post by Alan|Cvette on 2010-10-28
cat /proc/asound/card*/codec#*

```
Codec: Realtek ALC1200
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x103c2a6f
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC1200 Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC1200 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC1200 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a1984f: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x01813050: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01446130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x01c41160: [Jack] SPDIF In at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
```



cat /var/log/dmesg | ansi_parser

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #36-Ubuntu SMP Tue Oct 26 17:13:06 UTC 2010 (Ubuntu 2.6.35-23.36-generic 2.6.35.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=51d47456-b91a-4c48-8f8e-d6b378f37aca ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf6a0000 (usable)
[    0.000000]  BIOS-e820: 00000000cf6a0000 - 00000000cf6ae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf6ae000 - 00000000cf6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf6e0000 - 00000000cf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x1b0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask F80000000 write-back
[    0.000000]   4 base 180000000 mask FE0000000 write-back
[    0.000000]   5 base 1A0000000 mask FF0000000 write-back
[    0.000000]   6 base 0CF700000 mask FFFF00000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cf700000 - 00000000cf800000 (usable) ==> (reserved)
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcf6a0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b000 (usable)
[    0.000000]  modified: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cf6a0000 (usable)
[    0.000000]  modified: 00000000cf6a0000 - 00000000cf6ae000 (ACPI data)
[    0.000000]  modified: 00000000cf6ae000 - 00000000cf6e0000 (ACPI NVS)
[    0.000000]  modified: 00000000cf6e0000 - 00000000cf700000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000cf6a0000
[    0.000000]  0000000000 - 00cf600000 page 2M
[    0.000000]  00cf600000 - 00cf6a0000 page 4k
[    0.000000] kernel direct mapping tables up to cf6a0000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-00000001b0000000
[    0.000000]  0100000000 - 01b0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1b0000000 @ 1a000-22000
[    0.000000] RAMDISK: 37572000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fc440 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT 00000000cf6a0000 00044 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cf6a0200 00084 (v02 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cf6a0440 04E91 (v01 HPQOEM SLIC-CPC 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cf6ae000 00040
[    0.000000] ACPI: APIC 00000000cf6a0390 0006C (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cf6a0400 0003C (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cf6ae040 00072 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cf6a52e0 00038 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000cf6ae0c0 02024 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cf6b00f0 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: SSDT 00000000cf6b0bf0 0082F (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000001b0000000
[    0.000000] Initmem setup node 0 0000000000000000-00000001b0000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea0005ffffff] PMD -> [ffff880100200000-ffff8801057fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001b0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000cf6a0
[    0.000000]     0: 0x00100000 -> 0x001b0000
[    0.000000] On node 0 totalpages: 1570347
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3923 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 831192 pages, LIFO batch:31
[    0.000000]   Normal zone: 9856 pages used for memmap
[    0.000000]   Normal zone: 711040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1d000 - 1d7ff]
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cf6a0000 - 00000000cf6ae000
[    0.000000] PM: Registered nosave memory: 00000000cf6ae000 - 00000000cf6e0000
[    0.000000] PM: Registered nosave memory: 00000000cf6e0000 - 00000000cf700000
[    0.000000] PM: Registered nosave memory: 00000000cf700000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cf700000 (gap: cf700000:2f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1546155
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=51d47456-b91a-4c48-8f8e-d6b378f37aca ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] early_res array is doubled to 128 at [25800 - 267ff]
[    0.000000] Subtract (57 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037572000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d187c4]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009b000 - 00000f1cf0]   BIOS reserved
[    0.000000]   #7 [00000f1e3c - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000f1cf0 - 00000f1e3c]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #12 [000001a000 - 000001d000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18800 - 0001d19800]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d175c0]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0105800000]        MEMMAP 0
[    0.000000]   #19 [0001d175c0 - 0001d17740]         BOOTMEM
[    0.000000]   #20 [0001d19800 - 0001d31800]         BOOTMEM
[    0.000000]   #21 [0001d31800 - 0001d49800]         BOOTMEM
[    0.000000]   #22 [0001d4a000 - 0001d4b000]         BOOTMEM
[    0.000000]   #23 [0001d17740 - 0001d17781]         BOOTMEM
[    0.000000]   #24 [0001d177c0 - 0001d17803]         BOOTMEM
[    0.000000]   #25 [0001d17840 - 0001d17aa8]         BOOTMEM
[    0.000000]   #26 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #27 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #28 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #29 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #30 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #31 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #32 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #33 [0001d17e40 - 0001d17ea8]         BOOTMEM
[    0.000000]   #34 [0001d17ec0 - 0001d17f28]         BOOTMEM
[    0.000000]   #35 [0001d17f40 - 0001d17fa8]         BOOTMEM
[    0.000000]   #36 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #37 [0001d49800 - 0001d49820]         BOOTMEM
[    0.000000]   #38 [0001d49840 - 0001d498aa]         BOOTMEM
[    0.000000]   #39 [0001d498c0 - 0001d4992a]         BOOTMEM
[    0.000000]   #40 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #42 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #44 [0001d49940 - 0001d49948]         BOOTMEM
[    0.000000]   #45 [0001d49980 - 0001d49988]         BOOTMEM
[    0.000000]   #46 [0001d499c0 - 0001d499d0]         BOOTMEM
[    0.000000]   #47 [0001d49a00 - 0001d49a20]         BOOTMEM
[    0.000000]   #48 [0001d49a40 - 0001d49b70]         BOOTMEM
[    0.000000]   #49 [0001d49b80 - 0001d49bd0]         BOOTMEM
[    0.000000]   #50 [0001d49c00 - 0001d49c50]         BOOTMEM
[    0.000000]   #51 [0001d4b000 - 0001d53000]         BOOTMEM
[    0.000000]   #52 [0001d49c80 - 0001d49ec0]         BOOTMEM
[    0.000000]   #53 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #54 [0001d53000 - 0001d73000]         BOOTMEM
[    0.000000]   #55 [0001d73000 - 0001db3000]         BOOTMEM
[    0.000000]   #56 [000001d800 - 0000025800]         BOOTMEM
[    0.000000] Memory: 6102420k/7077888k available (5710k kernel code, 796500k absent, 178968k reserved, 5380k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 62914560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2599.465 MHz processor.
[    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5198.93 BogoMIPS (lpj=25994650)
[    0.010013] pid_max: default: 32768 minimum: 301
[    0.010037] Security Framework initialized
[    0.010056] AppArmor: AppArmor initialized
[    0.010057] Yama: becoming mindful.
[    0.010788] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.016123] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021819] Mount-cache hash table entries: 256
[    0.021977] Initializing cgroup subsys ns
[    0.021982] Initializing cgroup subsys cpuacct
[    0.021985] Initializing cgroup subsys memory
[    0.021995] Initializing cgroup subsys devices
[    0.021997] Initializing cgroup subsys freezer
[    0.021999] Initializing cgroup subsys net_cls
[    0.022029] CPU: Physical Processor ID: 0
[    0.022030] CPU: Processor Core ID: 0
[    0.022032] mce: CPU supports 6 MCE banks
[    0.022040] CPU0: Thermal monitoring enabled (TM2)
[    0.022044] using mwait in idle threads.
[    0.022046] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.022053] ... version:                2
[    0.022055] ... bit width:              40
[    0.022056] ... generic registers:      2
[    0.022057] ... value mask:             000000ffffffffff
[    0.022059] ... max period:             000000007fffffff
[    0.022060] ... fixed-purpose events:   3
[    0.022061] ... event mask:             0000000700000003
[    0.024350] ACPI: Core revision 20100428
[    0.030011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030016] ftrace: allocating 22688 entries in 89 pages
[    0.040057] Setting APIC routing to flat
[    0.040417] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.141580] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.150000] APIC calibration not consistent with PM-Timer: 149ms instead of 100ms
[    0.150000] APIC delta adjusted to PM-Timer: 1249970 (1874949)
[    0.150000] Booting Node   0, Processors  #1
[    0.310018] Brought up 2 CPUs
[    0.310021] Total of 2 processors activated (10382.46 BogoMIPS).
[    0.310517] devtmpfs: initialized
[    0.310599] regulator: core version 0.5
[    0.310624] Time: 22:28:45  Date: 10/27/10
[    0.310659] NET: Registered protocol family 16
[    0.310680] Trying to unpack rootfs image as initramfs...
[    0.310778] ACPI: bus type pci registered
[    0.310842] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.310844] PCI: not using MMCONFIG
[    0.310846] PCI: Using configuration type 1 for base access
[    0.320087] bio: create slab <bio-0> at 0
[    0.321102] ACPI: EC: Look up EC in DSDT
[    0.322130] ACPI: Executed 1 blocks of module-level executable AML code
[    0.327340] ACPI: SSDT 00000000cf6b0270 002B0 (v01 HPQOEM SLIC-CPC 00000011 INTL 20051117)
[    0.327585] ACPI: Dynamic OEM Table Load:
[    0.327588] ACPI: SSDT (null) 002B0 (v01 HPQOEM SLIC-CPC 00000011 INTL 20051117)
[    0.327970] ACPI: SSDT 00000000cf6b0730 002B0 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.328217] ACPI: Dynamic OEM Table Load:
[    0.328220] ACPI: SSDT (null) 002B0 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.328281] ACPI: Interpreter enabled
[    0.328284] ACPI: (supports S0 S1 S3 S4 S5)
[    0.328303] ACPI: Using IOAPIC for interrupt routing
[    0.328350] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.329801] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.371132] ACPI: No dock devices found.
[    0.371136] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.371273] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.371538] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.371540] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.371543] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.371545] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.371547] pci_root PNP0A08:00: host bridge window [mem 0xcf700000-0xdfffffff]
[    0.371550] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.371607] pci 0000:00:02.0: reg 10: [mem 0xfe900000-0xfe97ffff]
[    0.371611] pci 0000:00:02.0: reg 14: [io  0xc080-0xc087]
[    0.371615] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.371618] pci 0000:00:02.0: reg 1c: [mem 0xfe800000-0xfe8fffff]
[    0.371707] pci 0000:00:1a.0: reg 20: [io  0xc400-0xc41f]
[    0.371784] pci 0000:00:1a.1: reg 20: [io  0xc480-0xc49f]
[    0.371855] pci 0000:00:1a.7: reg 10: [mem 0xfe9fec00-0xfe9fefff]
[    0.371913] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.371917] pci 0000:00:1a.7: PME# disabled
[    0.371957] pci 0000:00:1b.0: reg 10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.372008] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.372012] pci 0000:00:1b.0: PME# disabled
[    0.372092] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.372096] pci 0000:00:1c.0: PME# disabled
[    0.372182] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.372186] pci 0000:00:1c.2: PME# disabled
[    0.372247] pci 0000:00:1d.0: reg 20: [io  0xc800-0xc81f]
[    0.372323] pci 0000:00:1d.1: reg 20: [io  0xc880-0xc89f]
[    0.372396] pci 0000:00:1d.2: reg 20: [io  0xcc00-0xcc1f]
[    0.372471] pci 0000:00:1d.3: reg 20: [io  0xd000-0xd01f]
[    0.372538] pci 0000:00:1d.7: reg 10: [mem 0xfe9ff800-0xfe9ffbff]
[    0.372594] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.372598] pci 0000:00:1d.7: PME# disabled
[    0.372724] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.372728] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.372731] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.372797] pci 0000:00:1f.2: reg 10: [io  0xd880-0xd887]
[    0.372803] pci 0000:00:1f.2: reg 14: [io  0xd800-0xd803]
[    0.372809] pci 0000:00:1f.2: reg 18: [io  0xd480-0xd487]
[    0.372815] pci 0000:00:1f.2: reg 1c: [io  0xd400-0xd403]
[    0.372821] pci 0000:00:1f.2: reg 20: [io  0xd080-0xd09f]
[    0.372827] pci 0000:00:1f.2: reg 24: [mem 0xfe9ff000-0xfe9ff7ff]
[    0.372866] pci 0000:00:1f.2: PME# supported from D3hot
[    0.372870] pci 0000:00:1f.2: PME# disabled
[    0.372904] pci 0000:00:1f.3: reg 10: [mem 0xfe9ffc00-0xfe9ffcff 64bit]
[    0.372922] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.372992] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.372996] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.373001] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.373008] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.373168] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.373242] pci 0000:02:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
[    0.373292] pci 0000:02:00.0: reg 20: [mem 0xfdff0000-0xfdffffff 64bit pref]
[    0.373318] pci 0000:02:00.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    0.373470] pci 0000:02:00.0: supports D1 D2
[    0.373471] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373485] pci 0000:02:00.0: PME# disabled
[    0.373628] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.373632] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.373636] pci 0000:00:1c.2:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.373642] pci 0000:00:1c.2:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.373699] pci 0000:01:05.0: reg 10: [mem 0xfeaff000-0xfeafffff]
[    0.373746] pci 0000:01:05.0: supports D1 D2
[    0.373748] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.373751] pci 0000:01:05.0: PME# disabled
[    0.373789] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.373794] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.373798] pci 0000:00:1e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.373804] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.373806] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.373808] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.373810] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.373812] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.373814] pci 0000:00:1e.0:   bridge window [mem 0xcf700000-0xdfffffff] (subtractive decode)
[    0.373816] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.373839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.373947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.374049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.374096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.385169] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.385267] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.385358] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.385451] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.385544] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.385636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.385727] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.385817] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.385857] HEST: Table is not found!
[    0.385941] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.385952] vgaarb: loaded
[    0.386074] SCSI subsystem initialized
[    0.386211] libata version 3.00 loaded.
[    0.386213] usbcore: registered new interface driver usbfs
[    0.386227] usbcore: registered new interface driver hub
[    0.386254] usbcore: registered new device driver usb
[    0.386365] ACPI: WMI: Mapper loaded
[    0.386367] PCI: Using ACPI for IRQ routing
[    0.386370] PCI: pci_cache_line_size set to 64 bytes
[    0.386461] reserve RAM buffer: 000000000009b000 - 000000000009ffff 
[    0.386464] reserve RAM buffer: 00000000cf6a0000 - 00000000cfffffff 
[    0.386548] NetLabel: Initializing
[    0.386550] NetLabel:  domain hash size = 128
[    0.386551] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.386565] NetLabel:  unlabeled traffic allowed by default
[    0.386597] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.386603] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.386608] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400034] Switching to clocksource tsc
[    0.409389] AppArmor: AppArmor Filesystem Enabled
[    0.409414] pnp: PnP ACPI init
[    0.409433] ACPI: bus type pnp registered
[    0.411305] pnp: PnP ACPI: found 14 devices
[    0.411307] ACPI: ACPI bus type pnp unregistered
[    0.411321] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.411327] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.411330] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.411332] system 00:06: [io  0x0480-0x04bf] has been reserved
[    0.411334] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.411336] system 00:06: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.411341] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.411343] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.411347] system 00:09: [io  0x0a00-0x0adf] has been reserved
[    0.411351] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    0.411355] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.411360] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.411362] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    0.411364] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.411366] system 00:0d: [mem 0x00100000-0xcf6fffff] could not be reserved
[    0.417158] pci 0000:00:1c.0: BAR 14: assigned [mem 0xcf700000-0xcf8fffff]
[    0.417162] pci 0000:00:1c.0: BAR 15: assigned [mem 0xcf900000-0xcfafffff 64bit pref]
[    0.417166] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.417169] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.417173] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.417178] pci 0000:00:1c.0:   bridge window [mem 0xcf700000-0xcf8fffff]
[    0.417182] pci 0000:00:1c.0:   bridge window [mem 0xcf900000-0xcfafffff 64bit pref]
[    0.417189] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.417192] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.417198] pci 0000:00:1c.2:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.417202] pci 0000:00:1c.2:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.417208] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.417210] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.417215] pci 0000:00:1e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.417219] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.417235] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.417241]   alloc irq_desc for 17 on node -1
[    0.417243]   alloc kstat_irqs on node -1
[    0.417250] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.417255] pci 0000:00:1c.0: setting latency timer to 64
[    0.417264]   alloc irq_desc for 18 on node -1
[    0.417265]   alloc kstat_irqs on node -1
[    0.417268] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.417272] pci 0000:00:1c.2: setting latency timer to 64
[    0.417279] pci 0000:00:1e.0: setting latency timer to 64
[    0.417283] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.417285] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.417287] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.417288] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.417290] pci_bus 0000:00: resource 8 [mem 0xcf700000-0xdfffffff]
[    0.417292] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.417294] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.417296] pci_bus 0000:03: resource 1 [mem 0xcf700000-0xcf8fffff]
[    0.417298] pci_bus 0000:03: resource 2 [mem 0xcf900000-0xcfafffff 64bit pref]
[    0.417300] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.417301] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.417303] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.417305] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.417307] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.417309] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.417311] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.417312] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.417314] pci_bus 0000:01: resource 8 [mem 0xcf700000-0xdfffffff]
[    0.417316] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xffffffff]
[    0.417354] NET: Registered protocol family 2
[    0.417588] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.419242] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.424928] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.425633] TCP: Hash tables configured (established 524288 bind 65536)
[    0.425635] TCP reno registered
[    0.425653] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425748] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425959] NET: Registered protocol family 1
[    0.425978] pci 0000:00:02.0: Boot video device
[    0.426150] PCI: CLS 32 bytes, default 64
[    0.426152] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.426155] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    0.426157] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    0.426356] Scanning for low memory corruption every 60 seconds
[    0.426500] audit: initializing netlink socket (disabled)
[    0.426509] type=2000 audit(1288218524.410:1): initialized
[    0.438764] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.440005] VFS: Disk quotas dquot_6.5.2
[    0.440056] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.440527] fuse init (API version 7.14)
[    0.440598] msgmni has been set to 11918
[    0.440920] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.440923] io scheduler noop registered
[    0.440924] io scheduler deadline registered
[    0.440953] io scheduler cfq registered (default)
[    0.441045] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.441086]   alloc irq_desc for 40 on node -1
[    0.441088]   alloc kstat_irqs on node -1
[    0.441099] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.441186] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.441223]   alloc irq_desc for 41 on node -1
[    0.441225]   alloc kstat_irqs on node -1
[    0.441232] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.441323] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.441390] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.441459] intel_idle: MWAIT substates: 0x22220
[    0.441461] intel_idle: does not run on family 6 model 23
[    0.441560] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.441565] ACPI: Power Button [PWRB]
[    0.441602] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.441604] ACPI: Power Button [PWRF]
[    0.441823] ACPI: acpi_idle registered with cpuidle
[    0.443684] ERST: Table is not found!
[    0.443880] Linux agpgart interface v0.103
[    0.443899] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.445040] brd: module loaded
[    0.445445] loop: module loaded
[    0.445833] Fixed MDIO Bus: probed
[    0.445859] PPP generic driver version 2.4.2
[    0.445886] tun: Universal TUN/TAP device driver, 1.6
[    0.445888] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.445957] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.445980] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.446002] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.446006] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.446036] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.446067] ehci_hcd 0000:00:1a.7: debug port 1
[    0.449964] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.450001] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9fec00
[    0.469817] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.469974] hub 1-0:1.0: USB hub found
[    0.469980] hub 1-0:1.0: 4 ports detected
[    0.470052]   alloc irq_desc for 23 on node -1
[    0.470054]   alloc kstat_irqs on node -1
[    0.470061] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.470087] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.470090] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.470134] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.470164] ehci_hcd 0000:00:1d.7: debug port 1
[    0.474036] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.474054] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.489799] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.489948] hub 2-0:1.0: USB hub found
[    0.489953] hub 2-0:1.0: 8 ports detected
[    0.490024] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.490038] uhci_hcd: USB Universal Host Controller Interface driver
[    0.490114]   alloc irq_desc for 16 on node -1
[    0.490116]   alloc kstat_irqs on node -1
[    0.490123] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.490130] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.490133] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.490167] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.490204] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c400
[    0.490303] hub 3-0:1.0: USB hub found
[    0.490307] hub 3-0:1.0: 2 ports detected
[    0.490350]   alloc irq_desc for 21 on node -1
[    0.490352]   alloc kstat_irqs on node -1
[    0.490355] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.490361] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.490364] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.490393] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.490422] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c480
[    0.490516] hub 4-0:1.0: USB hub found
[    0.490520] hub 4-0:1.0: 2 ports detected
[    0.490567] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.490572] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.490574] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.490599] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.490624] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c800
[    0.490724] hub 5-0:1.0: USB hub found
[    0.490727] hub 5-0:1.0: 2 ports detected
[    0.490773]   alloc irq_desc for 19 on node -1
[    0.490775]   alloc kstat_irqs on node -1
[    0.490779] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.490784] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.490787] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.490811] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.490842] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
[    0.490945] hub 6-0:1.0: USB hub found
[    0.490949] hub 6-0:1.0: 2 ports detected
[    0.490993] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.490999] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.491002] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.491032] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.491054] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cc00
[    0.491143] hub 7-0:1.0: USB hub found
[    0.491146] hub 7-0:1.0: 2 ports detected
[    0.491190] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.491196] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.491199] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.491226] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.491248] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d000
[    0.491337] hub 8-0:1.0: USB hub found
[    0.491340] hub 8-0:1.0: 2 ports detected
[    0.491443] PNP: No PS/2 controller found. Probing ports directly.
[    0.493721] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.493726] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.493822] mice: PS/2 mouse device common for all mice
[    0.493925] rtc_cmos 00:03: RTC can wake from S4
[    0.493961] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.493990] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.494082] device-mapper: uevent: version 1.0.3
[    0.494159] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.494216] device-mapper: multipath: version 1.1.1 loaded
[    0.494219] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.494342] cpuidle: using governor ladder
[    0.494344] cpuidle: using governor menu
[    0.494579] TCP cubic registered
[    0.494682] NET: Registered protocol family 10
[    0.494979] lo: Disabled Privacy Extensions
[    0.495133] NET: Registered protocol family 17
[    0.495852] PM: Resume from disk failed.
[    0.495865] registered taskstats version 1
[    0.496190]   Magic number: 14:315:503
[    0.496302] rtc_cmos 00:03: setting system clock to 2010-10-27 22:28:45 UTC (1288218525)
[    0.496305] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.496306] EDD information not available.
[    0.520777] Freeing initrd memory: 10744k freed
[    0.525582] Freeing unused kernel memory: 908k freed
[    0.526013] Write protecting the kernel read-only data: 10240k
[    0.526166] Freeing unused kernel memory: 412k freed
[    0.526465] Freeing unused kernel memory: 1644k freed
[    0.539488] udev[74]: starting version 163
[    0.602374] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.602418] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.602531] r8169 0000:02:00.0: setting latency timer to 64
[    0.602671]   alloc irq_desc for 42 on node -1
[    0.602673]   alloc kstat_irqs on node -1
[    0.602711] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    0.603140] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000c7c000, 00:26:18:32:ea:be, XID 1c4000c0 IRQ 42
[    0.614715]   alloc irq_desc for 20 on node -1
[    0.614722]   alloc kstat_irqs on node -1
[    0.614730] firewire_ohci 0000:01:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.623221] ahci 0000:00:1f.2: version 3.0
[    0.623243] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.623300]   alloc irq_desc for 43 on node -1
[    0.623302]   alloc kstat_irqs on node -1
[    0.623314] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.623326] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    0.623375] ahci: SSS flag set, parallel bus scan disabled
[    0.623424] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    0.623427] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ccc ems sxs 
[    0.623433] ahci 0000:00:1f.2: setting latency timer to 64
[    0.719868] scsi0 : ahci
[    0.719992] scsi1 : ahci
[    0.720044] scsi2 : ahci
[    0.720093] scsi3 : ahci
[    0.720143] scsi4 : ahci
[    0.720192] scsi5 : ahci
[    0.720337] ata1: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff100 irq 43
[    0.720340] ata2: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff180 irq 43
[    0.720343] ata3: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff200 irq 43
[    0.720345] ata4: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff280 irq 43
[    0.720348] ata5: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff300 irq 43
[    0.720351] ata6: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff380 irq 43
[    0.749790] firewire_ohci: Added fw-ohci device 0000:01:05.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    0.789701] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.961412] Initializing USB Mass Storage driver...
[    0.961514] scsi6 : usb-storage 1-1:1.0
[    0.961593] usbcore: registered new interface driver usb-storage
[    0.961595] USB Mass Storage support registered.
[    1.070059] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.070806] ata1.00: ATA-8: WDC WD6400AAKS-65A7B2, 01.03B01, max UDMA/133
[    1.070811] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.072537] ata1.00: configured for UDMA/133
[    1.090167] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-6 01.0 PQ: 0 ANSI: 5
[    1.090322] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.090325] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.090416] sd 0:0:0:0: [sda] Write Protect is off
[    1.090419] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.090437] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.090551]  sda: sda1 sda2 sda3 < sda5 sda6 sda7
[    1.190017] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.198484]  sda8 sda9 sda10 >
[    1.227312] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.230108] firewire_core: created device fw0: GUID 001e8c0001ec8b10, S400
[    1.341271] scsi7 : usb-storage 2-2:1.0
[    1.461267] usb 2-8: new high speed USB device using ehci_hcd and address 3
[    1.850026] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.850245] ata2.00: ATAPI: ATAPI   DVD A  DH16A6L-C, ZHCH, max UDMA/100
[    1.850931] ata2.00: configured for UDMA/100
[    1.871041] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6L-C ZHCH PQ: 0 ANSI: 5
[    1.876599] sr0: scsi3-mmc drive: 40x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.876604] Uniform CD-ROM driver Revision: 3.20
[    1.876765] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.876835] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.965124] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    1.969994] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    1.974874] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    1.979748] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    1.980101] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    1.980216] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    1.980333] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    1.980491] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    1.984357] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    1.985232] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    1.986106] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    1.986981] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    2.040023] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    2.220023] ata3: SATA link down (SStatus 0 SControl 300)
[    2.264378] usbcore: registered new interface driver hiddev
[    2.278901] input: CHICONY HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2
[    2.278982] generic-usb 0003:04F2:0841.0001: input,hidraw0: USB HID v1.11 Keyboard [CHICONY HP USB Multimedia Keyboard] on usb-0000:00:1a.0-2/input0
[    2.303953] input: CHICONY HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3
[    2.304037] generic-usb 0003:04F2:0841.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [CHICONY HP USB Multimedia Keyboard] on usb-0000:00:1a.0-2/input1
[    2.304049] usbcore: registered new interface driver usbhid
[    2.304050] usbhid: USB HID core driver
[    2.340620] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[    2.341038] sd 7:0:0:0: Attached scsi generic sg6 type 0
[    2.341733] sd 7:0:0:0: [sdf] 7905279 512-byte logical blocks: (4.04 GB/3.76 GiB)
[    2.342217] sd 7:0:0:0: [sdf] Write Protect is off
[    2.342222] sd 7:0:0:0: [sdf] Mode Sense: 45 00 00 08
[    2.342227] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    2.343968] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    2.343976]  sdf: sdf1
[    2.346210] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    2.346214] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[    2.500014] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.590024] ata4: SATA link down (SStatus 0 SControl 300)
[    2.698195] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input4
[    2.698287] generic-usb 0003:046D:C062.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.1-1/input0
[    2.960023] ata5: SATA link down (SStatus 0 SControl 300)
[    3.330020] ata6: SATA link down (SStatus 0 SControl 300)
[    4.241198] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   14.143404] udev[376]: starting version 163
[   14.204499] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   14.205534] Adding 11137020k swap on /dev/sda8.  Priority:-1 extents:1 across:11137020k 
[   14.205556] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   14.252317] lp: driver loaded but no devices found
[   14.407764] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.444386] type=1400 audit(1288232939.441:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=613 comm="apparmor_parser"
[   14.444941] type=1400 audit(1288232939.441:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=613 comm="apparmor_parser"
[   14.445241] type=1400 audit(1288232939.441:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=613 comm="apparmor_parser"
[   14.471579] [drm] Initialized drm 1.1.0 20060810
[   14.502221] cfg80211: Calling CRDA to update world regulatory domain
[   14.536378] cfg80211: World regulatory domain updated:
[   14.536382]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.536384]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.536386]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.536389]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.536391]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.536393]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.545385] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.545390] i915 0000:00:02.0: setting latency timer to 64
[   14.597367] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   14.597372] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   14.597455]   alloc irq_desc for 44 on node -1
[   14.597457]   alloc kstat_irqs on node -1
[   14.597466] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   14.597477] [drm] set up 7M of stolen space
[   14.597851] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.598163] [drm] initialized overlay support
[   14.640349] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   14.824599] phy0: Selected rate control algorithm 'minstrel'
[   14.825106] Registered led device: rt73usb-phy0::radio
[   14.825121] Registered led device: rt73usb-phy0::assoc
[   14.825138] Registered led device: rt73usb-phy0::quality
[   14.825700] usbcore: registered new interface driver rt73usb
[   14.843662] Console: switching to colour frame buffer device 128x48
[   14.845700] fb0: inteldrmfb frame buffer device
[   14.845702] drm: registered panic notifier
[   14.845705] Slow work thread pool: Starting up
[   14.845869] Slow work thread pool: Ready
[   14.845921] No ACPI video bus found
[   14.845987] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.846203]   alloc irq_desc for 22 on node -1
[   14.846206]   alloc kstat_irqs on node -1
[   14.846214] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.846261]   alloc irq_desc for 45 on node -1
[   14.846263]   alloc kstat_irqs on node -1
[   14.846273] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   14.846301] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.941208] hda_codec: ALC1200: SKU not ready 0x411111f0
[   14.941307] hda_codec: ALC1200: BIOS auto-probing.
[   15.289488] type=1400 audit(1288232940.281:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=953 comm="apparmor_parser"
[   15.289539] type=1400 audit(1288232940.281:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=954 comm="apparmor_parser"
[   15.290088] type=1400 audit(1288232940.291:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=954 comm="apparmor_parser"
[   15.290393] type=1400 audit(1288232940.291:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=954 comm="apparmor_parser"
[   15.292691] type=1400 audit(1288232940.291:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=955 comm="apparmor_parser"
[   15.293195] type=1400 audit(1288232940.291:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=957 comm="apparmor_parser"
[   15.294705] type=1400 audit(1288232940.291:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=958 comm="apparmor_parser"
[   15.729920] r8169 0000:02:00.0: eth0: link down
[   15.730806] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.872589] ADDRCONF(NETDEV_UP): wlan0: link is not ready



```




dmidecode```


# dmidecode 2.9
SMBIOS 2.5 present.
54 structures occupying 4091 bytes.
Table at 0x000F06E0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 5.39   
	Release Date: 05/06/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.14

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: HP-Pavilion
	Product Name: NY428AA-ABA p6110f
	Version:  
	Serial Number: 3CR9240WKV
	UUID: C848E048-A356-DE11-94D1-61BE3E554DF6
	Wake-up Type: Power Switch
	SKU Number: NY428AA#ABA
	Family: 103C_53316J

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: PEGATRON CORPORATION
	Product Name: Benicia
	Version: 1.01
	Serial Number: MS1C96R50202518
	Asset Tag:                                 
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:                                 
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: Hewlett-Packard
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: DM0001
	Asset Tag: Asset-1234567890
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Other
	Manufacturer: Intel            
	ID: 7A 06 01 00 FF FB EB BF
	Version: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz     
	Voltage: 1.3 V
	External Clock: 800 MHz
	Max Speed: 2600 MHz
	Current Speed: 2600 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number:                                 
	Asset Tag:                                 
	Part Number:                                 
	Characteristics: None

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: Other

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: Other

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: 1394
	External Connector Type: IEEE 1394
	Port Type: Firewire (IEEE P1394)

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9A1
	Internal Connector Type: None
	External Reference Designator: Video Out
	External Connector Type: DB-15 female
	Port Type: Video Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB3
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB4
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: None

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - SATA1
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J2 - SATA2
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J3 - SATA3
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J4 - SATA4
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J5 - SATA5
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J6 - SATA6
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H1 - FRONT PNL
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - SYSTEM FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FNT USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - MAIN POWER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001F, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI-E x16
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0020, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI-E x1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0021, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI-E x1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 2
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 3
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0023, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:                                  

Handle 0x0024, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description:  Intel(R) HD Audio

Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description:                                  

Handle 0x0026, DMI type 11, 5 bytes
OEM Strings
	String 1: bid=93NAv6PrA2;PROD_MSWORKS;SFCHK;DLED;IS.N60d;ACPwrFail=Off;Cha
	String 2: n=Retail;CPUFan=On;DVDRW;LegacyFloppy=No;TVout=NTSC;PCBRAND=Pavi
	String 3: lion;OS=MSV;LScribe;DVDP_STD;Vos.P;PROD_MSOFFHST;FPA=HM;C_VEN2;R
	String 4: MCO;CDS_D;SW_Main;MSC-3-100-10;.QH;##HPCPC=00000000<900000060200
	String 5: 00000420000253514130040000010001000;5;:0665<;85>18>1<2=1:<55>?4;
	String 6: ;=?=19:<8494;>:8011<=31953=?76?>378139;594701:=;34:;55;9128<7937
	String 7: ==0<722<:<1:2489>:088=6:?1;2>8=8>12691>>286:9?;4454>3<3>89909>=7
	String 8: 38375;02951<;>=??2?70>75;04<815:33<20846?312127;?24876>7488457<0
	String 9: ;0?39>9;?407;8;8;09>=;==>231>;?456:100000006;0000000000200084051
	String 10: 5?454=435<49434=23405347594>444?47535020000000000000000000000000
	String 11: 000000000000000?24?41954<8?4243:463542:9034;??09<31;8951=>:><6>3
	String 12: 291=35:7;:7?<0;=973478<4:062629<>53103<<=4651<3499:7?769::98;357
	String 13: 697=:3483>07=6;>1<1?<>7<817?5586>79?5:5?19<87:>=6507148017=835>5
	String 14: 52096;714776===1=59:5:9;7?16>;910;6<?>4?;=21?;7975:6660><>729>:9
	String 15: <98<5<=991>7?7>
	String 16:                                                                 
	String 17:                                                                 
	String 18:                                                                 
	String 19:                                                                 
	String 20:                                                                 
	String 21:                                                                 
	String 22:                                                                 
	String 23:                                                                 
	String 24:                                                                 
	String 25:                                                                 
	String 26:                                                                 
	String 27:                                                                 
	String 28:                                                                 
	String 29:                                                                 
	String 30:                                                                 
	String 31:                                                                 
	String 32:                                                                 

Handle 0x0027, DMI type 12, 5 bytes
System Configuration Options
	Option 1: 0123456789ABCDEF

Handle 0x0028, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x0029, DMI type 15, 35 bytes
System Event Log
	Area Length: 4 bytes
	Header Start Offset: 0x0000
	Header Length: 2 bytes
	Data Start Offset: 0x0002
	Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
	Access Address: Index 0x046A, Data 0x046C
	Status: Invalid, Not Full
	Change Token: 0x00000000
	Header Format: No Header
	Supported Log Type Descriptors: 6
	Descriptor 1: End of log
	Data Format 1: OEM-specific
	Descriptor 2: End of log
	Data Format 2: OEM-specific
	Descriptor 3: End of log
	Data Format 3: OEM-specific
	Descriptor 4: End of log
	Data Format 4: OEM-specific
	Descriptor 5: End of log
	Data Format 5: OEM-specific
	Descriptor 6: End of log
	Data Format 6: OEM-specific

Handle 0x002A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002B, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0017FFFFFFF
	Range Size: 6 GB
	Physical Array Handle: 0x002A
	Partition Width: 0

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: CE00000000000000
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: M3 78T2863EHS-CF7 

Handle 0x002D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x002C
	Memory Array Mapped Address Handle: 0x002B
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: CE00000000000000
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: M3 78T5663QZ3-CF7 

Handle 0x002F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00040000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x002E
	Memory Array Mapped Address Handle: 0x002B
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0030, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: CE00000000000000
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: M3 78T2863EHS-CF7 

Handle 0x0031, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x000C0000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0030
	Memory Array Mapped Address Handle: 0x002B
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0032, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: CE00000000000000
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: M3 78T5663QZ3-CF7 

Handle 0x0033, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00100000000
	Ending Address: 0x0017FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0032
	Memory Array Mapped Address Handle: 0x002B
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0034, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0035, DMI type 127, 4 bytes
End Of Table



```





lspci -vvnn

```
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at fe900000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at c080 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fe800000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at c400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at c480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe9fec00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: cf700000-cf8fffff
	Prefetchable memory behind bridge: 00000000cf900000-00000000cfafffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at c800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at c880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at cc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fe9ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92) (prog-if 01 [Subtractive decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: fea00000-feafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 43
	Region 0: I/O ports at d880 [size=8]
	Region 1: I/O ports at d800 [size=4]
	Region 2: I/O ports at d480 [size=8]
	Region 3: I/O ports at d400 [size=4]
	Region 4: I/O ports at d080 [size=32]
	Region 5: Memory at fe9ff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 10
	Region 0: Memory at fe9ffc00 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a6f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 42
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at fdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169
```




find /etc/modprobe.* -name \*.conf | xargs cat```


options iwlagn 11n_disable=1
# Uncomment these entries in order to blacklist unwanted modem drivers
# blacklist snd-atiixp-modem
# blacklist snd-intel8x0m
# blacklist snd-via82xx-modem
blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb-midi
blacklist radeon
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist visor
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

# Watchdog drivers should not be loaded automatically, but only if a
# watchdog daemon is installed.
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist booke_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i6300esb
blacklist i8xx_tco
blacklist ib700wdt
blacklist ibmasr
blacklist indydog
blacklist iTCO_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist ixp2000_wdt
blacklist ixp4xx_wdt
blacklist machzwd
blacklist mixcomwd
blacklist mpc8xx_wdt
blacklist mpcore_wdt
blacklist mv64x60_wdt
blacklist pc87413_wdt
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist s3c2410_wdt
blacklist sa1100_wdt
blacklist sbc60xxwdt
blacklist sbc7240_wdt
blacklist sb8360
blacklist sc1200wdt
blacklist sc520_wdt
blacklist sch311_wdt
blacklist scx200_wdt
blacklist shwdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist twl4030_wdt
blacklist w83627hf_wdt
blacklist w83697hf_wdt
blacklist w83697ug_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci
blacklist wm8350_wdt
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2


```


cat /etc/modules```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


```

---

### Post by Alan|Cvette on 2010-10-28
This is crazy :)

---

### Post by ubunterooster on 2010-10-28
> **Alan|Cvette said:**
> This is crazy :)
Agreed. And the site that has the Linux drivers just goes in a loop: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=2843&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=2843&lang=eng)

---

### Post by ubunterooster on 2010-10-28
Okay, maybe good news, maybe not. The intel site has a link to a driver for it but warns:              [COLOR=DarkOrange]Compiling and/or upgrading graphics drivers in Linux is a complex and error-prone task. [Here]("http://intellinuxgraphics.org/install.html") is a user guide for how to build the driver from scratch. If you are not experienced doing this, we recommend that you get precompiled packages from one of the many Linux distributions.[/COLOR]         

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by Alan|Cvette on 2010-10-28
Cheers mate! I will check these out tomorrow. I'm off to get some sleep now. Thanks again everyone for the help!

---

### Post by Alan|Cvette on 2010-10-28
Quick update:

I can't try those at the moment, but I will tonight when I get back from work. I DID however test the exact same game(s) on Ubuntu Netbook Edition and they worked flawlessly. I have a feeling that narrows it down bunches.

---

### Post by ubunterooster on 2010-10-28
UNE is not really gnome and uses a different 3D manager

---

### Post by Alan|Cvette on 2010-11-05
Hey everyone! How goes it? Sorry for having not replied recently, I had to move into a new apartment over the weekend. Comcast was a royal pain to get working!

I have some sad news, I suppose it could be good news too. I wound up trying a few extra distro's I had on my PC, namely Kubuntu, OpenSUSE, Linux Mint 9 KDE. 

-Kubuntu I had to abandon as the WiFi was painfully slow >_<
-OpenSUSE was a pain to get on the USB, and even when I finally did it was being a little buggah to install.
-Linux Mint 9 KDE was very nice and easy to use, but again, slow WiFi.

I had a butt load of partitions in the end, and decided to wipe it clean and start fresh with only my favorite, Ubuntu. So I did, and upon booting up I installed the applications that I WAS having trouble with before. And vola! They worked perfectly!

I thank you all for the hard work, time, and effort you put into trying to resolve this issue. I am unsure how to mark this, solved, unsolved, settled?

Cheers my friends :)

---

