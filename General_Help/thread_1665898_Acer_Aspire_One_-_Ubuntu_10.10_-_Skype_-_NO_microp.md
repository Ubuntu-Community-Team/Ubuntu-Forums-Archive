---
title: "Acer Aspire One - Ubuntu 10.10 - Skype - NO microphone??"
date: 2011-01-12
forum: General Help
---

### Post by Roasted on 2011-01-12
I'm running Ubuntu 10.10 desktop edition on my Acer Aspire One. The onboard microphone doesn't work at all in Skype, no matter what options I select. It works in audacity and sound recorder, though, so I have to wonder what in the world is wrong with skype. There's not a lot of audio options in skype, mostly just what sound server (only one option - pulseaudio) and whether or not skype is allowed to adjust volume levels - either way with it enabled or disabled, didn't make a difference.

Anything I can do?

---

### Post by Roasted on 2011-01-13
[http://ubuntuforums.org/showpost.php?p=10147128&postcount=28](http://ubuntuforums.org/showpost.php?p=10147128&postcount=28)

Can anybody confirm if this fixed it for them? I'm at work but I'm going to give it a shot when I get home... I'm also curious if anybody has anything to add that would explain why and how the Acer Aspire mic is the one problematic thing with Ubuntu and netbooks that I've been reading about.

---

### Post by Roasted on 2011-01-13
Ran home quick at lunch and grabbed the netbook. Here's my findings. I have an Acer Aspire One 8.9" netbook for what it's worth.

I installed the PAVUControl application or whatever it was in the software center. Under the input tab, there are TWO sliders - left and right. I'm not sure why there are two sliders for a microphone tab.

Here's the thing. If I take one of the sliders to 0, leaving the other at 100%, the microphone works fine in Skype. If I leave both at 100%, no mic in Skype. It doesn't matter which slider is 0 and which slider is 100%, either way ONE needs to be off for it to work. I noticed once I lowered the one slider, even without testing in Skype, suddenly it began showing me an active level of what the microphone would be recording, and sure enough when I did a test call on Skype it worked fine.

I also noticed if I go into my regular sound preferences and change the input level, it instantly matches the left/right sliders in the PAVUControl application, which them matched = not working. So if you change the level in your "sound preferences" for your input device, you have to go back and adjust the independent levels of the input device in PAVUControl.

Question of the day - can anybody tell me... why are there two levels for input device and what do they do? And why doesn't Skype work with them effectively?

---

### Post by legend_gibby on 2011-02-23
magic ive been looking for this for ages.....finally got it to work cheers bud

there is alot of crackeling in the background tho but im sure ill manage to get around that!!!

any luck on finding out about why it has to be done this way!!!?

Cheers james

---

### Post by justindisgustin on 2011-05-11
I'm having this same issue with my Acer Aspire One D250.  I can confirm this workaround.  I don't really get why I had to dig all over the web for something so simple (seems like it should maybe be in Skype's documentation), or why the settings weren't just set that way to begin with.
Anyway, thanks for the information!  I will repost in my little blog over at mypcchronicles.blogspot.com with due credit so that hopefully more people (myself included) can find it more easily.
Thanks! :)

---

### Post by justen_m on 2012-12-30
Thanks! This solved the same problem I was having with Ubuntu 12.10 and Skype 4.1.0.20 on my Acer Aspire One (AOA-150, an antique I got in 2008!)

In Skype, make sure to go to Sound Devices and uncheck the box that allows Skype to automatically adjust your mixer values or it will undo your changes. You can also launch pavucontrol directly from Skype.

---

