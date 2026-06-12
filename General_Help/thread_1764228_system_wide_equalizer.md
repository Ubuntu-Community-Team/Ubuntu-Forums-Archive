---
title: "system wide equalizer"
date: 2011-05-21
forum: General Help
---

### Post by oklinuxyo on 2011-05-21
plz i need one that work
i use google but i only find something for pulseaudio, i dont have it i use kubuntu and it sound compication much :<

so how i get system wide equalizer??? i find one called alsafreq but it very old and not work anymore (at lest not with my xonar st)

this is really anoyging becaus i have very bass lacking headphone and soundcard so i ned boost bass plz

---

### Post by oklinuxyo on 2011-05-21
bump

---

### Post by oklinuxyo on 2011-05-21
helo i cant use linux becaus of this...................

---

### Post by linuxinstalledfromhdd on 2011-05-21
I recommend some bass boost headphones

---

### Post by oklinuxyo on 2011-05-21
> **linuxinstalledfromhdd said:**
> I recommend some bass boost headphones
pleas stay serious!!
this is realy anoyin im audiophile with hq stuff in my pc but the drivers in linnux not supported 100% so i cant fine tune sound to what i want....
pelase anyone help me?
i can give cooki :)

---

### Post by oklinuxyo on 2011-05-22
ok bump

i try to install alsaequal again, but again nothing happen when i use equalizer in alsamixer or alsamixergui
```
naike@Naike-Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ST [Xonar ST], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: ST [Xonar ST], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```hmm something is wrong, how do i select analog output? i dont want digital or multichannel, i ned analog (for headphone and speker)
how i add this to list? linux should really invest to get beter driver....

this is my asoundrc file
```
ctl.equal {
  type equal;
}

pcm.plugequal {
  type equal;
  # Modify the line below if you don't
  # want to use sound card 0.
  slave.pcm "plughw:1,0";
  # or if you want to use with multiple applications output to dmix
  # slave.pcm "plug:dmix"
}

pcm.equal {
  # Or if you want the equalizer to be your
  # default soundcard uncomment the following
  # line and comment the above line.
# pcm.!default {
  type plug;
  slave.pcm plugequal;
}

```

---

### Post by oklinuxyo on 2011-05-22
bupm

---

### Post by Frogs Hair on 2011-05-22
See the first link about using the Pulse Audio Equalizer in Kubuntu . The second link is for using the Alsaequal plug-in . Make sure you have the correct version of the PAEQ if you decide to try it.  

[http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html](http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html)


[http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)

---

### Post by oklinuxyo on 2011-05-22
> **Frogs Hair said:**
> See the first link about using the Pulse Audio Equalizer in Kubuntu . The second link is for using the Alsaequal plug-in . Make sure you have the correct version of the PAEQ if you decide to try it.  

[http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html](http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html)


[http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)
i tried alsaequal acording to instructions and i edit the parameters int he config but still not work no afect when use eq

i wil read this blog entry thnks

---

### Post by oklinuxyo on 2011-05-22
ok nice try btu this pulse audio rqualizer not work with natty 
omg linux is only problem os nothing work nothing included ok nice its free but i also get windows for free from school ty

so pelase i ned other option, very bad support here i must say this os is really suck if no support
maybe nerd os but not for normal ppl

---

### Post by Frogs Hair on 2011-05-22
[http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)

---

### Post by oklinuxyo on 2011-05-24
> **Frogs Hair said:**
> [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)
thank u very much i folowed some other pulso audio eq from oficial ubuntu fosum, it didnt work
i will try this today thanks

---

### Post by oklinuxyo on 2012-10-09
hi
ok i know this is old thread but... i thougt i try linux again
i install ubuntu now, at least now compiz work with ati card okay :))
but still no equalizer for linux?? i search google and i find all the same info like last time
pulseaudio equalizer bla bla alsaequal
still the same problem

pulse equalizer "work" but when i activate it everything is low volume and super distorted
its like i would listen at 10000% volume but it only is 10% volume
why is it so hard to make eqauzlier for linux
maeby instead of creating "software center" for super retard people who cant use terminal or packet manager you should make system wide equalizer that is supported by ubuntu developer?

have anyone heard any news on equalizer or find anything that work for asus xonar essence st? the card is low bass (and my headphones too) so i need equalizer to boost bass volume

thanks

---

### Post by sienile on 2012-10-09
Have you tried searching in the Software Center for "mixer"? There's tons of them. Try them until you find one you like.

---

