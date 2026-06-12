---
title: "Problems with sound, printing, and wireless"
date: 2009-09-12
forum: General Help
---

### Post by itsjareds on 2009-09-12
Don't get me wrong -- I love Ubuntu, and I'll continue to use it. I just have a few problems with hardware/software that I'd like to get figured out. It'd be great to see ALL of my major concerns (which are minor enough to still use Ubuntu) fixed just through this thread :) so I'll list them.

1. Sound
	I've always had the same problem with sound in Ubuntu, ever since 8.04. The sound works, but it will only work for one process at a time. This seems to be a problem with mixing. I normally don't care about mixing, but when I'm using Firefox and want to listen to an online Flash music streamer, then load a Java program that also uses sound, I will only get sound from Flash apps. I can have as many Flash apps running fine with sound -- but any other process that tries to use sound will either simply NOT use it, or it'll hang then crash. Basically, if I have sound in Flash, I can't use it in Java, and vice-versa.
	I have a built-in Intel HDA soundcard.

2. Printing
	I don't print often, but sometimes I will have to print out papers for school. I have yet to find a driver that works in Ubuntu for my Canon i860, or a workaround in these forums. The closest I have gotten is using a foreign linux driver, but this still does not print and freezes at "Retrieving printer data.."

3. Wireless card
	I recently switched to a new wireless card after [frustratingly trying to figure out](http://ubuntuforums.org/showthread.php?t=853762) an awful older one. Now I have a Rosewill RNX-EasyN1, which has official linux drivers. After doing some tweaking, I finally got the driver working (did not work to simply install from source without modifying). My only problem with this wireless card is that the driver doesn't seem to work with any kernel upgrades. I don't know if this is something I did by mistake, but the wireless card only works when I boot into a 2.6.28-13-generic kernel. I have the 2.6.28-15-generic kernel installed, but booting into this kernel I don't get any connectivity. The ra0 wireless interface doesn't appear either. Do I need to reinstall my driver for every single kernel upgrade?


I hope someone can enlighten me on some possible answers! Ubuntu is a wonderful release when it works with all of your hardware.

Thanks

---

### Post by stderr on 2009-09-12
Hehe you're right, this is quite ironic :) I'll post back about wifi in a bit, I have to go and check a few things first. However, with regard to sound, the 'problem' may be Pulseaudio.

Could you try setting all your sound settings to ALSA in System->Preferences->Sound, and then killing all instances of Pulseaudio?

```
ps aux | grep ulse
```

everything aside from the **/usr/bin/dbus-launch** entry. You'll likely need

```
sudo kill -9 THE_PID
``` for some of them.

edit: Regarding wifi, I just tried 2.6.28-13-generic with no success. It looks like we could be experiencing different wifi issues. I'll try reverting to NetworkManager as I assume you're using that.

---

### Post by whitethorn on 2009-09-12
I'm not sure but I have to reinstall my graphic drivers with every kernel, unless I use the drivers in the repositories, so you probably have to reinstall your drivers with each kernel, or just keep using the old one.  

As to your sound problem, what kind of pulse plugin are you using.  Pulse, Alsa, ...  I also have an intel HDA and it works fine with Pulse.  Pretty much pulse sits on top of alsa and does the mixing it's sometimes a little hard to get up and running though.  Do you have surround sound, or a seperate bass?

As for printing can't help you there

---

### Post by itsjareds on 2009-09-12
> **stderr said:**
> Hehe you're right, this is quite ironic :) I'll post back about wifi in a bit, I have to go and check a few things first. However, with regard to sound, the 'problem' may be Pulseaudio.

Could you try setting all your sound settings to ALSA in System->Preferences->Sound, and then killing all instances of Pulseaudio?

```
ps aux | grep ulse
```

everything aside from the **/usr/bin/dbus-launch** entry. You'll likely need

```
sudo kill -9 THE_PID
``` for some of them.

I tried as you said and still the same issue. I've tried this method before without success.

> **stderr said:**
> edit: Regarding wifi, I just tried 2.6.28-13-generic with no success. It looks like we could be experiencing different wifi issues. I'll try reverting to NetworkManager as I assume you're using that.

Perhaps. I am actually using Wicd network manager, version 1.6.2. You might want to try Wicd if you're not getting a connection at all. I'm not sure about NM but you can set a custom interface to connect to -- in our case, ra0.

> **whitethorn said:**
> I'm not sure but I have to reinstall my graphic drivers with every kernel, unless I use the drivers in the repositories, so you probably have to reinstall your drivers with each kernel, or just keep using the old one.

That might be it. I was hoping I wouldn't have to do that, as it was a pain to install my driver the first time. Do you recommend any faster way to do this?

> **whitethorn said:**
> As to your sound problem, what kind of pulse plugin are you using.  Pulse, Alsa, ...  I also have an intel HDA and it works fine with Pulse.  Pretty much pulse sits on top of alsa and does the mixing it's sometimes a little hard to get up and running though.  Do you have surround sound, or a seperate bass?

I was using PulseAudio because I'd gone searching through these forums trying to find a solution, giving me the same info you're giving me. PulseAudio didn't do the trick, sadly. I even installed an extra PulseAudio device chooser and volume control. Right now I'm using Alsa as according to stderr. All of my sound settings are:

Sound Playback - ALSA
Music and Movies - ALSA
Audio Converencing - ALSA
Default Mixer Tracks - HDA Intel (ALSA Mixer)

What do you mean by surround sound? I just have built-in PC speakers, but I usually plug in my headphones (stereo).

---

### Post by stderr on 2009-09-12
> **itsjareds said:**
> I tried as you said and still the same issue. I've tried this method before without success.
That's annoying. I have one rig which I have to disable Pulse and use ALSA on, and that largely mixes fine, with the occasional exception of Flash through Firefox (and using Epiphany normally works fine with Flash - haven't bothered debugging it). The rest of the rigs use Pulse without issue. 
> **itsjareds said:**
> 
Perhaps. I am actually using Wicd network manager, version 1.6.2. You might want to try Wicd if you're not getting a connection at all.
I am using a source Ralink driver, with file edits applied, and to reliably connect need to either 
  a) set ra0 in interfaces, and manually issue /etc/init.d/networking restart after boot, or
  b) remove ra0 from interfaces & configure WICD to use a static IP with ra0, and either
  ..i)  continually boot until it connects, or
  ..ii) tell WICD to disconnect, execute /etc/init.d/networking stop, and tell WICD to connect once more. 
