---
title: "sound card issue dual install HDMI Nvidia + VIA Azalia"
date: 2011-02-09
forum: General Help
---

### Post by luishasbon on 2011-02-09
Dear developers, readers.

Well I just bought a new gpu (ECS GeForce gts 450). I installed ubuntu, i have a MSI Motherboard with VIA Azalia (via82xx) sound card. After installation, It resulted that i had no audio because of a very logical reason, Alsa recognized its default soundcard as the Nvidia HDMI output, I have no HDMI cables, so I was used to the VIA Azalia output from the motherboard, Alsamixer does not recognize my default VIA soundcard but lspci does detect the device as a sound device. Please, How do i use my via soundcard as default in order to audio playback nor the ndivia HDMI(now the soundcard detected by alsa is the NVidia HDMI(HDA)) ? 

I hope to be really clear.
Thank for your time!.

:guitar:

---

### Post by lidex on 2011-02-09
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by luishasbon on 2011-02-23
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

here is the link that alsa generated.

[http://www.alsa-project.org/db/?f=0c8a275f9ed9b7354abc451a3b9e03735094f2fc](http://www.alsa-project.org/db/?f=0c8a275f9ed9b7354abc451a3b9e03735094f2fc)

I don't know what else to do, thanks

---

### Post by lidex on 2011-03-01
> **luishasbon said:**
> here is the link that alsa generated.

[http://www.alsa-project.org/db/?f=0c8a275f9ed9b7354abc451a3b9e03735094f2fc](http://www.alsa-project.org/db/?f=0c8a275f9ed9b7354abc451a3b9e03735094f2fc)

I don't know what else to do, thanks

Looks like alsa doesn't even see the onboard card. Check your bios settings to make sure it's not disabled.

---

### Post by luishasbon on 2011-04-01
> **lidex said:**
> Looks like alsa doesn't even see the onboard card. Check your bios settings to make sure it's not disabled.

I checked the BIOS settings and the AZALIA sound driver is enabled. What I could think as a solution might be, downlaoding the snd82xx azalia driver, but first unistall the NVIDIA HDA sound driver but I don't know quite well how to achieve this. :S. Thanks!

---

### Post by lidex on 2011-04-01
> **luishasbon said:**
> I checked the BIOS settings and the AZALIA sound driver is enabled. What I could think as a solution might be, downlaoding the snd82xx azalia driver, but first unistall the NVIDIA HDA sound driver but I don't know quite well how to achieve this. :S. Thanks!

First let's update your system:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```
**Reboot**
Now try updating your alsa-driver-modules.
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by luishasbon on 2011-04-01
> **lidex said:**
> First let's update your system:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```
**Reboot**
Now try updating your alsa-driver-modules.
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Dear Lidex!

I havent tried out this still, but I think I was wrong about the module, the module is actually snd-hda-intel, the thing is that both, the hdmi nvidia soundcard and the via 82 motheboard card are using the same module, i think this is way the system only recognize one. Now, how do I specify which device is supposed to be used by the module?. Thanks ill try out this above before :)

---

### Post by luishasbon on 2011-04-01
Lidex, that didnt work out! :(

---

### Post by lidex on 2011-04-01
> **luishasbon said:**
> Lidex, that didnt work out! :(
OK. Go back to post #2 and rerun the script.

---

