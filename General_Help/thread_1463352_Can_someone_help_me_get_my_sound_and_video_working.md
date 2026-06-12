---
title: "Can someone help me get my sound and video working? Its a sony."
date: 2010-04-26
forum: General Help
---

### Post by schwabdale on 2010-04-26
Hello,
I have a Sony Vaio with the I3 Processor. I do not have any drivers installed. 
The video works, but I am sure its not using drivers. There is no sound.
Please help.

---

### Post by Hugh Mulqueen on 2010-04-26
What version of ubuntu are you using???

For the sound just click on the sound icon on the top right hand side and left click "sound preferences" and click on the volume to adjust the sound...

---

### Post by lidex on 2010-04-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by schwabdale on 2010-04-27
~$ uname -a
Linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
~$ head -n 1 /proc/asound/card*/codec#*^C
~$

---

### Post by schwabdale on 2010-04-27
Any ideas?

---

### Post by dubble on 2010-04-27
have you tried unmuting it using the command sudo alsamixer ?

---

### Post by schwabdale on 2010-04-27
I'm not sure how to unmute it running sudo alsamixer... but, Its not muted when I click on the speaker 
icon, and all of the bars are up when I run sudo alsamixer.

---

### Post by lidex on 2010-04-27
Please don't run alsamixer with sudo. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=vaio  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by schwabdale on 2010-04-28
> **lidex said:**
> Please don't run alsamixer with sudo. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=vaio  
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

I did this, but when I run alsamixer in a terminal I get ... no such file or directory error

---

### Post by lidex on 2010-04-28
> **schwabdale said:**
> I did this, but when I run alsamixer in a terminal I get ... no such file or directory error

Probably because you used sudo before. You should be able to run it without being root.

---

### Post by schwabdale on 2010-04-29
Whether I run it as Sudo or just type in "alsamixer" I get the same response. 
Do I need to reinstall Alsamixer? If so, how do I do that?

---

### Post by lidex on 2010-04-29
Run this command in a terminal:
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa libao2
```

Reboot!

---

### Post by schwabdale on 2010-04-30
> **lidex said:**
> Run this command in a terminal:
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa libao2
```Reboot!

Still get the same error.

---

### Post by schwabdale on 2010-05-03
Any ideas? Can someone please help me solve this problem.

---

### Post by jalirious on 2010-05-03
By default, the alsa modules are installed without any options. Unfortunately, the intel-hda drivers now require options to specify which hardware versions to support, and ubuntu doesn't specify any of those options when compiling the alsa modules. Here's a way to fix it on your local machine until the package is fixed.

Add a line like this to /etc/alsa/alsa-source.conf:
ALSA_CARD_OPTIONS="hda-codec-<your hardware>"

Here are the possible options from the configure scripts:
hda-codec-realtek, hda-codec-analog, hda-codec-sigmatel, hda-codec-via, hda-codec-atihdmi, hda-codec-conexant, hda-codec-cmedia, hda-codec-si3054, hda-generic

Once that's done, run the following commands:
sudo aptitude install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

### Post by schwabdale on 2010-05-04
> **jalirious said:**
> By default, the alsa modules are installed without any options. Unfortunately, the intel-hda drivers now require options to specify which hardware versions to support, and ubuntu doesn't specify any of those options when compiling the alsa modules. Here's a way to fix it on your local machine until the package is fixed.

Add a line like this to /etc/alsa/alsa-source.conf:
ALSA_CARD_OPTIONS="hda-codec-<your hardware>"

Here are the possible options from the configure scripts:
hda-codec-realtek, hda-codec-analog, hda-codec-sigmatel, hda-codec-via, hda-codec-atihdmi, hda-codec-conexant, hda-codec-cmedia, hda-codec-si3054, hda-generic

Once that's done, run the following commands:
sudo aptitude install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Here is a link to the Laptop I have. 
[http://www.bbspot.com/reviews/sony-vaio-vpc-eb11fxt-laptop-with-core-i3-review](http://www.bbspot.com/reviews/sony-vaio-vpc-eb11fxt-laptop-with-core-i3-review)

Do I add the line ALSA_CARD_OPTIONS=hda-codec-intel? Just like that?

---

### Post by schwabdale on 2010-05-10
Is it safe to assume its not possible on this laptop?

---

### Post by lidex on 2010-05-11
It should work. I think you borked something in your install. An OS re-install may be your best option.

---

### Post by ricardo.gloe on 2010-05-11
I didn't have sound on my Sony Vaio after installing Lucid. Tried everything described on this thread and nothing.

Only solution was installing newer kernel from:

[HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/[/HTML]  

I installed 2.6.33.3 - lucid, from apr, 27th. Sound and horizontal scrolling on mousepad worked after install.

---

### Post by schwabdale on 2010-05-14
> **ricardo.gloe said:**
> I didn't have sound on my Sony Vaio after installing Lucid. Tried everything described on this thread and nothing.

Only solution was installing newer kernel from:

[HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/[/HTML]I installed 2.6.33.3 - lucid, from apr, 27th. Sound and horizontal scrolling on mousepad worked after install.
I Tried this and it did not work. Any other ideas?

---

### Post by schwabdale on 2010-05-18
I installed the Kernel from April 27. 2.6.33 and my mouse pad scroller is working. 
This is an improvement. But, the sound is still not working. When I check the built in Mic,
it looks like its picking up my voice. I don't get it.

---

### Post by schwabdale on 2010-05-23
Update, I noticed if I plug in a headset, I get sound real low. Any more ideas?

---

### Post by lidex on 2010-05-23
Change the option in alsa-base.conf. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=sony 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Other options here:
```
options snd-hda-intel model=auto
options snd-hda-intel model=basic
options snd-hda-intel model=toshiba-s06
```

Use only one at a time and reboot to see changes.

---

### Post by schwabdale on 2010-05-24
Still no sound. One thing I noticed though, when I click on the option to select the sound card, I cannot type in sony, or select sony. 

Should I be able to do that?

---

