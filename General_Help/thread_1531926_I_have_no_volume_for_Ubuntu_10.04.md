---
title: "I have no volume for Ubuntu 10.04"
date: 2010-07-15
forum: General Help
---

### Post by Scottty on 2010-07-15
Hello

I have installed Ubuntu 10.04 and I have no volume for anything. I have changed from running Ubuntu 10.04 in virtualbox on Windows XP. I now have a stand alone version of Ubuntu 10.04

When I ran it on Windows XP in Virtualbox I was able to configure the sound with very little difficulty but now running on its own I'm having no luck.

Can you tell me how to get sound? and would like to learn why it isn't configured automatically like in Windows.

Thank you,
Scott

---

### Post by Lucasimo on 2010-07-15
Hi,

This can be fixed in 10.04

There are several known issues with sound not working or sometimes working etc etc.

Search the forums and you will find a solution...they are really good and have taught me quite a lot about Ubuntu.

First check SYSTEM> PREFERENCES> SOUND and see what you get...

Also you could install GNOME alsa mixer using Synaptic Package Manager.

Some sound problems can be solved by removing pulseaudio (this worked for me) but this should only really be done as a last resort....

Let us know how you get on...

Not everything is configured automatically in Ubuntu. Most things are, some things require a little bit of fine tuning :)


Lucasimo

---

### Post by Scottty on 2010-07-15
Hi Lucasimo

First I went to SYSTEM> PREFERENCES> SOUND
and this is what was in there
```

Sound Effects Tab
Sound theme: Ubuntu

Hardware Tab
Internal Audio Analog Stereo Input

Input Tab
Input volume: Unamplified 100%
Connector: Microphone 1

Output Tab
Dummy Output Stereo

```

GNOME alsa mixer is already installed

I then tried removing pulseaudio and still nothing happened. I did a reboot of the system and still no sound.

Thanks
Scott

---

### Post by Scottty on 2010-07-20
Can someone please help. I have tried and tried to enable sound on my Ubuntu 10.04. I have gone to many websites and followed their directions on how to enable sound but nothing has worked. Would it be better to go to an earlier version of ubuntu? If it is a better idea what version should I get? I really want 10.04 to work and be my main O/S. I don't want to have to go back to Windows.

Thank you

Scott

---

### Post by lidex on 2010-07-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Scottty on 2010-07-20
Thank you Lidex

uname -a```
 Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

aplay -l  ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
dpkg -l | grep "alsa" ```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

```
head -n 1 /proc/asound/card*/codec#*  I kept getting head: l: invalid number of lines

I have an ASUS FSB O.C 1600 P5KPL-CM

---

### Post by lidex on 2010-07-21
That's a 1 not the letter l (lowercase L).
Try this. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Scottty on 2010-07-21
Hello Lidex

I did exactly what you sais to do
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

Entered this on the bottom line
options snd-hda-intel model=auto


```
I then started **alsamixer** in the terminal
I changed all the muted settings and now they all display 00 on the bottom of each bar graph. I also increased the volume for each to 100

I then pressed F6 to select the proper sound card, my choices were
```

-   (default)
0   HDA Intel
enter device name

```
I selected 0 HDA Intel and pressed ENTER

When I pressed F3 nothing happened
When I pressed F4 the capture levels were displayed with values of 100<>100

I didn't have to mute/unmute anything

I then went to System ->Preferences ->Sound and went to the hardware tab
It has displayed

```

Internal Audio
1 Output / 1 Input
Analog Stereo Duplex

```

I have rebooted 2 times and still no sound. 

Scott

---

### Post by lidex on 2010-07-21
Did you try the analog stereo duplex profile?
I think you would benefit from an alsa upgrade. Follow the link in my sig.

---

### Post by syntax-error on 2010-07-26
root@gr0undzer0:/# uname -a
```
Linux gr0undzer0 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
```

root@gr0undzer0:/# aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

root@gr0undzer0:/# head -n 1 /proc/asound/card*/codec#*
```
Codec: VIA VT1708B 8-Ch
```

