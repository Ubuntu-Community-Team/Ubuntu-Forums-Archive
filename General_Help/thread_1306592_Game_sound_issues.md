---
title: "Game sound issues"
date: 2009-10-30
forum: General Help
---

### Post by wildbillkelso on 2009-10-30
Hi all.

My sounds are fine in the OS, CD playback and online sound content are great. My problem is when I play games. In particular TORCS or Flightgear. The sound is sometimes fine to start with, and then soon gets a horrible distortion and unpleasant fuzzy sound. Other times it distorts all the time right from the start. Supertuxkart is fine though. I have not yet had the opportunity to try others yet. I did not have this problem with Hardy, Intrepid, or Jaunty, but have just installed Karmic. In case it is of any use, I am using the 64 bit version of Karmic, and used the 64 bit versions of Hardy Intrepid and Jaunty with no issues.

Any ideas, solutions, or pointing in the right direction would be greatly appreciated.

Many thanks.

Tim

---

### Post by grizato on 2009-10-31
I have the same problems in Karmic with Spotify and Yo-Frankie.

Anybody, please help!

---

### Post by wildbillkelso on 2009-10-31
Hi grizato.

I was using on board sound. I wondered if it was a driver problem so I installed an old soundblaster live soundcard I had in another machine, and still had the same problem. The on board sound is Intel chipset. I thought then that it must be an Openal problem, so switched TORCS to Plib sound. No change, still sounds nasty. I'm out of ideas. Its a shame realy because other than this problem, everything else is sweet. I like Karmic lots. Can't complain though its early days. Be great to get it sorted though.

Best regards.

Tim

---

### Post by MaxTesla on 2009-11-03
I have a 32 version of Ubuntu 9.10 and get the sameproblem with supertuxkart the sound starts fine but then after 30-60 sec it gets all messed up I would also like some help

---

### Post by Ardghal on 2009-11-04
Hi, I'm affected by the same problem, just like the OP said. Audio, video and other sounds work fine, but *some* games are affected by this. And this didn't happen in 9.04, it started happening after the upgrade.

Particularly, I saw it in the Penumbra games, Nexuiz and ZSNES emulator. No sound, or sound for 30 seconds then nothing, or horrible distortion. And it's likely that if that happens, the computer will **freeze** when I leave a game. On the other hand, Torus Trooper and FCEUX and others don't have a problem.

I though it may be fullscreen games, but I tried a few others and that didn't happen. Also didn't happen on Diablo 2 through WINE (it's the only WINE game I have installed to test it on :P).

Tried uninstalling Pulseaudio and reinstalling, but it didn't change anything. Also tried selecting other options in audio devices. but none fixed the problem... probably didn't need to mess with that, as it worked fine just before!

Any ideas? :|

---

### Post by HiImTye on 2009-11-04
have you tried it using ALSA rather than PulseAudio?

is it perhaps a CPU load problem? use TOP/HTOP to see your load (from a terminal, type in 'top') in top there will be a line at the very top that says 'CPUs:' and a percentile. if it is at 100% then it could be an issue of your CPU is being overloaded by other programs.

---

### Post by ell02 on 2009-11-04
I had sound stutter from an online game, then enabled simulteous output and that cured 99% of it.
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

---

### Post by Ardghal on 2009-11-04
> **HiImTye said:**
> have you tried it using ALSA rather than PulseAudio?

How could I try that?

[QUOTE=HiImTye]is it perhaps a CPU load problem? use TOP/HTOP to see your load (from a terminal, type in 'top') in top there will be a line at the very top that says 'CPUs:' and a percentile. if it is at 100% then it could be an issue of your CPU is being overloaded by other programs.[/QUOTE]

It's not my case, at least. The problem doesn't seem to be related to CPU load as far as I can tell. Light applications can cause the error, even if nothing else if executed. The *top* command shows everything is OK.

[QUOTE=ell02]I had sound stutter from an online game, then enabled simulteous output and that cured 99% of it.[/QUOTE]

That may help, but it shouldn't be necessary to go that way to fix it. I never used that option and sound worked just fine. Besides, the guide itself says Simultaneous Output may consume a lot of resources.

Thanks for the reply, though. :)

---

### Post by wildbillkelso on 2009-11-07
Hi all.

I just tried out Xubuntu 9.10 64 bit and everything is fine in TORCS and Flightgear. I think I will stick with it.

Hope this helps.

All the best.

Tim

---

### Post by lessmemorelove on 2009-11-14
i was having sound issues in these games with karmic, too. i found the solution that works for me. it allows dosbox, wine, and openal games to all play nice. this idea has been taken from other places on the forums and cobbled together.

1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1

2.  add your user name to the pulse audio family with this command in terminal:

sudo adduser $user pulse-access

substitute your user name in for $user

3. edit /ect/openal/alsoft.conf as root add the following line under the lines talking about drivers