### Post by oklinuxyo on 2012-10-10
ya i have
i dont need mixxer i need equalizer
i want to change how it sounds not how loud it is!! :(
mixxer only control volume, input and output etc
but thanks for suggestion anyone else can help me???

---

### Post by oklinuxyo on 2012-10-10
ok please halp me

so i download alsaequal (libasound2-plugin-equal)
and i make a file in home directore ".asoundrc" in there i write:
```
pcm.!default {
  type hw
  card 1
}

ctl.!default {
  type hw
  card 1
}

ctl.equal {
  type equal;
}

pcm.plugequal {
  type equal;
  slave.pcm "plughw:1,0";
}

pcm.!default {
  type plug;
  slave.pcm plugequal;
}
```

and when i do aplay -l i get
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ST [Xonar ST], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: ST [Xonar ST], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

is my config file correct? cos when i use alsamixer -D equal
nothing happens when i use the levers
should i restart my pc?? what numbers should I use?
i think hw card 1 is correct cos card 0 is my gpu hdmi
but what i set at plughw:1,0? is the 1,0 like "card,device" oe what???
please help me and say if i need to restart each time i try different setting or just save config file???? :guitar:

---

### Post by Frogs Hair on 2012-10-10
I installed 12.10 Beta 2 and the Pulse Audio Equalizer still works fine. :confused: Make sure the Alsa plugin is up to date and compatible.   

This is from the Debian forum which Ubuntu is based on.[http://forums.debian.net/viewtopic.php?f=16&t=47899&start=15](http://forums.debian.net/viewtopic.php?f=16&t=47899&start=15)

---

### Post by oklinuxyo on 2012-10-10
> **Frogs Hair said:**
> I installed 12.10 Beta 2 and the Pulse Audio Equalizer still works fine. :confused: Make sure the Alsa plugin is up to date and compatible.   

This is from the Debian forum which Ubuntu is based on.[http://forums.debian.net/viewtopic.php?f=16&t=47899&start=15](http://forums.debian.net/viewtopic.php?f=16&t=47899&start=15)
for me it also work "fin" but audio sux and distortion 100%
:((( do u use hedphones

---

### Post by Frogs Hair on 2012-10-10
I have to modify  presets with the Pulse EQ because otherwise the sound is distorted because of my sub woofer .  I use external speakers but I don't have to change settings for headphones.  

The presets boost some signals and have to be modified for each system. I  base everything on the rock preset .

when it comes to Youtube, some videos are recorded at very high levels and sound distorted with or without the EQ  but I don't find that often.

---

### Post by oklinuxyo on 2012-10-11
duno why u dont have the same problem like me
i havent try my spekers cos i dont want to listen with them i like hedphone more

i give this nerd os another try but still all the same problems like over 6 years ago
no progress in 6 years??? wtf
i try to adjust all frequenzies separate but it just sound muffled and distorted like horse *** :mad::mad::mad:

im sry for language but i cant imagine anyone who take music more seriously can use this os when sound is so bad? no comprendo
i try to look for alternative sound server but pulseaudio is the only choic eihave sigh..

theres not even working equalizer for alsa
i try this: [http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)
i try it with many different config and on 2 different machine (one with onborad soundcard( but no help not working
each time i boot to windows and i hear login sound i get ear orgasm because sound work there with EQUALIZER
:( maeby in 10 years linux will support equalizer
or meaby i should study nerd language and program my own equalizer for linux 
no wonder ppl dont use linux cos theres so many problems
i know its mainly hardware makers fault cos they dont make proper driver (why???) for this os

linux very nice idea etc but too bad hardware makers only care for money
meaby some day i will be billionare and i buy all hardwar mekers and tell them to suport this os

in meantime, anyone else got tips to fix my problem?
tahnks

---

### Post by sienile on 2012-10-11
This thread got me interested in using an equalizer myself. I got the Quantal release of the Pulse Audio Equalizer. It works great in Precise. Give it another shot. It's probably been improved since you tried it last.

The best preset I've found that _didn't seem to cause distortion_ was "Party". "Club" was also pretty good, but I prefer the fuller bass of the "Party" preset. **Of course, tweaking the preset to your own liking is a must for those as picky about their music as you seem to be.**

Hope it works out for you.

---

### Post by oklinuxyo on 2012-10-11
i have same version
and i have used all lever/slider separetely in minimal increments but still the sound just is distorted and muffled like i would have some "effect" to sound like a concert 10km away (like dobly effects)

ok not 10km but still bad :(
i always listen to music when im ok pc, so i cant realy use linux now cos the sound is bad still
id really like to use linux cos its more of a challenge and i like the customizeablity but i have other things to do so i have my limits
i can spend many hours and days to search for a solution ok but not months to create my own solution
and i assume the solution is hard cos no one has create da working equalizer


[IMG]http://s12.postimage.org/h3lkaeesb/eqa.png[/IMG](ok someone remove my image........................................................ wtf it was only like 10x10px)
this is my setting in windows look how much i need so boost bass for the music to sound "little more bass than normal"
its cos of my soundcard and hedphone both have lacky low freq :(
with onbouard sound i dont need equalizer that much but its lik listen to music with nose poop in the ear lol

---

### Post by sienile on 2012-10-11
If bass distortion is the problem, have the rest of your levels set below the 0dB line and the bass slightly above. It may be that the Linux EQs have a higher top end and it's beyond what your headphones can do.

---

### Post by oklinuxyo on 2012-10-12
look
its dirstorted
but not the bass isnt high

it has to be the equalizer becaus in windows i can set all bass to full +20dB and listen so niger rap with mega bass and i get no distortion on full colume
i tried wht u suggest and it work now better thankd

maybe if i offset more than -4dB it will work even beter duno lol
weird system error
i also try the equalizer on my natbook with other hedphones and the same problem (intel something integrate audio meaby?)
i even get distortion when i listen normal muci like toto africa

---

### Post by wildmanne39 on 2012-10-12
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

