---
title: "Sound not working on 10.04 LTS"
date: 2011-02-25
forum: General Help
---

### Post by ardit ,A, on 2011-02-25
Hello I installed last night Ubuntu 10.04 LTS (I had XP) and now sound is not working! 
WHAT TO DO?

My sound card: **VIA Audio HD**

In volume manager is sound and I can make volume 1-100 but not working on youtube or any song or anything.

PLEASE HELP!

---

### Post by wiggly81 on 2011-02-25
please check for Additional Drivers

>System > Administration > Additional Drivers

---

### Post by ghostborg on 2011-02-25
Also Check your sound preferences. On my system left click on the sound icon on the top panel and choose "Sound Preferences"
Look at the Hardware and Output tabs to make sure the sound device your speakers are hooked to is selected. For example on my system I can choose between Internal Audio Analog Stereo and Digital Stereo(HDMI) .

---

### Post by ardit ,A, on 2011-02-25
> **wiggly81 said:**
> please check for Additional Drivers

>System > Administration > Additional Drivers

nothing appeared :S

> **ghostborg said:**
> Also Check your sound preferences. On my  system left click on the sound icon on the top panel and choose "Sound  Preferences"
Look at the Hardware and Output tabs to make sure the sound device your  speakers are hooked to is selected. For example on my system I can  choose between Internal Audio Analog Stereo and Digital Stereo(HDMI)  .

in Hardware tab is nothing but was **VIA HD Audio Controller **and something like this

---

### Post by ardit ,A, on 2011-02-25
please help

---

