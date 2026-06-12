---
title: "ALSA.. I can only assume that no one knows..."
date: 2010-01-26
forum: General Help
---

### Post by Danwhelan on 2010-01-26
All 

I can't believe that with everything that the new version of Ubuntu has achieved that it's being let down by something as simple as the sound... 

Networking, wireless, firewalls, stability.. all those things I could understand... but the sound? 

I have read hundreds of posts over the last two weeks detailing unresolved sound issues.. yet no one seems to have an answer. 

This was my last post

[http://ubuntuforums.org/showthread.php?t=1388643](http://ubuntuforums.org/showthread.php?t=1388643)

Annoyingly the sound comes on everyonce in a while, then blips off, sound on start up, no sound here, sound there, no mic. 

It's so random. 

Now people say... oh just reinstall the OS... that solves nothing and certainly does not provide us with an answer for when the next person comes along with the same problem. 

It's clearly a big issue to anyone running the realtek intel  sound combination which equates to about 20% of us I would say.. probably more... and with people dropping Windows left and right... we can expect a lot more. 

There must be some one that has the answer..... trust me, it will solve a lot of peoples problems... 

Dan

---

### Post by t4thfavor on 2010-01-26
there is a whole page dedicated to intel hda sound, I cannot remember the link, but I posted it to somebody yesterday.

Try going through that list, as I believe there is a section on intermittant sound.

---

### Post by lavinog on 2010-01-26
What was wrong with the default drivers?
What made you think you needed to compile your own ALSA driver?
How old was the guide you were following?
Pulseaudio is more likely to be the cause of many sound issues.
At this point, reinstalling the os would be the quickest, less painful way to go about this.
If a fresh install does not work, file a bug report, or see if a bug report was already filed.

Are you using karmic?

---

### Post by Danwhelan on 2010-01-26
Favor - thanks... I'm fairly sure I would have gone through this... however please let me have the link... anything that might help. 

Lavinog 

[I]What was wrong with the default drivers?  
[/I]
The sound was very bad, intermitant and there was no mic... also no hardware shown in the Gnome sound preferences... only dummy output 0db 

[I]What made you think you needed to compile your own ALSA driver?
[/I]
I didn't - I downloaded the lastest set from ALSA with help from another forum member 

[I]How old was the guide you were following?
[/I]
Brand new 

[I]Pulseaudio is more likely to be the cause of many sound issues.
[/I]
Pulseaudio is a possible problem, however I've seen no solutions that focus directly on that issue... only the editing updating and replacement of the ALSA package.

[I]At this point, reinstalling the os would be the quickest, less painful way to go about this.

[/I] Sorry - I agree but no... how are any of us going to learn anything if we turn away from the problems... that exact fix is why no one here really knows what is wrong 

[I]If a fresh install does not work, file a bug report, or see if a bug report was already filed.
[/I]
Hundreds of bug reports have been filed... I've been fighting with this for a few weeks now. 

Karmic koala 9.10 which I am officially renaming... "the quiet one" 

Dan

---

### Post by t4thfavor on 2010-01-26
Its here
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I don't know if it will help, but I guess it's worth a try.

I stay away from compiling drivers if at all possible.

---

### Post by Danwhelan on 2010-01-26
Thanks for posting that... however I've covered all of those steps in detail.. 

Many thanks 

Dan

---

### Post by Danwhelan on 2010-01-27
speaker-test -Dplughw:0,0 -c2

Working!!! Would you believe it... it works here.. no where else though. 

Danny:~$ amixer |grep Mic
Simple mixer control 'Mic Boost',0
Items: 'Mic' 'Internal Mic' 'Line'
Item0: 'Mic'
Simple mixer control 'Internal Mic Boost',0

Mic is dead... 

However if I run alsamixer from the console... then F4

I get 

   <Line In >   Mic Boos    Capture     Digital     Input So    Internal 

Now input so was not there before.... and if I navigate to it I get three options above it. 

Mic internal and line... but no level indicator... just the text. 

Any ideas anyone???

---

### Post by Danwhelan on 2010-01-29
guiltless bump :-)

---