drivers = oss

4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

5. reboot

you should be good to go

---

### Post by Ardghal on 2009-11-14
Thanks for the suggestions. Now I have better sound, but not on every program. I'll explain what I did so far.

> **lessmemorelove said:**
> 1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1

Doing that disabled sound altogether. I had to change it back to recover sound on the system.

[QUOTE=lessmemorelove]2.  add your user name to the pulse audio family with this command in terminal:

sudo adduser $user pulse-access

substitute your user name in for $user[/QUOTE]

I had to add me to that group through the GUI (Users and groups) because inputting that command said that *the user already existed*, so nothing happened. I have yet to restart and see if that does anything.

[QUOTE=lessmemorelove]3. edit /ect/openal/alsoft.conf as root add the following line under the lines talking about drivers

drivers = oss[/QUOTE]

When I open that with gedit from the terminal, it shows a completely blank file. So, it either does not exist, or it is blank. Should I still add that line?

[QUOTE=lessmemorelove]4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed[/QUOTE]

This is the one step I **could** do so far. Now there's sound both in Gens and ZSNES, plus, if I run Nexuiz through the file *nexuiz-linux-686-sdl* rather than *nexuiz-linux-686-glx*, it has flawless sound now. However, with the other one it behaves the same. Same for the Penumbra games. Of course, since I couldn't do everything, I'm not surprised.

Almost forgot! Installing *libsdl1.2debian-pulseaudio* demanded that I uninstall *libsdl1.2debian-alsa* and *fceux* (a NES emulator package). Now I can't install it back because I wants to reinstall alsa and unistall pulseaudio. Why is that? Maybe I'll try installing it from the source rather than a package. It's weird it won't work without those conditions. I used to work all great before the upgrade! :\

If you can, clarify those steps. Otherwise, thanks for the help. :)

---

### Post by Micaelus on 2009-11-14
I am having the same issue, both with WINE games as well as Neverwinter Night's Linux client. I am running the 64-bit Karmic.

After trying this series of instructions, the performance in the games did not change, but the opening Ubuntu sound was crackly, which hadn't happened before.

Also, is there a way to change from PulseAudio back to ALSA and use 9.04's sound without reverting back to Jaunty?

---

### Post by comet on 2009-11-14
I too am still having the same problems. Running 64-bit 9.10. The sound on games like OpenArena just start off really distorted and fuzzy. Games through Wine used to have fuzzy sound too, but now it has just disappeared completely. System sounds seem to work fine. Just all my good 3D games don't work right. :cry:

---

### Post by lessmemorelove on 2009-11-15
ok. sorry. the alsoft.conf file ony exists if you have games that use it. those games should be supertux, scorched earth 3d, supertuxkart, maybe others. i always open nautilus as root and browse to the files i want to edit and edit them with gedit.

as for "1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1" if you do that and you have added your user name to pulse-access, you should have sound at reboot.

as for removing pulse? yes it is possible. just use synaptic and remove the pulseaudio package and make sure you have alsa-base and alsa-oss installed. warning: there are downsides to that option so i suggest keep trying to get pulse to work.

i hope this clarifies. maybe somebody else can see a step i am missing here? i will keep trying to help because i know how annoying this can be.

---

### Post by Ardghal on 2009-11-21
> **lessmemorelove said:**
> ok. sorry. the alsoft.conf file ony exists if you have games that use it. those games should be supertux, scorched earth 3d, supertuxkart, maybe others. i always open nautilus as root and browse to the files i want to edit and edit them with gedit.

Alright, then. Should I install something so that it's created or is it not necessary to make sound work?

[QUOTE=lessmemorelove]as for "1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1" if you do that and you have added your user name to pulse-access, you should have sound at reboot.[/QUOTE]

OK, after adding myself to that group, changing that value from 0 to 1 didn't do any harm, as far as I could tell. Nexuiz through the glx executable still gets sound cut off after it starts; however the Penumbra games don't get sound cut off, as I've played for ~20 minutes and it did happen. Before it happened a lot sooner. It still gets noise when some sounds play... but less. Does that make any sense?

I'd also like to keep Pulse Audio, rather than replace it. :) Now it's not too big a deal, but it'd be nice to find out what's causing this!

-------

Correction: after another restart, sound was gone completely. Changing that value to 1 just shuts sound down for good. Maybe there're some more Pulse Audio packages that need to be installed for it to work properly?

---

### Post by lessmemorelove on 2009-11-25
You can always try to uninstall pulse audio through synaptic and install alsa-oss and its dependencies. reboot. test sound. then reinstall pulse audio leaving the alsa-oss installed.

---

### Post by Ardghal on 2009-11-27
> **lessmemorelove said:**
> You can always try to uninstall pulse audio through synaptic and install alsa-oss and its dependencies. reboot. test sound. then reinstall pulse audio leaving the alsa-oss installed.