### Post by Frogs Hair on 2011-02-25
Here is a basic trouble shooting guide. [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ngrieb on 2011-02-25
Try using the alsamixer to check your sound output. Open a terminal and type alsamixer. You should get a graphic equalizer. If the sound level for your speakers or headphones is not turned up, simply press the up arrow key. If there is a small MM at the bottom the channel is muted. 

If this is not the problem, then try and install the alsa-backports. If you are just moving over from windows and feel more comfy with the GUI, then go to System->Admin->Software Sources, and on the updates tab make sure the Unsupported (backports) box is checked. Then go to System->Admin->Synaptic Package Manager and download the correct backports module for your kernel. If you have no idea what I'm talking about post a reply. 

Also it might be helpful if you gave us some more information on your computer, what manufacturer, model etc. Is your sound card integrated, etc... Hope this helps. The guide link above should also help.

---

### Post by ardit ,A, on 2011-02-25
> **ngrieb said:**
> Try using the alsamixer to check your sound output. Open a terminal and type alsamixer. You should get a graphic equalizer. If the sound level for your speakers or headphones is not turned up, simply press the up arrow key. If there is a small MM at the bottom the channel is muted. 

If this is not the problem, then try and install the alsa-backports. If you are just moving over from windows and feel more comfy with the GUI, then go to System->Admin->Software Sources, and on the updates tab make sure the Unsupported (backports) box is checked. Then go to System->Admin->Synaptic Package Manager and download the correct backports module for your kernel. If you have no idea what I'm talking about post a reply. 

Also it might be helpful if you gave us some more information on your computer, what manufacturer, model etc. Is your sound card integrated, etc... Hope this helps. The guide link above should also help.

**I did all on this but, i dont understand the 2nd step "**Then go to System->Admin->Synaptic Package Manager and download  the correct backports module for your kernel. If you have no idea what  I'm talking about post a reply."

---

### Post by ardit ,A, on 2011-02-25
any other help please im waiting :(

---

### Post by ghostborg on 2011-02-25
I searched Ubuntu 10.04 VIA HD Audio Controller 
and found this:
[http://answerpot.com/showthread.php?1667578-+VT1708/A++(VIA+High+Definition+Audio+Controller)+had+sound+in+10.04,+not+10.10]("http://answerpot.com/showthread.php?1667578-+VT1708/A++(VIA+High+Definition+Audio+Controller)+had+sound+in+10.04,+not+10.10")
Strangely this is related to bug#536699. Changing, in the BIOS, the
graphics aperture size from 128MB to 256MB as suggested in that bug's comments solves both that issue and this.

Although it looked like people had sound in 10.04 and no sound in 10.10 but this was from last October and it's possible updates may have done this to you too.
Well it's worth a try.

---

### Post by ardit ,A, on 2011-02-25
> **ghostborg said:**
> I searched Ubuntu 10.04 VIA HD Audio Controller 
and found this:
[http://answerpot.com/showthread.php?1667578-+VT1708/A++(VIA+High+Definition+Audio+Controller)+had+sound+in+10.04,+not+10.10]("http://answerpot.com/showthread.php?1667578-+VT1708/A++%28VIA+High+Definition+Audio+Controller%29+had+sound+in+10.04,+not+10.10")
Strangely this is related to bug#536699. Changing, in the BIOS, the
graphics aperture size from 128MB to 256MB as suggested in that bug's comments solves both that issue and this.

Although it looked like people had sound in 10.04 and no sound in 10.10 but this was from last October and it's possible updates may have done this to you too.
Well it's worth a try.

nope I dont understand :S
if I dont reslove this problem I'll turn to XP :( I dont have another chance.
FOR ME ubuntu without sound sux.

---

### Post by cbennett a7xftw on 2011-02-25
try going to sound properties(the sound icon in the top right) then there is another tap which shows all these different sound options you can use.

---

### Post by ardit ,A, on 2011-02-25
please help :( to make sound work in my F***ING ubuntu.

---

### Post by Script Warlock on 2011-02-25
can you try in the terminal

sudo alsa force-reload

and test it with 

speaker-test -c 2 -t wav

---

### Post by Nickedynick on 2011-02-25
Not sure if it's related, but I'm having a similar issue with the same sound card here: [http://ubuntuforums.org/showthread.php?t=1695189](http://ubuntuforums.org/showthread.php?t=1695189)

If anything crops up on that thread I'll post it back here.

---

### Post by ardit ,A, on 2011-02-25
> **Script Warlock said:**
> can you try in the terminal

sudo alsa force-reload

nope I can't hear anything but when I tried this at sound preferences refreshed my driver at HARDWARE tab :D

---

### Post by Script Warlock on 2011-02-25
> **ardit ,A, said:**
> nope I can't hear anything but when I tried this at sound preferences refreshed my driver at HARDWARE tab :D

is this a pci or built-in soundcard..

try this also if you can hear anything

speaker-test -c 2 -t wav

---

### Post by ardit ,A, on 2011-02-25
> **Script Warlock said:**
> is this a pci or built-in soundcard..

try this also if you can hear anything

speaker-test -c 2 -t wav

Here are screenshots

Screenshot 1 [[IMG]http://img820.imageshack.us/img820/6939/screenshot1en.png[/IMG]](http://img820.imageshack.us/i/screenshot1en.png/)

Screenshot 2 [[IMG]http://img822.imageshack.us/img822/9052/screenshot2co.png[/IMG]](http://img822.imageshack.us/i/screenshot2co.png/)

Screenshot 3 [[IMG]http://img15.imageshack.us/img15/2296/screenshot3vv.png[/IMG]](http://img15.imageshack.us/i/screenshot3vv.png/)

Screenshot 4 [[IMG]http://img69.imageshack.us/img69/4356/screenshot4vn.png[/IMG]](http://img69.imageshack.us/i/screenshot4vn.png/)

---

### Post by ardit ,A, on 2011-02-25
> **Script Warlock said:**
> is this a pci or built-in soundcard..

try this also if you can hear anything

speaker-test -c 2 -t wav

X@X:~$ speaker-test -c 2 -t wav

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 5.239622
 0 - Front Left
 1 - Front Right
Time per period = 5.220883
 0 - Front Left
 1 - Front Right
Time per period = 5.221067
 0 - Front Left
 1 - Front Right
Time per period = 5.227744
 0 - Front Left
 1 - Front Right
Time per period = 5.233971
 0 - Front Left

 1 - Front Right
Time per period = 5.222928
 0 - Front Left
 1 - Front Right
Time per period = 5.227084
 0 - Front Left
 1 - Front Right

---

### Post by ardit ,A, on 2011-02-25
any help :P

---

### Post by Nickedynick on 2011-02-25
Did you actually hear anything while the test was running?

---

### Post by ardit ,A, on 2011-02-25
> **Nickedynick said:**
> Did you actually hear anything while the test was running?


nope :(

---

