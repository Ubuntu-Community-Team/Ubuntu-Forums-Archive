---
title: "Sound issue"
date: 2009-11-01
forum: General Help
---

### Post by JosephMarc on 2009-11-01
[SIZE=2]Hi,
I have been a happy ubuntu user since 8.04 hardy heron, but I always had a problem with making my 5.1 sound system work. On hardy and intrepid I had to edit the pulseaudio file into playing 6 channels. Fair enough. In Jaunty, in addition to this, I had to enable mic line as output. It got harder every time. Now with Karmic Koala I can't seem to find out what they messed up, but my sound system isn't working, I edited the config file but can't seem to find the mic as output option(or it's equivalent).

Any help or insight would be greatly appreciated 

PS: If anyone knows how to make Rythmbox quit with just the "x" button in the decoration it would also be greatly appreciated.
[/SIZE]

---

### Post by sigixv on 2009-11-01
Closing rhythmbox:

Tab "Edit" > plugins > status icon > status icon

change to "Always visible" instead of "owns window"

---

### Post by P4man on 2009-11-01
as for the mic output.. not sure but try installing gnone-alsamixer

---

### Post by JosephMarc on 2009-11-01
Thank you sigixv it works.

P4man : Alsamixer comes by default.

Anyone made his 5.1 system work under karmic?? Or has an insight on how to make it work?

---

### Post by JosephMarc on 2009-11-01
Ah sorry P4man got confused, alsmixer-gnome doesn't come by default.

I've tried enabling Line Jack mode and the 3 input sources but the settings aren't getting saved, each time they are reverted to default.

Any idea on how to fix this?

---

### Post by jackmetal on 2009-11-01
I'm right there with you!  I don't know what they've messed up this time either.  Like you said, it gets worse with each new release.  I've got 7.1, and the only thing producing sound are the front 2 speakers.  It's crazy!!  Worked fine in 8.10 (and even 9.04).

I've been searching for a while and thought I stumbled across a fix, but it didn't work.  If I find one, I'll let you know!

---

### Post by delaossa on 2009-11-02
Hello, I am also very interested in making the mic port works as line out:
The thing is that "mic as output" option has [disappear]("http://ubuntuforums.org/showthread.php?p=8197722") in the new karmic version of the alsamixer (in both gnome and terminal versions). 
Why? Any ideas about how to make this work again?
It is clear that it is possible, and there seems to be a lot of people affected by this issue.
In my case, due to a failure in the normal line out port, that was the only way to make my laptop sound through the speakers.
There are others who can not configure any more their surround system.

---

### Post by JosephMarc on 2009-11-03
Clearly there's an issue with 5.1 speakers in karmic(it's been three people complaining now), anyone care to help out? Maybe giving a tutorial on how to put sound the way it was back in jaunty would fix the problem. Anyone?

---

### Post by JosephMarc on 2009-11-03
I was able to get 4 channels to work till now, i typed : alsamixer in terminal and I've set "Line Jack" and "Mic Jack" as output. BUT :
My rear right channel is still disabled
My subwoofer SEEMS to work, but bass is choppy at best
This only worked for the time terminal was open, when i closed it everything reverted back to default.
Is there any way of making the changes permanent? (having a 4.1 is still better than a 2.0)

---

### Post by P4man on 2009-11-03
Does this help?

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/86656](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/86656)

---

### Post by JosephMarc on 2009-11-03
P4man : My issue is not with the sound card but with the way speakers are handled, my guess is that if I could enable the mic jack as output line I would get proper sound, but I wasn't able to do so.
Thank you for trying though.

---

### Post by P4man on 2009-11-03
> **JosephMarc said:**
> P4man : My issue is not with the sound card but with the** way speakers are handled,**

That is obviously a soundcard driver parameter. Not saying what i linked will solve anything, but its worth trying. Setting the 6ch parameter would make the soundcard  use mic as an output, how else would it output 6ch..

Anyway in Karmic if you want to try it it should be in 
/etc/modprobe.d/alsa-base.conf

---

### Post by JosephMarc on 2009-11-03
P4man : I tried, it didn't work.

What I really can't understand is how cannonical (or whoever is in charge of sound in ubuntu) decided to strip out such a crucial feature, it is really preposterous to do such a thing.

Anyway I'm kinda desperate right now, so any tips on making my 4.1 system which I was able to enable via alsa work without switching it on each time is welcome.

---

### Post by P4man on 2009-11-03
If you cant find a solution, file a bug report on launchpad.

I cant really help as Im an old fashioned "2 excellent speakers (and bassbox) is better than 6 mediocre speakers" guy ;)

---

### Post by JosephMarc on 2009-11-03
Ah well thank you for your time, seems a bug report has already been filed. I hope this gets sorted out quickly.

---

### Post by JosephMarc on 2009-11-04
I snooped around a little and it seems this new audio configuration that seems to be the source of my problems was copied from Fedora 11. Any idea on how to get the good old jaunty sound configuration?

---