OK, just tried that. After removing PA and adding alsa-oss (it didn't ask me for any dependencies) and rebooting, the *big* games worked again. The lack of sound or choppy sound went away and they had perfect sound. No more problems! Though the smaller games, plus the emulators didn't have sound at all. Neither did Audacious.

Then, I added PA back, without removing alsa-oss, as you said, and now those games that started working, have all the problems back, and the games that had no sound without PA, work again. :S

So, basically, this was a useful task. :D Apparently, PA doesn't work well with some games, but ALSA does. If it was possible to have ALSA work for those games, but leave PA for the ones that need it (and work well with it), that'd be great, 'cause it feels the solution is not too far!

Can it be that having both sound systems is causing the problem? It seems I did have some alsa package installed already, since I wasn't asked for dependencies.

Another solution would be to leave everything to ALSA, but seeing how removing PA left things without sound, I'd need directions to do that too. :\

---

### Post by lessmemorelove on 2009-11-28
which libsdl1.2debian do you have installed? i have the pulseaudio one. i also have both pulse and alsa-oss installed (needed to make wine, supertuxkart, scorched earth 3d, and others work right) if you have some of those games installed have you tried the alsoft.conf trick yet?

here are some extra packages i have installed. 
alsamixergui
padevchooser 
paman 
paprefs 
pavumeter 

i used alsamixer to make sure sound is turned up and not muted in alsa stuff.
i used paprefs to make sure all my networked sound was off. (not desirable if you are streaming sound i guess, but i dont do that.)

also, did you edit /etc/default/pulseaudio as root to make pulseaudio a daemon? (not good if you have a multi-user login screen. make sure if you do this trick you need to add your user name to the pulse-access group.)

edit: found this from another thread on pulse audio problems in karmic: [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by Ardghal on 2009-12-04
OK, here's what I got from trying all solutions.

I had installed *libsdl1.2debian-esd*, instead of *libsdl1.2debian-pulseaudio*, but that's probably because the .deb package of **fceux** requires it. There's also a *libsdl1.2debian-all* option, but it sounds almost too good to work. Now I have installed the *libsdl1.2debian-pulseaudio* one.

Also, I added *alsamixergui*, *padevchooser* and *paprefs*, which I didn't have. But I couldn't change anything in alsamixer or the dev chooser. The first one doesn't have anything to change, and the second already complies with what you said.

I am added to the *pulse-access* group already. When I tried running PA as a daemon, there just was no sound whatsoever.

Then, I tried the link you posted. There were many things to try there. Tried most of them (not the kernel thing, for example), even installing that alsa updated package.

I also installed **SuperTuxKart**, but it didn't add anything to alsoft.conf (it's blank). Maybe I'll try installing one of the other games later. Running it showed that it's also affected by the problem. After a while, sound goes off completely in the game.

Now, after trying all those things, it has sound, so does **ZSNES**, but **fceux** is all laggy because of the sound (turning it off in the game config makes it all smooth again!), and the other games are still affected by their respective problems. So, that's it. :( So far, what made more sense was something in the wiki link that suggested that the problem lies with the libsdl1.2debian-* packages. I checked the properties of all games, but **Penumbra** ('cause it's installed differently and doesn't show on Synaptic) and all require that package. Even **VisualBoyAdvance**, which I don't use 'cause it lags horribly. Could it be related to that? :| ...and what could be done? o_O

---

### Post by Blue_Wolf on 2010-01-06
Hey I have sound Issue's with Super tux 2 and some other games, not sure what the problem is at all but the sound starts sound distorted right when I start a game in general. Is there anyway to fix this? It's really bugging me

---

### Post by Vladislav Mkrtychev on 2010-05-10
> **lessmemorelove said:**
> which libsdl1.2debian do you have installed? i have the pulseaudio one. i also have both pulse and alsa-oss installed (needed to make wine, supertuxkart, scorched earth 3d, and others work right) if you have some of those games installed have you tried the alsoft.conf trick yet?

here are some extra packages i have installed. 
alsamixergui
padevchooser 
paman 
paprefs 
pavumeter 

i used alsamixer to make sure sound is turned up and not muted in alsa stuff.
i used paprefs to make sure all my networked sound was off. (not desirable if you are streaming sound i guess, but i dont do that.)

also, did you edit /etc/default/pulseaudio as root to make pulseaudio a daemon? (not good if you have a multi-user login screen. make sure if you do this trick you need to add your user name to the pulse-access group.)

edit: found this from another thread on pulse audio problems in karmic: [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Hello,

Thanks for the link. I had the same problems with the sound in AM.
I just installed the libsdl1.2debian-pulseaudio package (which uninstalls the libsdl1.2debian-alsa package) and sound is great now!

Thanks!

---

