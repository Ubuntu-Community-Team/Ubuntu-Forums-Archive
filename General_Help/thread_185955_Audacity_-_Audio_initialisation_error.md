---
title: "Audacity - Audio initialisation error"
date: 2006-06-01
forum: General Help
---

### Post by ketsugi on 2006-06-01
I used to be able to run Audacity. Now, however, I'm getting an error dialog on startup (see the screenshot).

[quote="Audacity"]There was an error initializing the audio i/o layer. You will not be able to play or record audio.

Error: host error.[/quote]

Everywhere else in Ubuntu/Gnome sound is working properly; only Audacity has problems.

Any ideas?

---

### Post by BitTorrentBuddha on 2006-06-01
This is because Audacity doesn't use ALSA or ESD, therefore if you don't have a sound card with hardware mixing, it won't be heard if you are using any other programs that are accessing the card, to fix this you should probably get a new sound card with hardware mixing, I've heard good things about the Sound Blaster Live!, available for less than $10 on ebay.

---

### Post by Ramses de Norre on 2006-06-01
```
sudo aptitude install aoss && aoss audacity &
```
Start audacity with this second part of the command everytime (change the menu entry).

---

### Post by BitTorrentBuddha on 2006-06-01
aoss doesn't fix it for audacity. When trying to play any sound, the following three lines are spat out. ```
Pa_SetLatency: could not SNDCTL_DSP_SETFRAGMENT
Pa_SetLatency: numBuffers = 5, framesPerBuffer = 1024, powerOfTwo = 12
Pa_SetupDeviceFormat: could not SNDCTL_DSP_SETFMT
```

---

### Post by ketsugi on 2006-06-01
[QUOTE=BitTorrentBuddha]to fix this you should probably get a new sound card with hardware mixing, I've heard good things about the Sound Blaster Live!, available for less than $10 on ebay.[/QUOTE]

Getting a new sound card on my laptop is rather out of the question, I'm afraid...

Also, as I mentioned, Audacity used to work (I'm not sure what triggered it to stop working) so it's not likely to be my sound card's problem either.

As for the other suggestion:

```
ketsugi@Asahara:~$ sudo aptitude install aoss
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package matching "aoss".  However, the following
packages contain "aoss" in their description:
  alsa-oss
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Running "aoss audacity" gets me into Audacity without errors, but after opening a file, I get this error when clicking on the play button:

> Error while opening sound device. Please check the output device settings and the project sample rate.

---

### Post by Scunizi on 2006-06-04
I'm having the same issue.  I had been running Dapper Flight 5 upgraded through June 2.  I decided to do a fresh install (problematic ..for another post).  After the fresh install audacity stopped working.  I get the same error "There was an error initializing the audio i/o layer.  You will not be able to play or record audio.   Error: Host error."  This never use to show up so I know the sound card is ok.  This is happening on the i386 & i686 kearnal.

Edit:  After doing some checking in Audacity's preferances I noticed Audacity doesn't recognize the system's default audio setup.  Under Edit/Preferances/Audio I/O there is nothing in the boxes and the blank space can't be changed.  When I go to System/Preferances/Multimedia Systems selector everything is listed just fine.  Audio output input from mic tests just fine.  However I did notice that even if I turn the mic off with the volumn control properties and leave the switch on for playing the mic through the speakers, the mic is still active.  The only way to silence it is to turn the volumn control down all the way.  If I simply put a check mark on the "pass through to the speakers" switch I can't hear the mic but it is still giving the system input.  Not good when you're recording something (if I could) that's playing from the net.

---

### Post by benobi on 2006-06-04
Same problem, with a Dell XPS m140 laptop.

"There was an error initializing the audio i/o layer. You will not be able to play or record audio."

And I also do not plan to change my soundcard !

---

### Post by Scunizi on 2006-06-04
I just picked up something in another thread that fixed audacity for me.  That is until the next reboot then you have to go through it again.  Open a terminal and type "killall esd".  Suddenly audacity will recognize the system setup for sound and work.  If I have to do this every time I may have to add it to the launcher.  It would seem much easier than going through all the gyrations I read in other threads.

---

### Post by ketsugi on 2006-06-04
Hm, that worked for me. Thanks.

---

### Post by VortexICS on 2006-06-06
Something that worked for me without having to kill ESD is 

# System -> Preferences -> Sound
# Sound preferences

General Tab -> Sounds for events (Un-Checked)

After that, you will obviously not be able to hear gnome sounds, but it is much better than having to run scripts or commands in order to have Audacity working.

---

### Post by menaar on 2006-06-08
That worked for me as well.

Thanks!!

---

### Post by m4rk4 on 2006-06-08
FYI: [http://audacityteam.org/wiki/index.php?title=LinuxIssues](http://audacityteam.org/wiki/index.php?title=LinuxIssues)

---

