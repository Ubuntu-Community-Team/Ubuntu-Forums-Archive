---
title: "mp3 to CD-R: won't play"
date: 2011-08-11
forum: General Help
---

### Post by peragrate72 on 2011-08-11
I've Googled this a bunch, haven't found the answer yet, and know that many people have posted about this.

I've gone through about 8 Sony CD-R 700mb discs trying to burn an mp3 I made in Audacity. I've checked Audacities settings: 44100 Hz, exported as mp3 and wav 16-bit PCM (whatever that means...)

(It plays fine on my laptop)

And I've used Brasero, GnomeBaker, and K3B.

The last time I remember making audio CDs on a Ubuntu system was about a year ago, and it was a snap. I used to make them for the drive to work all the time.

Now, for whatever reason, I simply can't make an audio CD that plays in my Sony CD Walkman. It's old, but it's the same one I used a year ago for the ride to work.

Can anyone with more technical experience help me with this?

Thanks.

---

### Post by haqking on 2011-08-11
> **peragrate72 said:**
> I've Googled this a bunch, haven't found the answer yet, and know that many people have posted about this.

I've gone through about 8 Sony CD-R 700mb discs trying to burn an mp3 I made in Audacity. I've checked Audacities settings: 44100 Hz, exported as mp3 and wav 16-bit PCM (whatever that means...)

(It plays fine on my laptop)

And I've used Brasero, GnomeBaker, and K3B.

The last time I remember making audio CDs on a Ubuntu system was about a year ago, and it was a snap. I used to make them for the drive to work all the time.

Now, for whatever reason, I simply can't make an audio CD that plays in my Sony CD Walkman. It's old, but it's the same one I used a year ago for the ride to work.

Can anyone with more technical experience help me with this?

Thanks.

I dont personally use audacity as i use K3b and works great though i needed to add a plugin for it to convert .mp3 straight to CD. Perhaps it is same for audacity ?

Edit: yes Audacity does not support it due to patent so you need to install LAME see here [http://wiki.audacityteam.org/index.php?title=MP3](http://wiki.audacityteam.org/index.php?title=MP3)

see here for installation of LAME
 [http://wiki.audacityteam.org/wiki/Lame_Installation](http://wiki.audacityteam.org/wiki/Lame_Installation)

---

### Post by peragrate72 on 2011-08-11
I don't think the problem in with Audacity. I've already installed lame. Let me explain the process I'm using:

1. I recorded the files with Audacity and exported them in MP3 and WAV format.
2. I tested the track and it played fine on my laptop.
3. I burned multiple CD-R copies of the sound track using K3B, Brasero, and Gnome Baker: None of which would play on a Walkman that is cd-r/cd-rw compatible.

Sorry, sometimes I just don't explain things very well. So, I actually have no idea what the problem is. But making an MP3 with Audacity is not it.

Perhaps the mp3 is encoded incorrectly. Perhaps the burning software has the wrong dependency installed.  I know I have cdrecord (well, whatever it's called... you know the one I mean...)

---

### Post by mcduck on 2011-08-11
So are you actually trying to burn the .mp3 or .wav files to the disk? That will only give you a data-CD with some audio files in it, while an audio-CD is completely different thing...

(you said the player is CD-R/RW-compatible, but you didn't mention if it's MP3-compatible or not, and if you are trying to create a normal audio-CD or an "MP3-CD" (which is just a normal data-CD with a bunch of .mp3 files in it)

If you want to make an audio-CD with Brasero you need to choose the "Audio Project" option. That should work just fine as long as you have the required gstreamer plugins installed for whatever type of encoding your source files are using.

---

