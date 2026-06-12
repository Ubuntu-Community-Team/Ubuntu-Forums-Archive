---
title: "No sound over HDMI in Karmic??"
date: 2009-12-06
forum: General Help
---

### Post by RX8volution on 2009-12-06
Hi, I just re-installed this laptop from scratch with Karmic, and when I plug in HDMI the video works brilliantly, but NO AUDIO!

aplay -l shows:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Obviously ... missing the Digital piece - anyone have any idea what's happened?!

I hate to say this but "it works fine in dual-boot Windows7"...

---

### Post by RX8volution on 2009-12-06
No one?  anyone?

---

### Post by nielsavonds on 2009-12-12
Hi,

I'm having the exact same problem and have been trying to get it to work for a couple of weeks now...

Please let me know if you or anyone else finds a solution.

Thanks,
Niels

---

### Post by baltm604 on 2009-12-25
am having the same problem as well.  looking at the alsa drivers, trying to figure out why the intel 965 chipset shows up as analog and not digital.  Will let you know if I figure it out, but I am kinda of a noob with this as well.  

maybe we need to compile the hda digital driver and load that instead?

---

### Post by nielsavonds on 2009-12-26
Hi,

I'm not very experienced with Ubuntu either, but I'll keep looking for a solution. Meanwhile, for anyone to be able to help us, I'll give the print of some commands:

niels@niels-laptop:~$ lspci | grep -i audio

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

niels@niels-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec

Codec: Analog Devices AD1981
Codec: Conexant ID 2c06

I hope we can figure this out, because I'm tired of waiting for ages to boot my Vista just so I can watch something on the television.

Niels

---

### Post by AllanP on 2009-12-26
Same here. Laptop = HP DV6-2043CA; no sound, but works fine in Windows 7.
I copied your commands and got the following:

lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series].

cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD75B3X5
:confused:

---

### Post by nielsavonds on 2009-12-26
Hi Allan,

since there are a lot of different ways in which sound over HDMI doesn't work (and a lot of different solutions that might get it to work), can you please paste the output of :
aplay -l

I have an HP Compaq 8710w.

Niels

---

### Post by AllanP on 2009-12-26
I'm not sure if I'm barking up the wrong tree. In Sound preferences I switched Sound output from Internal Audion Analog Stereo to R700 Audio Device trying to get sound to work; wasn't sure which should be checked. Bottom line = No sound either way.

allan@allan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
allan@allan-laptop:~$

---

### Post by nielsavonds on 2009-12-26
Hi Allan,

your problem is a seperate one (since in your aplay -l, a digital one shows up). The problem described in this thread is that no digital audio device is showing up in this list.

Please open a new thread since replies here will probably not be relevant to your case.

Niels

---

### Post by DutchSherpa on 2009-12-26
Is there _anybody_ who has got sound working smoothly in Karmic? In Rhythmbox as well as Flash/Firefox as well as Ekiga? No sound stops and no disappearing devices if you activate another application? Just like it works in -- dare I say it? -- Windows?

