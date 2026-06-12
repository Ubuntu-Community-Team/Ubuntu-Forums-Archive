---
title: "Start again from the top... Sound... Help... please..."
date: 2010-01-29
forum: General Help
---

### Post by Danwhelan on 2010-01-29
This has been going on for weeks now... please please please some one must know the answer to this... 

Running Karmic 9.10

1 - Acer Aspire

2 - The sound was working prior to me playing around... however the mic was not working.... not volume down... not working. 

I followed the following steps 

Extracted the latest version

Compiled 
 
./configure
make
sudo make install

Configured alsa-base.conf using sudo gedit - filename 
 Added the following line to the end of /etc/modprobe.d/alsa-base.conf
 
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

To complete the disaster I rebooted

All this seemed to go off with out a problem.. as in there were no errors that I noticed... however I am from the school of never assume... and I assume that as things are not working that there must have been some sort of error. 

I'm a little worried about un-installing things as the first time I set the system up I have an issue removing some blackberry software and ended up removing the desktop and a whole load of other stuff... 

I've now realised that the version I got wasn't the latest and downloaded the most recent version installed without problems. 

Now... zero sound.... except in Firefox! Firefox sound is there. In fact after investigation it's sound from video files, and flash. 

Which makes it even more annoying. 

GNOME sound shows Dummy Output 0.00db - yet sound in FF 

Various other things / clues 

Alsamixer functions well as a program... but like the labour party actually does nothing... there is no control of the sound at all it's either on full volume or off

Alsa conf - again runs through and picks the sound card... sets it up, says OK... then... no sound still dummy output 

Alsa force-reload produces 

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release. (approx 35 times) 

ALSA mixer - key F4... mic is set to capture in red.. so something is working.... but it's not the Mic 

Mic source only gives me the option of front mic.... on the pre 9.10 versions this was a problem for ACER... since no one has answered a acer mic Q for about 8 months I have to assume that this is still the case. 

Later on it's giving me mic options, and mute mic..

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

I've the ALSA driver right - I think... were realtek ALC268 and Intel 8280ih

I've tried every type of model=acer etc  eg aspire / 3stack 

Hardware is seen by the OS... 

I've tried it all... trace my history back if you think I'm not trying.... I'm not some bone head that sits and posts... then bumps and bumps until some one does it for me... What I have tried would not fit in to one post... and trust me I have read them all... 

But I need some help from some one that really knows what they're talking about. 

Please... anyone... 

Any ideas anyone???

---

### Post by quixote on 2010-01-31
Looks like you've already tried pretty well everything.  Sound in linux can be a real mess.  (I believe it's the manufacturers' fault, but whatever.)

I'm a sound noob myself, so the only thing I can really do is point you to the links that helped me.  (I'm not sure you haven't covered all that though.)  
For troubleshooting: [help.ubuntu.com/community/SoundTroubleshooting#Loading%20a%20working%20sound%20configuration](help.ubuntu.com/community/SoundTroubleshooting#Loading%20a%20working%20sound%20configuration)

For any and every configuration and codecs issue: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Sometimes the snd-intel-whatnot drivers cause problems which are solved just by commenting them out.  Also, from your error message, there's clearly a kernel module not being loaded and without that, the OS has no idea how to play any sound.  If it were me, I'd try just reinstalling the whole sound setup.

If you do decide to do that, you may want to just use the next version of Alsa, which, stupidly, is not the version in the repositories.  There's a script [here]("http://ubuntuforums.org/showthread.php?p=6589810") which makes it easier to maintain the changes after kernel upgrades, or there's a fully manual method [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/"). Both of these are for jaunty, but I don't think sound has changed all that much between jaunty and karmic. (??)

(Re your troubles with suddenly uninstalling the whole desktop: that happened to me once too.  The problem is that for reasons known only to God, the gnome devs decided to make ubuntu-desktop a dependency of all kinds of programs.  So when you select a package to uninstall, carefully check the list of other programs that will also be uninstalled.  If it includes ubuntu-desktop, you can't uninstall it. :(.)

---

