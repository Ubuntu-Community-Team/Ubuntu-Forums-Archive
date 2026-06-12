---
title: "Help me Obi Wan, you're my only hope. On Board Optical Digital out hell!!!"
date: 2009-12-08
forum: General Help
---

### Post by speed3racer on 2009-12-08
Dear all...

2 weeks ago I junked MS completely, Vista gawn, just sick of always working at making it work.. And here I am 2 weeks down the line of this and still no worky

Installation of Karmic Koala went well all except for audio. Previously working with Vista

I have searched this entire forum and I have made sure Alsamixer's channels aren't muted 

My card appears in aplay:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v says

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device c0aa
    Flags: medium devsel, IRQ 22
    I/O ports at ec00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx


Alsamixer says it's a Realtek ALC650F

In the last install (I thought a re-install would help - No - another story for the evolution backup-restore forum) wth Pulse volume control I could see signal inn a VU style meter when audio was playing. So I know there's sound in there somewhere I ust can't get it out.

I have red light at the Toslink port on the back of the PC I have IEC958 enabled 

Please help before I junk this too and go back to my ZX Spectrum...

What else can I tell you for you to help me?

Pleas note I am a complete noob at Linux and the terminal scares me!!!


Please please.. If I don't get this working my 3 year old daughter will leave me for someone with a dvd player to watch Peppa Pig :popcorn::(

Kind regards and thanks in advance

Your's 
'Soundless in Herts UK'

---

### Post by lidex on 2009-12-08
Check these out:
[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala]("http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala")
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")

---

### Post by speed3racer on 2009-12-09
Thanks lidex for that but unfortunately after all that I still have no sound.

I have what looks like sound happening in the volume meter but nothing getting to my amp. There must be something I'm missing to get the signal to the optical output laser doofrey whatsit on the back of my Shuttle XPC...

There has to be a solution


Thanks again in advance

Neil

---

### Post by llamabr on 2009-12-09
Hi, there.  Have you tried plugging in headphones?  Let's make sure that there's no output first that's just going to the wrong place.

Next, many report that uninstalling pulseaudio solves the problem:

```
sudo apt-get remove pulseaudio
```

Finally, you say there's no sound.  In firefox, or at all?  Can you play mp3's from the terminal?  Do you hear startup sounds?

---

### Post by speed3racer on 2009-12-10
Analogue sound is fine, As a fall back I have plugged the headphone out from the PC into an analogue input to my amp and have everything OK...

I just can't get the Optical output to operate...

There has to be a way... :(

Thanks for your input.

Neil

---

### Post by lidex on 2009-12-11
speed3racer:
Can you clarify this for me? 
> Thanks lidex for that but unfortunately after all that I still have no sound.
> Analogue sound is fine
Which is it? You have sound or you don't??

---

### Post by speed3racer on 2009-12-11
lidex, I have analogue sound working via the headphones socket on my PC. what i want is the optical (Toslink) digital out to work.

I am using the PC as a HTPC and  have it connected to a Home theater system and would like the best possible sound - DTS, Dolby etc. It can't be beyond possibility.

The headphone socket is a compromise just to get sound out so the PC is useable (read: justifiable by the wife!!!)

Again many thanks for any input


Neil

---

### Post by cgb on 2009-12-11
by default sound will not play via headphone and digital at the same time..  Sounds like your default is set for analog.  Might have other issues as well but for starters you will need to correct this.  If you are using pulseaudio you can open the pulseaudio volume control, choose output devices, right click on your digital device and make sure default is chosen.  Otherwise no sound will be sent to your digital device.

---

### Post by speed3racer on 2009-12-11
Thanks cgb.been there done that... with Digital output IEC958 selected... no output via optical even though in Pulse volume control I can see music playing in the level meter..

There's my confusion...


Thanks anyway, appreciate your input :-)

Neil

---

### Post by cgb on 2009-12-14
hmm..  Not sure completely what is going on in your situation then.  The things that have helped me in the past for getting spdif working is what I mentioned earlier and possibly making sure iec958 is not showing muted in alsamixer, which it sounds like you have verified already.  There are some other pulseaudio threads in these forums that might help by going through and reinstalling pulseaudio.  Best of luck...

---

### Post by Chesamo on 2009-12-14
It is possible that your optical sound card is simply not supported by Ubuntu yet (or is partially supported, since you have analog out).

---

### Post by dnns on 2010-03-01
I used to get digital stereo out of my PC just fine. Now I have the same problem - albeit with the COAX digital out of my ASUS M2N32. Tried upgrading to Lucid 10.4, still no dice.

---