Please, send me your setup. I needed an afternoon to fix sound in Flash/Firefox. (There is so much well-meant crap on the forums. Why can't the guys at Ubuntu mark the correct and useful posts?) 
Then I wasted three days on installing VOIP and it still does not work...

I would love to work on a Linux machine, but I am afraid I have to give up on Ubuntu altogether.

Thanks a lot for a working sound setup. (I am using a Fujitsu Siemens PC, with a VIA VT82XX soundcard that Ubuntu consistently identifies as a VT1708.)

---

### Post by JakaBac on 2010-02-06
Hi Everybody

I also have 8710w HP Notebook and the digital output was also missing.

This can be partially solved by adding:
```
options snd-hda-intel **model=basic** power_save=10 power_save_controller=N
```
to:
/etc/modprobe.d/alsa-base.conf

Since it seems that the HDA Intel codec driver detects that you have an HP system and automatically sets the model to **hp** Which enables configuration patch for the HP nx6320 notebook.

The AD1981 chip has the following models available:```

AD1981
        basic      3-jack (default)
        hp      HP nx6320
        thinkpad   Lenovo Thinkpad T60/X60/Z60
        toshiba   Toshiba U205

```

But I said partially above, because the **hp** model has the right customizations to make your audio volume controls and the mute button work properly, but it disables the digital output. With the **basic** option you get back the digital out, but the volume level touch control and the mute button behave strangely (the mute in inverted,...). And of course your speakers stop working since headphones plug autodetection stops working and the system thinks that you have headphones plugged in at all times.

And lastly, the most unfortunate thing is that even if you get the digital output back and aplay -l shows:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I still did not manage to get the sound through the HDMI. The picture works without problems, but when selecting the digital output you simply get no sound. I tried all the tricks which I found on the net. Setting volume level to 0, using alsamixer command to play with the volume controls, I even forced the Pulse Audio daemon to 48khz sampling rate (with 44.1khz I was getting "unsupported audio signal on my TV"). But still no luck. The TV doesn't get any sound.

I am now slowly running out of ideas...

---

### Post by nielsavonds on 2010-02-09
Hi,

thank you very much for your reply! At least now we got the digital output and can start messing with it until we get the sound working. I will run some tests this weekend when I get home again.

Thanks again,
Niels

---

### Post by JakaBac on 2010-02-09
Just to bring everyone up to speed with what I have tried so my efforts are not duplicated.

I tried to play 44.1khz 16bit Stereo and 48khz 16bit stereo with aplay I could see that my TV (Sony BRAVIA) complains about the format when sampling rate is 44.1khz. With 48khz it does not complain, but in either case the sound is not coming through.

I then used alsamixer to route the microphone input to the ADC and then to route this to the digital out since the datasheet for the codec chip AD1981HD shows that this can be done

Curious people can find the datasheet here:
[[COLOR="Blue"]AD1981HD Datasheet[/COLOR]]("http://www.alldatasheet.com/datasheet-pdf/pdf/166507/AD/AD1981HD.html") 

This also did not work.

Then I downloaded the hda-verb utility and looked at the windows drivers if I could find codec initialization commands there and immitate this in linux (hda-verb allows sending commands to the codec).
The documentation for everything (hda-verb, Intel HD audio specs, and linux Intel HD sound driver architecture) can be found here:
[[COLOR="blue"]HD-Audio docs[/COLOR]]("http://www.kernel.org/pub/linux/kernel/people/tiwai/docs/HD-Audio.html")

I found some init verbs which the windows driver sends, nut after applying them in linux, I still did not get any sound out.

Then I went crazy and messed with the codec commands which I thought that could make a difference. This also included turning on the internal beep generator at 1khz which is supposed to send a beep out of all codec's outputs. I got the beep on the analog out, but the digital was silent.

Then after some further googling I found some people saying that NVIDIA's driver doesn't support sound passthrough in linux.

Next I was thinking that maybe the driver loading order is different in windows and linux and that in windows display driver loads before sound which maybe makes a difference, so I suppressed loading of sound related kernel modules until X was already running. Also no results..

The last thing that I could think of is HDCP. Maybe my Sony TV wants a HDCP compliant source in order to play sound which Linux definitely does not provide. (In Windows I have a HDCP page in the NVIDIA control panel. I can't adjust anything there, It simply says that it is working ok). But then again... I think that HDCP would also cause that no picture would be displayed.

Does anybody know if the docking station for 8710w provides spdif out jack? If it does, then we could at least check if digital audio is coming out of the codec chip at all...

---

### Post by ApfelBirne on 2010-04-27
I got nearly the same problem. My ubuntu Karmic has lost his sound.
I'm using a lenovo r60 with a HDA Intel AD 1981 Soundcard. I found out that the alsa process isn't running but I couldn' get it startet again.

---

### Post by Alethenorio on 2010-05-20
I am in the exact same boat here. I have an HP 8510w and cannot get the digital portion to appear on aplay. I have been trying to get audio through HDMI ever since Ubuntu 8.10 (I am currently using 10.04)

I have just spent the last 2 hours trying stuff out.

I upgrade alsa to version 1.0.23 which made no difference then following the upgrade I added the model=basic which indeed gave me a digital output however I would get no sound anywhere and whenever I tried to choose the analog output to try and see if sound was working on normal laptop speakers, the output device would show up as a dummy.

I am still trying things out and I am also trying to get it on a Sony BRAVIA TV however I don't believe it has anything to do with HDCP.

I have the dock however I unfortunatelly cannot test it as it sits at work.

Anybody had any more progress on the matter?

Regards
Alethenorio

---

### Post by Alethenorio on 2010-05-20
Something tells me the digital output is for SPDIF only. I'll check whether the dock has a SPDIF output, and I was able to get sound coming through headphones when using the model=basic but that's it (As you suggested).

Maybe it might be worth to put up a bug report on launchpad? I have no idea where to even start so if anybody is up for it...

I have also tried pretty much every possible model combination for the AD198X found in the latest Alsa drivers but none worked. The basic was the only one to show a digital output (But no HDMI output).

---

### Post by JakaBac on 2010-05-20
Yes digital out is SPDIF only and the card can output two different signals at once. (one over analog and the other through digital)

the SPDIF does not mirror the analog out by default. If you manually fiddle with alsamixer you should be able to make the chip output same signal on analog out and SPDIF.

But inside the notebook the SPDIF is wired into the Quadro board which then embeds the audio into the HDMI signal.

So even if the digital out works on the AD1981, the Nvidia Quadro may still need something else in order to start embedding the audio.

So if you have a spdif port on your dock you can a least check if something is coming out of it. If it works there we can probably forget the hdmi audio since the nvidia driver probably needs to do something. And I have a strong hunch that this is the problem.
This can then only be fixed by the nvidia guys who know how their chips work and have the source for their driver.... Or the Nouveau hackers who are making the opensource version of the driver.

I can file this as a bug, but I doubt that Ubuntu team can do anything about it...

---

### Post by Alethenorio on 2010-05-21
I am not sure how I am gonna check the SPDIF as I don't have an SPDIF cable nor do I have anywhere to plug it in to see if sound comes out where the dock is at but I'll see if I can think of something.

If you have any ideas let me know

---

### Post by Alethenorio on 2010-05-21
I am currently sitting at work. I have checked the dock.

There's no SPDIF output as far as I can tell. There's a green output for headphones and a blue input which I believe it for a microphone.

However it does seem that some docking station models do have an SPDIF out as can be seen here

[http://www.norsystems.net/cgi-bin/p?showItemDetails=1&itemno=hpTc4200dock](http://www.norsystems.net/cgi-bin/p?showItemDetails=1&itemno=hpTc4200dock)

so I am afraid I can't help you much more to check the SPDIF out :(

Regarding the bug report, if anything, the fact that we get no sound through speakers and only headphone is a bug right?

Regards
Alethenorio

---

### Post by Alethenorio on 2010-06-09
Right, I have currently access to a dock that looks like the one I posted on the link above, and the yellow port at the back IS NOT a SPDIF port (It seems to be a composite video output)

This leads me to believe that there is no dock with SPDIF which again brings me to the question on what the digital output is for?

Anybody has had any more progress?

Regards
Alex

---

