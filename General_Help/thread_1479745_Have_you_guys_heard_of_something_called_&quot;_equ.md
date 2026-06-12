---
title: "Have you guys heard of something called &quot; equalizer &quot; ???"
date: 2010-05-11
forum: General Help
---

### Post by soona86 on 2010-05-11
Hi,
I just wanna know where I can find a media player with an equalizer feature attached. The sounds on Ubuntu are flat as a board!

Hasn't anyone you noticed that? If you have, how did you deal with it?

---

### Post by Dessicus on 2010-05-11
Banshee has an equalizer (press Ctrl+E)

---

### Post by sarin_cv on 2010-05-11
latest version of Amarok(2.3) has an equalizer... before that I was using audacious... without an equalizer it is hard to enjoy music... :)

---

### Post by Rasa1111 on 2010-05-11
VLC has an equalizer
Guayadeque has an equalizer
Songbird has an equalizer
banshee has an equalizer...

take yer pick. 

personally, I think VLC and Guayadeque are best.
Songbird is really good to, but they are stopping the Linux gig i guess. 

my sound is amazing in Ubuntu though, even with no equalizer enabled/on.

---

### Post by soona86 on 2010-05-11
> **Rasa1111 said:**
> VLC has an equalizer
Guayadeque has an equalizer
Songbird has an equalizer
banshee has an equalizer...

take yer pick. 

personally, I think VLC and Guayadeque are best.
Songbird is really good to, but they are stopping the Linux gig i guess. 

my sound is amazing in Ubuntu though, [COLOR="Red"]even with no equalizer enabled/on.[/COLOR]

Enabling equaliser!!! Is there a way to enable equaliser in Ubuntu?? I mean is it in the system or you meant in a media player software?

====================================

Thanks Dessicus, sarin_cv "Yes, tell me about it! :)" and finally thanks to Rasa1111

But just a general question : does it matter if the program was for a different desktop environment ? like KDE or something ?

---

### Post by Dessicus on 2010-05-11
KDE apps will install and run just fine in gnome.

---

### Post by ngrieb on 2010-05-11
Audacious 2 and most others.

---

### Post by wojox on 2010-05-11
Even [Rhythmbox]("http://live.gnome.org/RhythmboxPlugins/ThirdParty#A10_Band_Equalizer") has one.

---

### Post by Rasa1111 on 2010-05-11
> **soona86 said:**
> Enabling equaliser!!! Is there a way to enable equaliser in Ubuntu?? I mean is it in the system or you meant in a media player software?

====================================

Thanks Dessicus, sarin_cv "Yes, tell me about it! :)" and finally thanks to Rasa1111

But just a general question : does it matter if the program was for a different desktop environment ? like KDE or something ?


 Hiyah, 
Well,  i just took a look around for a 'system wide equalizer".. and found this~ 
what do you think?
[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136843&d=1258652669[/IMG]

Might be worth a shot. 

 

 But in my post, I did mean an equalizer in the actual software/programs themselves. 

also, you can use KDE apps in GNOME~ no problem. 

 hope it helps.

---

### Post by Rasa1111 on 2010-05-11
if you end up using either VLC or Guayadeque...

here's a couple screenshots of the equalizers.. lol
circled in black.

---

### Post by soona86 on 2010-05-11
> **wojox said:**
> Even [Rhythmbox]("http://live.gnome.org/RhythmboxPlugins/ThirdParty#A10_Band_Equalizer") has one.

I downloaded the plug-in. Do you know how to install it? It's a bz2 file

---

### Post by soona86 on 2010-05-11
> **Rasa1111 said:**
> if you end up using either VLC or Guayadeque...

here's a couple screenshots of the equalizers.. lol
circled in black.

lol it's okay I can find it's location, thanks for the help :)

Unfortunately VLC doesn't work well on my system; dunno why..I installed it already but the sound is a little glitchy (I don't know if it's spelling is right; but it's like the word "laggy" when you play an online game; you know stops then plays then stops then plays again. lol I know the description is funny!) even if the euqalizer is not enabled :S

So no VLC for me :(

My system is Ubuntu 8.04 Hardy Heron, does the PulseAudio work on it?

I think I'll try guayadeque & PulseAudio; If it's compatible with my system version because the topic you've given me says tips for other versions except mine see this quote :

> Note 2: This script requires PulseAudio 0.9.19 or later to function properly, which has the following implications:

    * Jaunty users: your version of PulseAudio is outdated - you must upgrade. I recommend Luke Yelavich's PPA.
    * Karmic users: you do not need to upgrade PulseAudio. If you are already using the 0.9.20 packages from the semi-official Ubuntu Audio Dev PPA, the equalizer will continue working.
    * Lucid (testing) users: you have the latest version of PulseAudio - no further action is necessary.


Thanks a lot Rasa1111 for your help :) I'm really grateful :)

---

### Post by soona86 on 2010-05-11
> **Dessicus said:**
> Banshee has an equalizer (press Ctrl+E)

I pressed ctrl+E nothing happened :(

---

### Post by Dessicus on 2010-05-11
The version of Banshee in the Hardy repos must be an older one. Try installing from the [PPA]("https://launchpad.net/~banshee-team/+archive/ppa")

---

### Post by soona86 on 2010-05-12
> **Dessicus said:**
> The version of Banshee in the Hardy repos must be an older one. Try installing from the [PPA]("https://launchpad.net/~banshee-team/+archive/ppa")

what's PPA??

when i did the steps in the link u gave me..there was an error in the middle of the process (don't remember what it was)..afterwards it said "warning this could allow a malicious individual to take control of your system" or something like that

i undid the steps anyways...

---

### Post by Dessicus on 2010-05-12
PPA = Personal Package Archive - overview [here]("https://help.launchpad.net/Packaging/PPA")

To install Banshee from PPA:
First uninstall the version of Banshee you already have.
Next open the terminal and type:

```
sudo gedit /etc/apt/sources.list
```

Scroll down to the bottom and enter these two lines exactly:

```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu hardy main
```

Now save and close the file. Then back in the terminal type:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
```

Finally to install Banshee type in the terminal:

```
sudo apt-get update && sudo apt-get install banshee
```

---

### Post by jodiefoster on 2010-05-12
I think VLC and Guayadeque are best.
Songbird is really good to, but they are stopping the Linux gig i guess.  


[green world](http://www.squidoo.com/bestgreenplanet)

---