My ALSA Info [http://www.alsa-project.org/db/?f=2d1ed23f65c83b3662cfa5fcc453b201fd60d68d](http://www.alsa-project.org/db/?f=2d1ed23f65c83b3662cfa5fcc453b201fd60d68d)
```

!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23
```

I've followed the guides on your sig, updated ALSA driver from 1.0.21 to 1.0.23 still I have no sound :(

Motherboard is Asus P5KPL-AM.

---

### Post by Scottty on 2010-07-26
Hello everyone

I could not get the sound for Ubuntu 10.04 to work so I was wondering where I could get 9.10 Karmic Koala and see if I can get the sound to work with it.

Thanks for help

Scott

---

### Post by lidex on 2010-07-26
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Scottty on 2010-07-26
Hi lidex 

I reinstalled Ubuntu 10.04 and guess what I had sound. I could hear the drums when the system started and heard other sounds once Ubuntu was up and running. Such as minimizing windows

Then I did the update for the system, there were about (250 to 350 updates) and then did a reboot and once again no sounds.

What am I doing wrong? Ubuntu worked better at 7.10

Scott

---

### Post by lidex on 2010-07-26
Recheck your mixer and audio preference settings as they tend to get reset. alsa will default to muted.

---

### Post by Scottty on 2010-07-26
> 
Recheck your mixer and audio preference settings as they tend to get reset. alsa will default to muted. 


Hi lidex
I followed all your directions
> 
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.



I worked with the alsa mixer. Although there was one thing muted it didn't correct the problem.

I also went through the sound preferences and there was nothing muted

Scott

---

### Post by lidex on 2010-07-26
Let me see the output of these commands please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

And this:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by Scottty on 2010-07-26
Here are the results
uname -a :
```

linux scott-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

```

aplay -l :
```

 **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

dpkg -l | grep "alsa"
```

ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                         0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

```

head -n 1 /proc/asound/card*/codec#*
```

Codec: VIA VT1708B 8-Ch

```

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

USER        PID ACCESS COMMAND
/dev/snd/controlC0:  scott      1346 F.... pulseaudio

```

dmesg | grep C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

[    8.316319] psmouse serio1: ID: 10 00 64
[    8.436663] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.436710] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.436811] usbcore: registered new interface driver hiddev

