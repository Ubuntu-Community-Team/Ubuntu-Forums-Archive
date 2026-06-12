---
title: "No sound from Line In"
date: 2010-09-14
forum: General Help
---

### Post by brunolabs on 2010-09-14
Hi.

I'm using Ubuntu 10.04 and I can't get any sound from Line In.
After checking Sound Preferences menu I can see from the "Input" tab that the correct input is selected and the Input level bar is moving. But no sound comes out.

What should I do?


Thanks!

---

### Post by brunolabs on 2010-09-24
Bump.

Anyone have this problem?

---

### Post by lkjoel on 2010-09-24
> **brunolabs said:**
> Hi.

I'm using Ubuntu 10.04 and I can't get any sound from Line In.
After checking Sound Preferences menu I can see from the "Input" tab that the correct input is selected and the Input level bar is moving. But no sound comes out.

What should I do?


Thanks!
Line in is not for output.

---

### Post by brunolabs on 2010-09-24
> **lkjoel said:**
> Line in is not for output.

I know that...
What I want is to get sound from output (speakers) when I input a sound signal in Line In.

---

### Post by lkjoel on 2010-09-24
I think only MS Windows does that.

---

### Post by brunolabs on 2010-09-24
> **lkjoel said:**
> I think only MS Windows does that.

