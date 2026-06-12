---
title: "No sound once again ... o.O"
date: 2011-03-03
forum: General Help
---

### Post by skillsforilz on 2011-03-03
Okay, so I have no sound on Ubuntu 10.04 ONCE AGAIN... I fixed it before with no help from my last post because no one ******* replied. This is so damn annoying. I know a code to reinstall my sound driver, but now it says "E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic"
If someone can please freaking help me, I'd greatly appreciate it. I've searched EVERYWHERE. I've been looking for hours. Nothing is working. Don't say, OH YOURE SOUND IS ON MUTE. Or like, add this to the end of this line. I've tried it all. Now for some reason, that package is missing and I can't find it anywhere. And in Synaptic, I can only find linux-alsa-driver-modules-2.6.32-28-generic. Not -29-generic.

Nice.... 48 views and not one single reply. This happens every time I post on these forums..

---

### Post by vkanth on 2011-03-06
> **skillsforilz said:**
> Okay, so I have no sound on Ubuntu 10.04 ONCE AGAIN... I fixed it before with no help from my last post because no one ******* replied. This is so damn annoying. I know a code to reinstall my sound driver, but now it says "E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic"
If someone can please freaking help me, I'd greatly appreciate it. I've searched EVERYWHERE. I've been looking for hours. Nothing is working. Don't say, OH YOURE SOUND IS ON MUTE. Or like, add this to the end of this line. I've tried it all. Now for some reason, that package is missing and I can't find it anywhere. And in Synaptic, I can only find linux-alsa-driver-modules-2.6.32-28-generic. Not -29-generic.

Nice.... 48 views and not one single reply. This happens every time I post on these forums..

Not sure if you've fixed the problem, but I had the exact same issue since I last performed an automatic update. After much struggle I ran the following command:

 [COLOR=RoyalBlue]sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2[/COLOR]

Found this in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) where they talk about all customizations being removed. Please use the above at your own risk. Worked for me, doesn't mean it will work for you. Good luck.

---

### Post by Yellow Pasque on 2011-03-06
> **skillsforilz said:**
>  but now it says E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic
...because you're using a different kernel version now. Just having a "code" doesn't help much if you have no idea what it's actually doing. ;)

---

### Post by waffelball on 2011-03-06
Same problem for me.

In lucid the kernel was recently updated to version 2.6.32-29. I suppose you are also using the ppa of ubuntu-audio-dev, just as suggested here [http://ubuntuforums.org/showthread.php?t=1668173](http://ubuntuforums.org/showthread.php?t=1668173) . Up to now the modules on the ppa are still using the kernel version  2.6.32-28, that's why pulse is not working for you (and me).

I guess that the modules on the ppa are updated within the next days. Until then you can select the old kernel 2.6.32-28 at start up and everything should work fine (press shift+ESC before you see the "ubuntu"-sign to enter the boot loader grub and select the kernel image).

---

### Post by brian_hammerhead on 2011-03-12
I also am getting the error: 

[FONT=Courier New]  E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic
[/FONT] 
Details follow.

I am fairly new to Ubuntu and Linux, but I am eager to learn and have  spent quite a bit of time researching my problem.  I would really  appreciate advice from someone more experienced than I.

I am running Mythbuntu 10.04 (Ubuntu 10.04.2 LTS, MythTV  0.23.201000617-1 s25362).  I had a stable setup about 6 months ago and  didn't do any updates so that everything would keep working - and it has  been super for the family.

I found myself needing to replace my video card.  After reading multiple  suggestions, I purchased the NVIDIA GT 430 with integrated audio over  HDMI.  Installing this card required me to update my NVIDIA video drivers so I  also updated my kernel (this may have been where I made my mistake).  I now have everything back to working  correctly except one thing - my system doesn't recognize the audio card  on the NVIDIA card.

Following the suggestion from lidex at [http://ubuntuforums.org/showthread.php?t=1668173](http://ubuntuforums.org/showthread.php?t=1668173), I did the following:

 [FONT=Courier New]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa[/FONT]
    [FONT=Courier New]sudo apt-get update[/FONT]
  [FONT=Courier New]sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/FONT]
  
Which returns the error:

[FONT=Courier New]  E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic
[/FONT]
As you can probably tell from the error message above, I am now  running the 2.6.32-29-generic kernel.  Apparently, the modules on the ppa are still using the kernel version 2.6.32-28 (thanks waffelball!).  

The GRUB2 startup-manager lists  the next previous version available on my system as 2.6.32-24-generic.  I tried to switch back  to the previous kernel, but then my video card wouldn't work and when I  tried to update the NVIDIA drivers (apt-get install nvidia-current) after booting into kernel 2.6.32-24, I received the message that I was already  on the latest version.

***My main goal** is to get the audio working this weekend if at all possible because of a specific need for my wife.*

However, if  waiting will save me from messing up my system requiring many hours or  work, I will wait for ppa.


_**Questions:**_

1) If I wait for ppa to be updated, how long do you think I will need to wait?  Hours, days, weeks, never?