```

thanks for the help lidex

---

### Post by lidex on 2010-07-26
OK. Try post #7 again. If that doesn't work we can try some different models.

---

### Post by Scottty on 2010-07-26
I tried all the steps in Post #7 and still no sound. I would like to try some of the models you are suggesting.

Scott

---

### Post by lidex on 2010-07-26
Just replace what comes after the = with one of these at a time:
```
6stack-digout 
asus-mode3
lifebook 
```
For this delete the existing line and add both together:
```
options snd-hda-intel probe_mask=1
options snd-hda-intel enable=1 index=0 model=lenovo
```

You'll need to reboot for changes to become effective or maybe this will work:
```
sudo alsa force-reload
```

---

### Post by Scottty on 2010-07-26
> 
Just replace what comes after the = with one of these at a time:


Sorry I don't understand this line can you make it more clear.

Thanks
S

---

### Post by lidex on 2010-07-26
> **Scottty said:**
> Sorry I don't understand this line can you make it more clear.

Thanks
S
Yeah. The line you added to alsa-base.conf:
```
options snd-hda-intel model=auto
```
Change auto to one of the other options I gave. Save. Reboot.

---

### Post by Scottty on 2010-07-26
hi

I tried each one and rebooted after each and sound has not returned . Let me know if you think of anything else.

thanks
S

---

### Post by syntax-error on 2010-07-27
any suggestions about my query lidex?

---

### Post by lidex on 2010-07-27
Return alsa-base.conf entry to:
```
options snd-hda-intel model=auto
```
Did you try any other profiles in sound preferences>hardware - other that stereo duplex?
Also what is showing in output?

---

### Post by lidex on 2010-07-27
Can you post a screenshot of gnome-alsamixer, the default tab, and also the properties sheet displayed from 'Edit>Sound Card Properties'? We're looking for external amplifier (EAPD).

---

### Post by syntax-error on 2010-07-27
One quick update.

I reinstalled everything from scratch (ubuntu 10.04) guess what! I have sound! but, after i restart it goes away. Well after 3 installations I ended up not restarting nor installing anything and started to give you this update.

root@gr0undzer0:~# uname -a
```
Linux gr0undzer0 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```
root@gr0undzer0:~# aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
root@gr0undzer0:~# dpkg -l | grep "alsa"
```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
```
root@gr0undzer0:~# head -n 1 /proc/asound/card*/codec#*
```
Codec: VIA VT1708B 8-Ch
```

Here is the alsa info of my box [http://www.alsa-project.org/db/?f=8b8e2d4ae073c3ae7c66ab23108ddde580846ac5](http://www.alsa-project.org/db/?f=8b8e2d4ae073c3ae7c66ab23108ddde580846ac5)

Could somebody help? I mean how come the sound goes away after I restart? Well I thought that the nvidia driver was causing it but then it should not affect the audio right. audio -- graphics two different things.

During the installation by the way, Audio is also ok, I mean if you do a backspace on an empty textbox during the phase where you are suppose to enter your username I hear a sound.

---

### Post by Scottty on 2010-07-27
Here are the screenshots you asked for and some extras

[http://picasaweb.google.ca/sgtreanor/Ubuntu?feat=directlink](http://picasaweb.google.ca/sgtreanor/Ubuntu?feat=directlink)

Thanks
S

---

### Post by Scottty on 2010-07-27
I forgot one and I just added it.
It was for the Sound Card Properties

Please let me know if you need anything else.

Scott

---

### Post by lidex on 2010-07-27
Do you have any other profiles in the dropdown for profile?
Have you tried enabling 'independent headphone' in gnome-alsamixer? When I uncheck 'headphone' in my mixer it mutes system volume.
In sound preferences have you tried moving the output volume slider past 100%?
Try playing an audio file and open pavucontrol look to see if it shows as playing on 'playback' tab. Play around with the settings.

---

### Post by Scottty on 2010-07-28
Hi lidex
> 
Do you have any other profiles in the dropdown for profile?

I'm not sure where I find the dropdown for profile
> 
Have you tried enabling 'independent headphone' in gnome-alsamixer? When I uncheck 'headphone' in my mixer it mutes system volume.

I tried enabling independant headphone and then I exit from the gnome alsamixer. There is still no sound. Then I try going back into gnome alsamixer and the Independant headphone is unchecked. I tried this 3 or 4 times and each time the Independant Headphone unchecks itself.

> 
In sound preferences have you tried moving the output volume slider past 100%?

I tried but there is no sound still

> 
Try playing an audio file and open pavucontrol look to see if it shows as playing on 'playback' tab. Play around with the settings

Yes I loaded a Bon Jovi audio file in Rhythembox and it shows up on the Playback tab in the pavucontrol. I tried playing around with the settings but nothing worked.

Is there anything else I can try?

Scott

---

### Post by lidex on 2010-07-28
> I'm not sure where I find the dropdown for profile

Sound properties, the hardware tab.
[http://picasaweb.google.casgtreanorUbuntu?feat=directlink#5498622738339468466](http://picasaweb.google.casgtreanorUbuntu?feat=directlink#5498622738339468466)
Near the bottom. Click the down arrow next to analog stereo duplex

---

### Post by Scottty on 2010-07-28
Hi lidex

I tried changing the profiles there were about 10 profiles. I tried rebooting or logging in and out after trying each of them. 

Don't know what to do. I really wanted to work with blender.( Not that I need sound for it to use it.) but sound would be nice. What do you think I should do? Have others had this problem or is it just me?

Would it be better to install Karmic Koala and see if that works? I managed to get a copy downloaded. 

thank you for help
Scott

---

### Post by syntax-error on 2010-07-29
Anyone? :(

Its the same with ubuntu 9.10!

Fresh install has audio, after you restart it goes away for no apparent reason.

---

### Post by lidex on 2010-07-30
> **syntax-error said:**
> Anyone? :(

Its the same with ubuntu 9.10!

Fresh install has audio, after you restart it goes away for no apparent reason.

Makes no sense. Are you checking your mixer and volume controls to see if the reboot is muting sound? Sometime volume settings are not retained. That is another issue that can be addressed.

---

### Post by Scottty on 2010-07-30
That is exactly what is happening to me. I install and there is sound( I hear the drums), and once I come to the desktop I install all the updates. I then reboot and when I come back to the desktop there is no sound anymore.

Scott

---

### Post by lidex on 2010-07-30
Did you check your levels in alsamixer and also sound preferences? What about the profile on the hardware tab?

---

### Post by Scottty on 2010-07-30
Hi lidex

> 
Did you check your levels in alsamixer and also sound preferences? What about the profile on the hardware tab?


Actually yes i did. I worked on restoring sound for about 2 hours tonight. Nothing has yet worked. I found a few posts on others having sound issues with Ubuntu 10.04. I tried doing what they did and nothing happened.

I'm wondering though. I use headphones for sound. I'm left wondering if I had speakers would I be hearing sound. 

Scott

---

### Post by lidex on 2010-07-30
Hmm, really? What port are the headphones plugged into? Line/speaker/headphone?

---

### Post by Scottty on 2010-07-30
I have the headphones plugged into the green port on the front of the computer. I use the same port to listen to my radio station on windows xp at night. I don't know should I be plugged in to a different port on ubuntu. 

Scott

---

### Post by lidex on 2010-07-31
> **Scottty said:**
> I have the headphones plugged into the green port on the front of the computer. I use the same port to listen to my radio station on windows xp at night. I don't know should I be plugged in to a different port on ubuntu. 

Scott
I'm not sure. Isn't green the line out? That's what I have my speakers plugged into on the back of my pc. Have a look at your motherboard outs. There should be symbols for them and try the line and headphone to see if you get sound.

---

### Post by syntax-error on 2010-08-02
> **lidex said:**
> Makes no sense. Are you checking your mixer and volume controls to see if the reboot is muting sound? Sometime volume settings are not retained. That is another issue that can be addressed.

Volumes are set to max after reboot. Anyway thanks for trying to help.

---

### Post by lidex on 2010-08-02
> **syntax-error said:**
> Volumes are set to max after reboot. Anyway thanks for trying to help.

I may think too logically - if you have basic sound then pulseaudio may be the problem. Pulse Audio aka Defier of Logic. Click the pulse audio link in my sig and do 'Part A' then the troubleshooting section.

---

### Post by Scottty on 2010-08-12
I can't believe I solved my volume issue with Ubuntu 10.04
It was in fact an issue with my headphones. I always use the green port at the front of my CPU to listen to my favorite radio station every night.However there is a green colored port at the back of the CPU. So I tried it out. 

Guess what I have sound now. After all the work trying to figure what the problem was. Thank you for all your help and sorry for wasting your time.

I am so happy. YEEEEEEEEEEESSSSSSSSSSSSSSS!!!!

Scott

---

### Post by lidex on 2010-08-13
Do me a favor and mark this as solved so I don't inadvertently re-open it :?

---

