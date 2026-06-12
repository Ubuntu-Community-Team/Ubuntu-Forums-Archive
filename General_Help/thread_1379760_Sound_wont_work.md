---
title: "Sound wont work"
date: 2010-01-12
forum: General Help
---

### Post by Martzy13 on 2010-01-12
My sound was working fine when i was running ubuntu 9.04 but with ubuntu 9.10 my sound just stopped working, i know its not the speakers, relatively new to Ubuntu so any help would be greatly aprreciated.

---

### Post by sigmarhophi on 2010-01-13
Sorry to read your sound decided to not work after your upgrade.  All hope is not lost, but some information will be necessary inorder to assist further.
-What type of sound card do you have?
-Is the Volume Applet running? and does it have an "X" on it?
-prior to your upgrade, did you install, or tweak your sound drivers?

---

### Post by Mickser_52 on 2010-01-13
This thread looks similar to yours [http://ubuntuforums.org/showthread.php?t=1379387]("http://ubuntuforums.org/showthread.php?t=1379387"). Don't know if it was solved or not.

---

### Post by Martzy13 on 2010-01-13
sudo apt-get install linux-backports-modules-alsa-karmic-generic



^^^
i tried this and it installed the newest version, i restarted my computer and still no sound

I'm not sure what sound card i have how would i check?

---

### Post by UltraParadigm on 2010-01-14
Hi.  Please pardon my N00bness, I just signed up because I was looking for a resolution to a similar issue, and I haven't edited my profile yet.

Quick specs
> 
Brand spanking new (2 days old) HP Dv6T
-Nvidia HD sound controler
-built in microphone
-Altec Lansing built in speakers
I've been working on my laptop non-stop in between work shifts and am dual booting with win 7.  Ubuntu 9.10 is already outperforming Win 7 in the fact that things I expected not to work, like my bluetooth device and internal mic were recognised right off the bat, whereas I had to install tons of HP drivers from their site before stuff would work in windows7.  Way to go Ubuntu!

Everything seems to work very well so far except for the sound.  I've been doing research whenever I had a moment to focus and I found the prev post about doing the sound test in administration>system testing. 

Lo and behold!  My sound works through my bluetooth headset!  This is amazing to me because I could't get my head set to work in Win7.  Win7 said I needed drivers to run my headphones!  So I rolled my eyes and said forget it.  

So since I can now hear sound through my headset in Ubuntu, I know that my sound devices and drivers are working, at least some of them.  What is not working is the sound through my speakers and headphone jacks.  The volume applet works and even responds to the HP touch buttons on the laptop (WOW!) and I can record my voice, but I can't play back anything through the speakers or through the headphone ports.

Is there something else that I need to install?  Linux seams to see two audio devices.
> 
:~$ aplay -l
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
I presume that the analog one is for speaker output and the digital one is my HDMI output that comes on this laptop.  But I would expect it to say nVIDIA rather than Intel.  Am I looking at the right device?  lspci shows me both intel and an nVIDIA devices.

> 
:~$ lspci
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
Anyone know what device is what?  Since the audio driver is obviously working, albeit through bluetooth headsets only, are there speaker devices that need to be installed or something?

---

### Post by UltraParadigm on 2010-01-14
I ran sudo apt-get install linux-backports-modules-alsa-karmic-generic, and rebooted, and everything is working perfectly for me now.  The speakers work now, and the microphone port, the internal mic, the head phone jacks, all working.  As long as I use the Analogue duplex hardware profile everything is kick ***!

---

### Post by Martzy13 on 2010-01-14
I tired the aplay -l in terminal and it said that no sound cards were found, what should i do now?

---

### Post by Martzy13 on 2010-01-14
[http://xpapad.wordpress.com/2009/12/31/fixing-sound-after-upgrading-to-ubuntu-9-10-karmic-koala/](http://xpapad.wordpress.com/2009/12/31/fixing-sound-after-upgrading-to-ubuntu-9-10-karmic-koala/)

FIXED!!!!!!! thanks to everyone for there help. this fixed my issue completely =)

---

