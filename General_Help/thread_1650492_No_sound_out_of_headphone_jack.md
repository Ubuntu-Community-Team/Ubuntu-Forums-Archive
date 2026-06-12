---
title: "No sound out of headphone jack"
date: 2010-12-21
forum: General Help
---

### Post by Ploozi on 2010-12-21
[FONT="Verdana"][SIZE="2"][LEFT]I've looked around the forums and I've seen that some people are having the same issue as me, but the workarounds that they have put out have not worked for me.

I have a Toshiba Satellite L655, workin with Maverick. Sound comes out of my main speakers that are on my laptop, but when I try to plug in my Bose headphones or my Logitech speakers, they don't want to work period. The headphone jack works I know for a fact because it works in Windows. 

When I open up Kmix, it doesn't show my headphone port at all, it shows up "RV710/730 Digital Stereo (HDMI)" which is my TV's audio output and then my main laptops "Internal Audio Analog Stereo".

Any help will be helpful, I'm not a completely beginner with Ubuntu, but this new laptop I just bought is buggin' me.[/LEFT][/SIZE][/FONT]

---

### Post by Zorael on 2010-12-22
I don't know what posts you've read, so I'll just list the first things that come to mind.

If you open up **alsamixer** in a terminal, is there an option to enable Headphone Jack Detection or something to that effect?

If that fails, you may need to specify a different *model* for your soundcard chipset. This is assuming you have an Intel HDA-based soundcard.

A chipset in one soundcard (or motherboard) may have different quirks compared to the same chipset in another soundcard. The driver tries to autodetect which one you have and interface with it accordingly, but it's not always right. For instance, I have to specify **model=acer** on my Acer Aspire **9815**, since the driver identifies it as an Acer Aspire **9810**, whose sound chipset apparently has different quirks than mine has.

If you run '**aplay -l**' in a terminal, it should list what soundcard **[COLOR="RoyalBlue"]driver[/COLOR]** you're using as well as the name of the **[COLOR="Green"]chipset[/COLOR]**.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: **[COLOR="RoyalBlue"]Intel [HDA Intel][/COLOR]**, device 0: **[COLOR="Green"]ALC883 Analog [ALC883 Analog][/COLOR]**
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
(Again, if it doesn't say **[COLOR="RoyalBlue"]HDA Intel[/COLOR]**, this may not be applicable).

Open up **/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz** in a text editor, such as Kate. Find the section for your chipset and see if there is any entry that sounds like it could match your machine and soundcard. Excerpt;
```
**[COLOR="Green"]ALC[/COLOR]**882/**[COLOR="Green"]883[/COLOR]**/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
[B][COLOR="Red"]  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G[/COLOR][/B]
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```
Doing a text search in the file, there seems to be a **[color=red]toshiba[/color]** model that might do the trick for you. Unless that's the one being detected.

To try one, create a new file as **/etc/modprobe.d/options.conf** (or any other filename you want though it must end in **.conf**). You need superuser permissions for this, obviously, so Alt+F2 and '**kdesudo kate /etc/modprobe.d/options.conf**'. Add a line specifying what model you want to force, like so;
```
options [COLOR="RoyalBlue"]**snd-hda-intel**[/COLOR] model=**[COLOR="Red"]toshiba[/COLOR]**
```
For changes to take effect you have to unload the module (driver), which is difficult/impossible if you're running a graphical desktop. PulseAudio may hinder it further, so the easiest way is to simply reboot.

To make the process faster, instead of making a full and normal boot into X, you can instead boot into recovery mode, pick **root shell** and run '**speaker-test -twav -c2**' to play a test sound. Be sure to check that both your speakers and your headphones work before making a judgment as to whether the model was a hit or a miss. *ALSO*, hitting the correct model may only unlock that Headphone Jack Detection option in alsamixer, so make sure to check there as well.

You may need to test several on a trial and error basis. Try other models listed in your chipset section - you may just find one that works. If not, then it's a bug that needs to be reported. ...In a sense it should be reported in either case.

---

### Post by Ploozi on 2010-12-22
When I run aplay -l, I get this:

```

card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And I went through the "/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz" and I looked for my chipset "Conexant CX20585", which wasn't there but I looked for all the Toshiba model names, attempted those, and unfortunately it didn't work. I then did put in the basic "laptop" name because I only have two ports, the microphone and the headphone ports, and that didn't work neither. It's probably a bug in ALSA or the kernel, no idea.. I still have audio for the main speakers, but I'd just rather have the audio come out of my headphone port because you can set up different speakers.

---

### Post by Zorael on 2010-12-23
Hmm. Some slight googling turns up with [this thread](http://ubuntuforums.org/showthread.php?t=1641931).

> **2) Built-in microphone, microphone input jack, and headphone output jack do not work.**
-Built-in speakers work.  Plugging in headphones do not mute speakers.

Audio: Conexant CX20585

Solution: 
-edit /etc/modprobe.d/alsa-base.conf and add:
```
options snd-hda-intel model=thinkpad
```

References:
[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/2698401/]("http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/2698401/")
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Note: Upgrading to the latest alsa development code (3 Dec 2010) did not resolve the sound issue.
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")
Whether you save it to **alsa-base.conf** or your own .conf file makes little difference; changes to **alsa-base.conf** might get overwritten when doing upgrades, though.

Last post was 6 days ago so if you're still having trouble after trying that out, perhaps the original poster is still sort of around to help.

---

### Post by Ploozi on 2010-12-24
Yeah I've tried changing the model name to different things that I have found throughout the internets and none of them worked. I'm wondering if its a bug maybe.

---

### Post by Ploozi on 2010-12-24
Okay, so I was getting desperate, so I removed everything ALSA from my  system and installed OSS4, and now I can listen to music through my  speakers. It's not fully complete just yet. I gotta find out a way to make my internal speakers mute when something is plugged into the headphone jack, and for some reason my back speakers are crackling, but for right now, the problem is somewhat fixed.

EDIT:: Everything is working now. If possible, please delete this thread.

---