Always done this in previous Ubuntu versions.:(

---

### Post by KeyserSoze93 on 2010-09-24
You mean you plugged an audio device with a line-level input into the blue plug on your soundcard?

Yes that should work - if it doesn't I'll not be upgrading.

Has your volume control got a "switches" section? Some soundcards have a toggle between blue = line-in and blue = rear/centre speaker.

---

### Post by brunolabs on 2010-09-25
> **KeyserSoze93 said:**
> You mean you plugged an audio device with a line-level input into the blue plug on your soundcard?

Yes that should work - if it doesn't I'll not be upgrading.

Has your volume control got a "switches" section? Some soundcards have a toggle between blue = line-in and blue = rear/centre speaker.

Yes I did plug in a mp3 player to the line in port (blue) and I can't get that sound to the computer speakers (green).

I'll post the screenshot with the Sound Prefs menu. As you can see there is the sound signal active and not muted. And still I get no sound from it. :(

---

### Post by brunolabs on 2010-09-26
Bump for help.

This is a big issue for me.


Thanks.

---

### Post by KeyserSoze93 on 2010-10-01
See my comment about some soundcards having a switch between blue = line-in and blue = rear speaker.

I don't run 10.04 so the volume control is different - you'll have to explore it to find the switches section.

---

### Post by brunolabs on 2010-10-02
The switch configuration I have selected is the right one for my hardware and speaker system.
But I also tried every other possible combination (just in case) and still no sound.

---

### Post by brunolabs on 2010-10-07
Any more ideas please?

---

### Post by brunolabs on 2010-10-09
Bump.

Need help please.

---

### Post by dixonstalbert on 2010-10-14
hello

I am having the same problem.

I am setting up a new Motherboard with ALC892 HD sound.

I can plug in an mp3 player in blue jack and volume indicator moves with input. I can also use Sound Recorder  and record line-in and playback output. but there is no live monitoring of line-in while I am recording it like on my old computer. 

I have tried the various fixes for alsa-base.conf for snd-hda-intel but no help.

I am getting an error on startup in kernel.log of:

```
 8.941751] hda_codec: ALC892: BIOS auto-probing.
[    8.947828] Too many connections
```

I have been googling to find why i am getting this error but nothing so far...
I will post back if I find a solution

---

### Post by jkxx on 2010-10-14
First of all are you able to record sound from the line-in? If yes, then skip the next step.

If no, go to [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound") and follow the guide to install OpenSound (OSS) instead of Alsa. Do not remove PulseAudio, however. This will get your input and output working.

To actually get sound from any one port to go to another port, you need JACK. See this page [https://help.ubuntu.com/community/UbuntuStudio/GettingStarted]("https://help.ubuntu.com/community/UbuntuStudio/GettingStarted") on how to install Jack, then this one [https://help.ubuntu.com/community/HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration") for configuration tips.

Basically once you have your inputs and outputs working, Jack will give you a GUI app that allows you to drag inputs to outputs with the result being that audio from the line in comes out of your speaker jack. It allows you to do much more than that as you'll discover as you use it more.

Good luck and keep posting if you have problems.

---

### Post by brunolabs on 2010-10-14
I'll give JACK a try, but in previous Ubuntu versions it wasn't necessary, worked out of the box.

---

### Post by brunolabs on 2010-10-18
> **jkxx said:**
> 
Basically once you have your inputs and outputs working, Jack will give you a GUI app that allows you to drag inputs to outputs with the result being that audio from the line in comes out of your speaker jack. It allows you to do much more than that as you'll discover as you use it more.

Good luck and keep posting if you have problems.


Thanks for helping me with this.
Well, using JACK solved the problem I have been posting about. But with JACK activated I can't get no system sound (sound from apps like rythmbox or VLC).
I thought it might be any missing connection in JACK connections menu, but now I selected all combinations possible and still no sound. I can hear the sound from line in though.

---

### Post by lkjoel on 2010-10-19
> **brunolabs said:**
> Thanks for helping me with this.
Well, using JACK solved the problem I have been posting about. But with JACK activated I can't get no system sound (sound from apps like rythmbox or VLC).
I thought it might be any missing connection in JACK connections menu, but now I selected all combinations possible and still no sound. I can hear the sound from line in though.
Have you tried OSS 4.x?
It is active.
The guide is in Fix your sound! in my signature.

---

### Post by brunolabs on 2010-10-25
Still haven't tried OSS 4.x.

Just curious if anyone can listen from line in directly to output out-of-the-box, or if it is a problem with my hardware. It really should be an option enabled by default like in previous Ubuntu versions.
If it isn't, why does the input menu in sound prefs have a mute button?? It's always mute!!

---

### Post by Schrute Farms on 2010-10-25
I had a heck of a time figuring out how to record from line in on my machine.  I could hear the sound, but I couldn't record it.  It turned out that I didn't have my settings right in alsamixer.  And, apparently my card can be a bit of a pain.  So it can be done with Ubuntu right out of the box.
I was able to do it keeping ALSA, but only installing alsamixer, so I don't know anything about JACK.

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                         F1:  Help               &#9474;
&#9474; Chip: CA0106                                         F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Capture [dB gain: 0.00, 0.00]                  Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;     L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       Line in     i2s in       &#9474;
&#9474;    CAPTURE     -------     CAPTURE     -------                               &#9474;
&#9474;    100<>100    100<>100    100<>100       0                                  &#9474;
&#9474;  <  Capture  > AC97 Aux    AC97 Line   AC97 Mic   Analog Sour Digital Sou    &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```
That is what the settings are for my card in alsamixer.  Right now I am listening and capturing vinyl with Audacity.  Of course, your settings may vary, hopefully this may help.

---

### Post by brunolabs on 2010-10-26
> **Schrute Farms said:**
> I had a heck of a time figuring out how to record from line in on my machine.  I could hear the sound, but I couldn't record it.  It turned out that I didn't have my settings right in alsamixer.  And, apparently my card can be a bit of a pain.  So it can be done with Ubuntu right out of the box.
I was able to do it keeping ALSA, but only installing alsamixer, so I don't know anything about JACK.

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                         F1:  Help               &#9474;
&#9474; Chip: CA0106                                         F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Capture [dB gain: 0.00, 0.00]                  Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;     L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       Line in     i2s in       &#9474;
&#9474;    CAPTURE     -------     CAPTURE     -------                               &#9474;
&#9474;    100<>100    100<>100    100<>100       0                                  &#9474;
&#9474;  <  Capture  > AC97 Aux    AC97 Line   AC97 Mic   Analog Sour Digital Sou    &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```
That is what the settings are for my card in alsamixer.  Right now I am listening and capturing vinyl with Audacity.  Of course, your settings may vary, hopefully this may help.

I have the inverse problem. I can record but can't listen.

Checked my alsamixer and it appears to be with the right settings.

Guess I have to give OSS a try.


Thank you all for the help.

---

### Post by brunolabs on 2011-01-03
Hi there!

Can anyone with the same issue tell me if this functionality is enabled in Ubuntu 10.10?
Or if it going to be in 11.04?


Thanks.

---

### Post by donovan.thompson on 2011-02-20
I've just came into this same issue. I can use apps like Skype and video chat, but when I try to hook another device to my line in and listen to it, I don't get any sound.

Like others, I can open the sound prefs and see the bars moving, indicating that the sound is getting into the machine but it's just not coming out.

Anyone figured out what the issue is yet? I'm running Ubuntu 10.10

---

### Post by kpoole on 2011-03-02
High.  And I am,  I just solved your and my problem.

I was setting up a second machine and wanted to direct the line-out from the second machine, which won't be on continuously through the first machine which is on pretty much all the time so the speakers are attached to the first machine.

The solution I found was to install GNOME ALSA Mixer.  As soon as that was installed and I ran it I could see that the Line-in was muted.  Uncheck the Mute box and voila, she is magically playing the sounds that you already know are reaching the line-in jack.

Where the heck one is expected to unmute the line-in from the tool that's already there I have no idea.  I looked for such a thing, left right and centre and plain couldn't find it.

Good luck.

---

### Post by Neovos on 2011-03-28
> **kpoole said:**
> High.  And I am,  I just solved your and my problem.

I was setting up a second machine and wanted to direct the line-out from the second machine, which won't be on continuously through the first machine which is on pretty much all the time so the speakers are attached to the first machine.

The solution I found was to install GNOME ALSA Mixer.  As soon as that was installed and I ran it I could see that the Line-in was muted.  Uncheck the Mute box and voila, she is magically playing the sounds that you already know are reaching the line-in jack.

Where the heck one is expected to unmute the line-in from the tool that's already there I have no idea.  I looked for such a thing, left right and centre and plain couldn't find it.

Good luck.

can confirm that this worked for me. This happened after an update and what was working normally just stopped working even though I could too see the sound bar moving and nothing else changed.

For me, in gnome-alsamixer, I unchecked the "mute" button and moved the slider up in the "Line" column; back to normal.

---

### Post by brunolabs on 2011-04-11
> **kpoole said:**
> the solution i found was to install gnome alsa mixer.  As soon as that was installed and i ran it i could see that the line-in was muted.  Uncheck the mute box and voila, she is magically playing the sounds that you already know are reaching the line-in jack.

tyvm! :)

---

### Post by Neovos on 2011-04-11
....however....

it seems to re-mute itself when I resume from suspend. Anyone else having this issue?

---

### Post by brunolabs on 2011-04-15
> **Neovos said:**
> ....however....

it seems to re-mute itself when I resume from suspend. Anyone else having this issue?

I have a desktop pc, so I don't need to use suspend. Tried to do it to check your problem but the computer wakes up all messed up. Can't help you on that.

Don't know why this major bug isn't fixed by now... :(

---

### Post by davesinger on 2011-04-22
I had the same issue after installing 10.10.  Jack didn't work, GNOME ALSA Mixer, worked once, but after a crash and reinstall it didn't.  QAmix, on the other hand worked on first try.  Perhaps some software works better on some machines.

FWIW, I really don't know much about what I'm doing, but I can report what worked.

---

