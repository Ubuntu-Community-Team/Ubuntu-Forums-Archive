---
title: "Emu 1616 and ALSA"
date: 2010-02-25
forum: General Help
---

### Post by counselordave on 2010-02-25
I'm running 9.10.  I was installing ALSA so that I could run my EMU 1616, and when I tried to go through the steps to install, I'm running into two errors that I've noticed so far.  I think.  Anyway, the first is that is states that the panelw library isn't there, and that alsamixer: function snd_ctl_open failed for default: No such device or address.  The alsamixer one is really odd, since it's there, but I don't know why it won't run. 

I initially had it running, and now it isn't.  I've yet to get sound out of my EMU.  the terminal window also tells me that it can't find the snd_emu file, even though it exists on the computer as well.    I need an answer for a dummy.  Help Please!

---

### Post by counselordave on 2010-02-28
I got some features to work.  Still working on the others.

---

### Post by saimoncis on 2010-03-11
Hi, I'm using 9.10 too with my 1616 pcmcia
it all works well, I have followed the simple guide in the ALSA site.

You said that once it worked, do you have tested the midi input from an external source?

It's the only thing that I don't make to works...
ciao

---

### Post by counselordave on 2010-03-13
I tried testing the midi.  Haven't gotten that to work either.  What I find incredibly odd about the issues I'm having is that the stereo mini out on the dock and the headphone out on the dock work just fine, as well as the headphone out on the pc card work, but I can't use anything else.  I can't seem to get control of anything.  So I don't know.  I read somewhere where someone was using ardour and they got things to work.  Other day I tried a microphone in, but it didn't work too well.  The quality was crappy.  So I don't know what's going on.  I'll check the alsa site again.

---

### Post by saimoncis on 2010-03-19
I use Ardour flawlessy, with both the mics recording.
For yor crappy sounds, try to set to 48000 hz the alsamixer, jack and Ardour. For me it works with no glitches..
ciao

---

### Post by Ilnore on 2011-06-03
I'm struggling to get an E-MU 1616M / PCIe working under Ubuntu Studio 11.04.

lspci detects my card okay, and Ubuntu Studio 11.04 comes with ALSA 1.0.24. Can't seem to find a proper configuration any way I try. There's not much basic configuration documentation anywhere, so I can't get my card detected...

Tried compiling ALSA from scratch too, and that came up with a few compilation errors, so I'm missing some library somewhere... no documentation on what I'd need though.

This is a bit sad, was really looking forward to not having to use Windows for an audio workstation for a change. :p

---

### Post by Abanom on 2012-02-28
From a clean install run install the latest ALSA like this [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Thats it.  Run Qjatclt and Emutrix to route.  You might need to set up your capture dsp settings in the alsamixer from your terminal as well.

Also check out [http://ubuntuforums.org/showthread.php?t=1378290](http://ubuntuforums.org/showthread.php?t=1378290)


[]("http://ubuntuforums.org/showthread.php?t=1681577")

---

