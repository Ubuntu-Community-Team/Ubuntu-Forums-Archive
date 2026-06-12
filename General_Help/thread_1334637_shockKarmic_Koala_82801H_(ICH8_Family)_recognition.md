---
title: ":shock:Karmic Koala 82801H (ICH8 Family) recognition of sound card - A real challenge"
date: 2009-11-22
forum: General Help
---

### Post by PauPau on 2009-11-22
Greetings,

I've been trying to tackle this problem for way too long now,
I run a HP Pavillion with the Sound Card:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Just can't get the sound to work or the computer to recognise the soundcard, tried OSSv4, many alsa versions... but still doesn't work.
Someone help, please.

---

### Post by Claus7 on 2009-11-22
Hello,

if you have the patience, this thread is covering a sound card similar to yours. Following some links from there, you might be able to make out what is going on with yours.

[http://ubuntuforums.org/showthread.php?t=1321413](http://ubuntuforums.org/showthread.php?t=1321413)

> Just can't get the sound to work or the computer to recognise the soundcard

Your sound card seems to be recognized from ubuntu. How you were able to give the specs of the card? I think that you would get an unknown type as a result, if it was not recognized.

Good luck,
Regards!

---

### Post by PauPau on 2009-11-22
Thanks Claus7,

I'm reading through it right now. I used the  lspci command. Recently I've read a threat that recommended OSSv4 instead of ALSA, so I uninstaled all my ALSA utils and installed OSS, still... No Dice. The Card doesn't show up on the System>Administration>Hardware Drivers, nor on Sound Preferences, even if I post
sudo aplay -l in the terminal:
aplay: device_list:223: no soundcards found...

Completely stumped...

---

### Post by Claus7 on 2009-11-23
Hello,

just googling a little I came up with this:

[http://ubuntuforums.org/showthread.php?t=291078](http://ubuntuforums.org/showthread.php?t=291078)

From what you have supplied up to now, I think that it will fix your problem.

Regards!

---

### Post by PauPau on 2009-11-24
Thank you so much for the effort. 

Sadly, tried everything and nothing works. Must have gotten something very very wrong.


Still, thank you for trying.

---

### Post by friedhelm on 2009-11-29
Hello PauPau

I had the same problem with my
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

(Karmic)

I found a solution on
[http://forum.ubuntu-nl.org/installatie/ubuntu-9-10-en-geen-geluid/?action=printpage](http://forum.ubuntu-nl.org/installatie/ubuntu-9-10-en-geen-geluid/?action=printpage)

I added the following line
   options snd-hda-intel probe_mask=1
to the file
   /etc/modprobe.d/alsa-base.conf
and restarted.
That was all. My headphone works well. The integrated speakers of my Medion MD 97470 work, though they sound a little bit funny. This is, because the MD 97470 has two stereo speakers and a small "subwoover". The subwoover seems to be without function.
Nevertheless, I am happy.

Hope this helps
Friedhelm

---

### Post by shadetree1 on 2009-12-16
> **friedhelm said:**
> Hello PauPau

I had the same problem with my
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

(Karmic)

I found a solution on
[http://forum.ubuntu-nl.org/installatie/ubuntu-9-10-en-geen-geluid/?action=printpage](http://forum.ubuntu-nl.org/installatie/ubuntu-9-10-en-geen-geluid/?action=printpage)

I added the following line
   options snd-hda-intel probe_mask=1
to the file
   /etc/modprobe.d/alsa-base.conf
and restarted.

That was all. My headphone works well. The integrated speakers of my Medion MD 97470 work, though they sound a little bit funny. This is, because the MD 97470 has two stereo speakers and a small "subwoover". The subwoover seems to be without function.
Nevertheless, I am happy.

Hope this helps
Friedhelm

Thank You......I have been trying to fix this bug on a new install of Karmic on  a Dell Inspiron 1318.  Intel HD Audio 82801H chip, works great now...:P

shadetree

---

