---
title: "No Sound in 9.04"
date: 2009-07-01
forum: General Help
---

### Post by the beekeeper on 2009-07-01
I went through the well written tutorial on this site:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578))


but to no avail.  I am trying to use the onboard sound card.  I have never gotten a peep out of the speakers.  The PC speaker works fine.  Is there a way to generate a constant sound to make sure everything is plugged in OK?  It seems to be working ok on the software side, and I know for sure the speakers work.  Any suggestions?  Thanks in advance.

---

### Post by the beekeeper on 2009-07-01
I am trying to run the onboard soundcard for an A-Bit IS7. Thanks again.

---

### Post by the beekeeper on 2009-07-01
I do not even hear the drumbeat at the login screen.

](*,)

---

### Post by DeMus on 2009-07-02
> **the beekeeper said:**
> I do not even hear the drumbeat at the login screen.

](*,)

Please open a terminal (Applications > Accessories > Terminal) and type
lspci
Select the output in the terminal window by dragging your mouse over all the text while keeping the left mouse button pressed, press ctrl-shift-c to copy and paste (ctrl-v) this in your answer.

---

### Post by the beekeeper on 2009-07-02
Thank you very much.

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)
02:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem

```

---

### Post by the beekeeper on 2009-07-02
Is something wrong with having alsa and pulseaudio installed?
I had a sound card in previously, but I was told it was broken so I removed it and only have the onboard sound now.

Can I uninstall and re-install these components in the Synaptic PM?

---

### Post by the beekeeper on 2009-07-02
Oh well...

I remember last time I installed Ubuntu the wireless card would not work.  I understand it was because the drivers were proprietary for the card.  I would think sound would not be so difficult.  Are Abit motherboards proprietary as well.  Also does linux suffer from bugs like this all the time?  Thanks in advance.

---

### Post by moster on 2009-07-02
I do not understand completly. Post result of this too.
```
aplay -l
```

You had other sound card in ubuntu, and after while you remove it and now your integrated sound card is not working? All of that in same Ubuntu installation?

Check BIOS if your integrated sound card is really "enable" and check if speakers is in the right hole... Just play some song and change holes... That ac97 should work.

---

### Post by the beekeeper on 2009-07-02
Thank so much for the help.  Here are the results:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by the beekeeper on 2009-07-02
This makes me sad.  I really want to use/ learn ?Linux, but it appears to have a vertical learning curve.

:confused:

---

### Post by the beekeeper on 2009-07-02
Do you think a full reinstall would work?

---

### Post by moster on 2009-07-03
I still do not get it. If sound work before in Ubuntu on same card, then reinstall will help. If never work then it is probably incompatible and no one here post solution.

Now, if I were you and I never had sound in jaunty with that sound card... I would download latest alpha Ubuntu 8.10 and boot with live cd and see if I have sound there.

This is just my suggestion, what I would do. Here

[http://cdimage.ubuntu.com/releases/karmic/alpha-2/]("http://cdimage.ubuntu.com/releases/karmic/alpha-2/")

---

### Post by sandwormblues on 2009-07-03
This might work for you.  I have had a similar problem with my Intel 82801 ICH7 audio.  I've been having this problem since Dapper Drake and now I'm running Intrepid Ibex.

Open a terminal and type:

sudo gedit /etc/modprobe.d/alsa-base.conf 

add the line at the bottom:
options snd-hda-intel model=3stack

In 9.04 it mostly works, but I can't record audio with the microphone.  I can hear the microphone through the speakers but i can't use audacity or skype.  I'm probably going to downgrade to Gutsy (i hope kde4 still works).

---

### Post by the beekeeper on 2009-07-04
Thanks to both of you for all the help.  I never thought of just loading the live cd and see if that would work.  I really like the Linux community and hope to become part of it!  Thanks again!!!

---

### Post by moster on 2009-07-04
Your sound chip name is "IEC958", try to search that on internet... Just by enter that in google there are several problems listed, so you are not alone. This is just one of them..

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/172654]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/172654")

But, like I said, with new ubuntu all of your misterious problems might be gone. Like mine. I guess it was new kernel credit.

---

### Post by the beekeeper on 2009-07-05
I also downloaded Mint and Damn Small Linux.  I don't know if they use a different setup, but it can't hurt to try.  I have really started lo like Linux though... is it too late to turn back before it becomes an obsession?

;)

---

### Post by ivanvajar on 2009-07-05
When Linux becomes an obsession, it's a good thing ;-)

---