I haven't found a reliable auto-connect solution yet ;)

edit: I wouldn't have thought we'd need to re-compile the driver for each kernel upgrade unless the upgrade changes something major WRT wireless in a non-backwards-compatible sense, but could be wrong. Let us know if that works for you! If not, I wonder what the tail end of your dmesg log says with regard to rt28xx_init etc. edit: & your wicd log too...

---

### Post by itsjareds on 2009-09-12
It may be the same problem I have with this card (and my old one). After Ubuntu restarts, it doesn't seem to "turn off" my wireless cards. I have to manually unplug/replug the wireless card sometime inbetween the computer turning off and booting up Ubuntu again. This seems to reset the link. I get the same issue you do when I don't replug it.

---

### Post by itsjareds on 2009-09-12
Seems like reinstalling on the newer kernel fixed it. That will get annoying really quickly when I have to keep reinstalling. I wonder if I can uninstall the old driver installation, and have the driver still work on the old kernel.

P.S. - I found a really good ReadMe file in Rosewill's version of the RT3070STA driver (not the RT2870, but I've heard the two drivers are similar). It defines all the different variables in the .dat file, and it gives step-by-step instructions on how to install it with various configurations. I posted it in the attachment if you're interested.

edit: I uninstalled the driver that went with my previous kernel, and I am able to get a connection on both kernels. I'm beginning to think I just compiled the driver incorrectly the first time around, and now I have it right.

---

### Post by stderr on 2009-09-12
Nice, glad you got that sorted! It'll be interesting to see if further kernel updates cause issues or not. BTW, that readme is very similar to the RT2870STA README in Ralink's tarball.

I have switched over to NetworkManager, and so far all boots have resulted in a working connection - although I'd put money on it falling over soon ;)

Is it just Flash sound you're struggling with when you're running ALSA, i.e. totem + rhythmbox + ... works OK? If so, when you launch firefox in a terminal, no obvious error messages pop up about missing shared libs or any such thing? 

Also, maybe some (nasty) workarounds like installing alsa-oss and flashplugin-nonfree-extrasound may help?

---

### Post by gordintoronto on 2009-09-12
> **itsjareds said:**
> 2. Printing
	I don't print often, but sometimes I will have to print out papers for school. I have yet to find a driver that works in Ubuntu for my Canon i860, or a workaround in these forums. The closest I have gotten is using a foreign linux driver, but this still does not print and freezes at "Retrieving printer data.."



Did you see the instructions at 
[http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860](http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860) 

It's very old....

---

### Post by itsjareds on 2009-09-12
> **stderr said:**
> Nice, glad you got that sorted! It'll be interesting to see if further kernel updates cause issues or not. BTW, that readme is very similar to the RT2870STA README in Ralink's tarball.

Oh, must have missed it when I looked through Ralink's.

> **stderr said:**
> I have switched over to NetworkManager, and so far all boots have resulted in a working connection - although I'd put money on it falling over soon ;)

Glad it's working :D [for now]

> **stderr said:**
> Is it just Flash sound you're struggling with when you're running ALSA, i.e. totem + rhythmbox + ... works OK? If so, when you launch firefox in a terminal, no obvious error messages pop up about missing shared libs or any such thing?

Also, maybe some (nasty) workarounds like installing alsa-oss and flashplugin-nonfree-extrasound may help?

Hmm, I *never* use totem/rhythmbox, but I did just to try that out. It actually does work with both of them playing a song at the same time. So now it must definitely be a Flash issue. That helps narrow it down a lot :)

I'll scour the forums for a fix.

> **gordintoronto said:**
> Did you see the instructions at 
[http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860](http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860) 

It's very old....

Yeah, those were the only relevant instructions I could find. That was the one where I installed a foreign driver but it didn't really work. Thanks for searching though :)

---

### Post by stderr on 2009-09-12
Ah yes, no sound with Flash nonfree is a common issue. Unfortunately I can't say the solutions are always the same, but there are quite a number of solutions/workarounds out there. NB: If you try installing flashplugin-nonfree-extrasound, it may be worth grabbing libasound2-plugins and libasound2 as well.

Hmm, did you get any useful output in the cups logs when you tried the canon driver?

---