2) Is there something I can do to get it working today or tomorrow?

What do you think of these options: 

[LIST]
[*]Compile the ALSA drivers myself for 2.6.32-29 (which I have never done before and would have to research how to do it).
[*]Install the 2.6.32-28 kernel (I only have used apt-get to get the latest kernel, so I don't know if this is possible).
[*]GRUB2 boot to the 2.6.32-24-generic kernel and keep trying to figure out how to get the NVIDIA drivers to install with that kernel.
[*]Use some other package that can handle the audio over HDMI features of the GT 430.
[/LIST]

As you can tell, I am treading water that is a bit over my head.  I really welcome the best directions back to shore so that I don't get even deeper.

Thanks!

---

### Post by Yellow Pasque on 2011-03-12
> Compile the ALSA drivers myself for 2.6.32-29 (which I have never done before and would have to research how to do it).
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by brian_hammerhead on 2011-03-12
Thanks for your fast response and for providing the helpful link.  The instructions look a bit daunting for a newbie like myself, but I am working through it so I "don't use this script unless [I] know what it's really doing".  ALSA is still quite a mystery to me.

If I do compile the ALSA drivers for myself, will I be able to still use apt-get to get ALSA driver updates in the future?

Do you know if there are plans to update the ALSA drivers to be compatible with the 2.6.32-29-generic kernel, and if so, when would you expect them to be available?

Thanks again!

---

### Post by brian_hammerhead on 2011-03-14
I did a bit of research and found this page:

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+packages]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa/+packages")

It appears to list the status of future builds.  I looked at it this evening and it appeared that the build that I needed was scheduled to run very soon.  Sure enough, an hour later it was complete.  I executed the commands:

[FONT=Courier New]sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/FONT]

  ... and magic happened!  No error message this time and the package was installed.  Note that the update command is required.

  I have rebooted and will start to see what configurations need to be made.  Thanks again to those that helped.

---

### Post by brian_hammerhead on 2011-03-15
For those that may find this information helpful in the future, here is what I did after getting the drivers installed:

Remember that I am using Mythbuntu 10.04 (Ubuntu and MythTV).  I just installed the NVidia GT 430 and want digital audio over HDMI as opposed to my previous DVI card (NVidia GeForce 8600 GT) and using my Coax digital output to my surround sound receiver.
[FONT=Verdana]
One neat thing to note is that the NVidia GT 430 will output both DVI and HDMI ***at the same time***!  This is particularly important for me since my MythTV box is in a wiring closet 80 feet away from my projector, so I have another monitor in the wiring closet so I can see what I am doing.[/FONT]  The wiring closet monitor uses the DVI output and the projector uses the HDMI output.  Also, on my previous card, I would experience "tearing" when using both DVI outputs. I see no such tearing when using both DVI and HDMI on the GT 430.  Nice.

 ```
a)    >aplay –L
    

hdmi:CARD=NVidia
      HDA NVidia, HDMI 0
      HDMI Audio Output
```[FONT=Courier New][FONT=&quot]

[/FONT][/FONT]```
> alsamixer

[F6] to change sound cards

1 HDA NVidia

```[FONT=Courier New][FONT=&quot]
[FONT=Verdana]Hmmm.  I have:[/FONT]

[/FONT][/FONT]```
S/PDIF
S/PDIF 1
S/PDIF 2
S/PDIF 3
```[FONT=Courier New][FONT=&quot]

[FONT=Verdana]Select each one and press 'M' to unmute.  ESC to save and exit.
Find hardware devices[/FONT]

[/FONT][/FONT]```
> cat /proc/asound/devices 
```[FONT=Courier New][FONT=&quot]

[FONT=Verdana]I now have four new “digital audio devices”[/FONT]

  [/FONT][/FONT]```
9: [ 1- 9]: digital audio playback
 10: [ 1- 8]: digital audio playback
 11: [ 1- 7]: digital audio playback
 12: [ 1- 3]: digital audio playback
```[FONT=Courier New][FONT=&quot]
[FONT=Verdana]
Now to test the output.  Note that to test the multichannel output I needed test files.  I downloaded mine from here:

[http://sverigesradio.se/sida/default.aspx?programid=2446](http://sverigesradio.se/sida/default.aspx?programid=2446)[/FONT]

[/FONT][/FONT]```
> aplay -D hw:1,9 ./test.wav
```[FONT=Courier New][FONT=&quot]
[FONT=Verdana]
IT WORKS![/FONT]

[/FONT][/FONT]```
> aplay -D hw:1,8 ./test.wav
```[FONT=Courier New][FONT=&quot]

[FONT=Verdana]Doesn’t work.[/FONT]

[/FONT][/FONT]```
> aplay -D hw:1,7 ./test.wav
```[FONT=Courier New][FONT=&quot]
[FONT=Verdana]
Doesn’t work.[/FONT]

[/FONT][/FONT]```
> aplay -D hw:1,3 ./test.wav
```[FONT=Courier New][FONT=&quot]

[FONT=Verdana]Doesn’t work.[/FONT]
[FONT=Verdana]
Test multi channel[/FONT]
[/FONT][/FONT]```
[FONT=Courier New]
> aplay -D hw:1,9 ./test-dd.wav
> aplay -D hw:1,9 ./test-mts.wav[/FONT]
```[FONT=Courier New][FONT=&quot]
[FONT=Verdana]
Both WORK![/FONT]

Test using card configuration[/FONT][/FONT]

```
aplay -D hdmi:CARD=NVidia ./test-dd.wav  
[FONT=Courier New][FONT=&quot;] 
[/FONT][/FONT]
```Doesn't work.  I am not sure why.  Perhaps my syntax isn't correct.  However, if I vary the name of the card (e.g. Nvidia) I get an error that it can't be found.  This leads me to believe that there is some kind of configuration file that isn't in place.  I am just learning about this stuff...

Let's try and set it up for MythTV anyway.

From the main frontend screen:

```
Utilities/Setup -> Setup -> General

Database Configuration 1/2
NEXT

Database Configuration 2/2
NEXT

Settings Access
NEXT

Audio System
(1)    Audio output device: ALSA:plughw:1,9
(2)    Speakers configuration: 5.1
(a)    Upconvert stereo to 5.1 suround: checked
(b)    Upmix: fastest
(c)    Digital output device: ASLA:plughw:1,9
(3)    Audio Process Capabilites
(a)    Dolby: Checked
(b)    DTS: Checked
NEXT

Audio Mixer
NEXT

General
NEXT

Media Monitor
NEXT

Program Exit
NEXT
    
Remote Control
FINISH
```IT WORKS!!

The audio still doesn't work inside my GNOME desktop yet.  It can see the audio card, but it only gives one option for stereo output - instead of multiple options for 5.1, etc.  And, no sound comes out when playing something through the desktop.

I still have to figure out why the desktop isn't working, but at least the MythTV box is working!  If anyone could post some tips for getting the sound to work correctly in the desktop, I (and others) would probably appreciate it.  Just keep it simple and complete.  I am a bit of a newbie here.

I hope this helps someone else.

---

### Post by brian_hammerhead on 2011-03-18
OK, it took me a couple of hours to figure it out, but the solution is simple once you know.  As I mentioned before, I had the following issue:
```
aplay -D hw:1,9 ./test.wav
```Worked.
```

aplay -D hdmi:CARD=NVidia ./test-dd.wav
```Didn't work.

It turns out that the configuration file that controls the device name is at: /usr/share/alsa/cards/HDA-Intel.conf

The relevant section for the hdmi: setting is:
```
HDA-Intel.pcm.hdmi.0 {
        @args [ CARD AES0 AES1 AES2 AES3 ]
        @args.CARD {
                type string
        }
        @args.AES0 {
                type integer
        }
        @args.AES1 {
                type integer
        }
        @args.AES2 {
                type integer
        }
        @args.AES3 {
                type integer
        }
        type hooks
        slave.pcm {
                type hw
                card $CARD
                device 3
        }
        hooks.0 {
                type ctl_elems
                hook_args [
                {
                        name "IEC958 Playback Default"
                        lock true
                        preserve true
                        value [ $AES0 $AES1 $AES2 $AES3 ]
                }
                {
                        name "IEC958 Playback Switch"
                        lock true
                        preserve true
                        value true
                }
                ]
        }
        hint.device 3
}
```Note the device number and the hint.device number.  The default is "3".  This is the PHYSICAL Codec ID.  In my example, this number is "9" because I have "hw:1,9".

I changed the numbers from 3 to 9 for these two parameters, rebooted, and voila!  Now when I type:

```

aplay -D hdmi:CARD=NVidia ./test-dd.wav
```IT WORKS!!

Not only that, but the sound in my GNOME Desktop also works!!

One weird thing is that the desktop sounds don't seem to work in the sound configuration GUI panel.  Ah well. This is good enough for me right now.

I hope that this helps someone else.

---

### Post by brian_hammerhead on 2011-03-18
Oh, by the way, this is an excellent article on HDMI on NVidia cards.

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

---

