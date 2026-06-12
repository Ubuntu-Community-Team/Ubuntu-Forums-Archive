---
title: "Sound thru DVI&gt;HDMI on Nvidia card"
date: 2009-10-18
forum: General Help
---

### Post by mac666 on 2009-10-18
Hey!
Im trying to get the sound to go to my TV thru my HDMI cable, that is connected to a DVI adapter on the videocard.

My videocard is a MSI Nvidia 9800GT Zilent and do support audio thru this setup, but i cant get it to work, and the manual doesnt really explain how to make it happen.

With the same TV and cords/adapters i get sound and video on another computer with a different videocard, so its nothing wrong with the cords.

My friend told me to activate IEC958 and IEC958 Default PCM in Volumecontroll settings, and then i activated it in Switches (Dunno the translation for this, im on swedish ubuntu)

Does anyone now if i missed anything? Do i need to update Alsa? I think i have 1.08

Do i need to connect anything else to the videocard hardware, eg SPDIF? I have no idea what this is :)

Thaanks!

---

### Post by m_duck on 2009-10-19
Hey,

I don't know for certain, but I was always under the impression that it isn't possible to send sound through a DVI cable. I think DVI is basically HDMI minus audio. Googling "sound via dvi cable" and suchlike seems to yield similar conclusions.

An alternative would be to run an optical cable from your sound card into an audio in on your TV if there is one?

---

### Post by iski4kix on 2009-10-19
.

---

### Post by zzzBrett on 2009-10-19
> **m_duck said:**
> Hey,

I don't know for certain, but I was always under the impression that it isn't possible to send sound through a DVI cable. I think DVI is basically HDMI minus audio. Googling "sound via dvi cable" and suchlike seems to yield similar conclusions.

An alternative would be to run an optical cable from your sound card into an audio in on your TV if there is one?

This is right on.  No sound in a DVI cable.

---

### Post by mac666 on 2009-10-21
I can get sound via same setup via on another computer
No sound via DVI cable but you can channel the sound thru a DVI > Hdmi adapter.

No problems their on a windows computer...
I just wonders how to choose to output the sound thru my videocard...

---

### Post by zzzBrett on 2009-10-21
> **mac666 said:**
> I can get sound via same setup via on another computer
No sound via DVI cable but you can channel the sound thru a DVI > Hdmi adapter.

No problems their on a windows computer...
I just wonders how to choose to output the sound thru my videocard...

What ports do you have on your video card?

---

### Post by Another Monkey on 2009-10-21
> **mac666 said:**
> I can get sound via same setup via on another computer
No sound via DVI cable but you can channel the sound thru a DVI > Hdmi adapter.

No problems their on a windows computer...
I just wonders how to choose to output the sound thru my videocard...
This is my understanding, please excuse me if I am wrong.
I thought DVI and HDMI plugs were the same, but DVI did not pass sound.  I guess you could have a device that take the DVI picture and merges that with sound (DVI+sound)->HDMI.  If you see what I mean.

Is the hardware identical between the two PCs?  Are you sure you are not taking the signal from a TV card, rather than just the graphics card?  I've not heard of graphics cards mixing in sound, but that's not to say they don't exist.

---

### Post by zzzBrett on 2009-10-21
> **Another Monkey said:**
> This is my understanding, please excuse me if I am wrong.
I thought DVI and HDMI plugs were the same, but DVI did not pass sound.  I guess you could have a device that take the DVI picture and merges that with sound (DVI+sound)->HDMI.  If you see what I mean.

Is the hardware identical between the two PCs?  Are you sure you are not taking the signal from a TV card, rather than just the graphics card?  I've not heard of graphics cards mixing in sound, but that's not to say they don't exist.


This is not correct.  DVI and HDMI are two completely different plugs.  The video signal, however, is the same (as I understand).  Both carry digital video signals.  HDMI also carries digital audio signal, but the DVI cable does not.  This is why you can get an adapter that goes from DVI to HDMI, which will deliver video but not audio.

Someone please correct me if i'm wrong :)

---

### Post by mac666 on 2009-10-24
cant u read. it works. 
ive never mentioned a dvi cable. its a dv adapter!

the problem is drivers, cant get
 back my audio drivers... check my other thread,
search my nick...

---

### Post by zzzBrett on 2009-10-24
.

---

### Post by mac666 on 2009-10-25
Sorry, was on mobile phone while doing last post. Couldnt edit the typo.

DVI adapter to HDMI works to send sound, DVI Cable cannot send sound.

If it do work on my computer now, its all about buggy drivers.

Most Nvidia GF supports sound thru DVI if its used with the right adapter.
BUT on most GF the SPDIF connection most be connect on the GF to the MB.

---

### Post by zzzBrett on 2009-10-25
Run alsamixer in terminal, look for IEC958 or anything that looks similar to it.  Scroll over to it, and press "m" to switch it on/off.

---

### Post by mac666 on 2009-10-25
It works right now but i cannot Raise or lower volume... Only mute, and only 1 instance may use it at the time... Any ideas?

---

### Post by zzzBrett on 2009-10-25
> **mac666 said:**
> It works right now but i cannot Raise or lower volume... Only mute, and only 1 instance may use it at the time... Any ideas?

What made it work?

---

### Post by mac666 on 2009-10-25
The SPDIF Chord to the MB...

---

### Post by P4man on 2009-10-25
check your default mixer in system > preferences > sound

---

### Post by Lantesh on 2009-10-25
> **mac666 said:**
> The SPDIF Chord to the MB...

Ding ding ding.  On Nvidia cards the audio pass through will not work unless you actually run a physical connection from a S/PDIF header pin on the mother board to the video card audio input.

---

### Post by mac666 on 2009-10-25
> **Lantesh said:**
> Ding ding ding.  On Nvidia cards the audio pass through will not work unless you actually run a physical connection from a S/PDIF header pin on the mother board to the video card audio input.

....

That part i figured out some days ago. The problem now is that i cant get the drivers to work good.

I refere to this Thread instead, since its more On Topic: 
[http://ubuntuforums.org/showthread.php?p=8147202](http://ubuntuforums.org/showthread.php?p=8147202)
Please help me out there!

---

