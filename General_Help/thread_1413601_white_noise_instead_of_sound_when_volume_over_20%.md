---
title: "white noise instead of sound when volume over 20%"
date: 2010-02-22
forum: General Help
---

### Post by cyprys on 2010-02-22
Hi,

[edited: It got worse, please read the 4th post.]

I use 64bit Ubuntu. Installed Karmic, sound worked. While I was watching a movie (720p MKV) in about half of it sound went "over-driven". When volume was under 4% the sound was almost clean but quite, when over 5-6% there was only a white noise and loud.

I reinstalled Ubuntu and it worked but now after a few months it happened again (also while watching 720p MKV).

I don't know what those commands gave before...
```
cyprys@greenshit:~$ lspci | grep audio
(there is no output)

cyprys@greenshit:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

cyprys@greenshit:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

I also did:
```

sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
sudo apt-get install ubuntu-desktop

```
Logged out, logged in, now the sound plays almost clean when the volume is under 20%.

1. How and where to configure it properly?
2. How to run some pulseaudio mixer or where to look for configuration files?
3. Is this some kind of bad frequency problem?

4. Why did it worked perfectly and broke suddenly during the normal system usage (watching a movie, nothing else)?

Cheers!

---

### Post by colobix on 2010-02-22
Could it be the front mic?
Open your volume controller and disable the front mic.
It should be right next to Microphone.

---

### Post by cyprys on 2010-03-29
[quote=colobix]Could it be the front mic? (...) Open your volume controller[/quote]Nope, mic's slot is empty and works perfectly. Ubuntu 9.10 doesn't have such thing as "volume control" for microphone. There's only one volume controller available after left-click on the system tray speaker.

I used to fix this problem by using "paconfig" (pulse audio config) script - I had to run it after every reboot and set the default settings.

After one of updates (don't know which one) the sound works without paconfig. However there's no audio in "lspci" or in whatever output I could think of. It doesn't stop the system tray speaker to popping up with the following info (after I place a mouse pointer over it and wait a second):
> Output: 100%
0.00 dB
CM6501 Analog Stereo
dB goes up when I force volume over 100% in sound preferences and goes negative when I set volume below 100%. Can't say it's solved permanently and this 0.00 dB doesn't conflict with anything because I didn't have time for movies since this issue but the sound seems to work anyway so I am marking this thread as solved.

---

### Post by cyprys on 2010-08-27
Basically this is what happens:

After install (10.04 64bit +updates) the sound goes well for months. Suddenly, sooner or later, something messes up (the driver?). It always happens when I'm watching a DVD or mkv. It's sudden, boom, and it happened. Without a warning. This time I've lost only vocal - only frequencies typical for human voice are noisy now and everything else plays normally (I can throw out a karaoke party, yuppie!). It sounds like there was a badly configured noise removal tool applied (I did that once with some music using Audacity, there were pitches and glitches, peeps, beeps, and so on).

I still can use paconfig and it helps but now I also have to decentralize the sound (a little more to the left or right speaker). When it's centralised the problem occurs.

Alsamixer doesn't help - it makes some change but somehow on "wrong" frequencies.

Yelp?

---

### Post by cyprys on 2010-10-03
I've just installed 10.10 Maverick and the problem persists.

---

### Post by cyprys on 2010-10-10
Bump.

I'm officially sick of it. Someone, please, tell me **how to reset Pulseaudio settings to complete defaults, just as it is after installing Ubuntu**. After using Live CD or fresh install it works great for some time, so I could easily make a script which would reset the settings, e.g. once a day.

[list]
[*]I tried to delete .pulse directory from my $HOME, didn't work,
[*]I tried to use paconfig to remove my Pulseaudio settings, didn't work,
[*]I tried to *sudo mv /etc/pulse/default.pa /etc/pulse/default.pa.original*, didn't work,
[*]I tried to *rm -r /etc/pulse*, well, let's say it didn't went well and neither did *sudo apt-get remove --purge -y pulseaudio* afterwards (I messed something big time and had to reinstall from CD but since it wasn't a fresh install the sound problem still exists).
[/list]

---

### Post by cyprys on 2011-01-16
I messed a lot with it and switched to ALSA, then back to Pulseaudio, then installed **LADSPA Plugin Multiband EQ** and tweaked it's settings. All that on october 2010 and for the time being it seems to work.

I do not consider this issue solved since I still don't know how to reset Pulseaudio settings to default in case the problem occurs again on LADSPA Plugin. Also when I switch the output back to Internal Audio Analog Stereo the problem is still there and since I installed LADSPA I can't control master volume on internal output any more. I will mark it solved after using fresh instal of Narval for few months without the problem.

---

### Post by kvcckid on 2011-01-17
> **cyprys said:**
> I messed a lot with it and switched to ALSA, then back to Pulseaudio, then installed **LADSPA Plugin Multiband EQ** and tweaked it's settings. All that on october 2010 and for the time being it seems to work.

I do not consider this issue solved since I still don't know how to reset Pulseaudio settings to default in case the problem occurs again on LADSPA Plugin. Also when I switch the output back to Internal Audio Analog Stereo the problem is still there and since I installed LADSPA I can't control master volume on internal output any more. I will mark it solved after using fresh instal of Narval for few months without the problem.

I have just won a battle with alsa; the result was I can now play audio over HDMI, but there is white noise/sounds like microphone feed back with all of my audio.

No Microphone is connected and it is disabled in sound preferences.

halp plox?

---

### Post by _sleeper on 2011-01-25
I had the exact same problem a long time ago, so long that I have forgotten about it. And a few weeks back it happened again and since then I struggled to find a solution, but to no avail. And then, bam, it came to me. I just needed to shut down my pc and turn off the power or pull the plug for a minute in order to eliminate any currency on the motherboard. And, tata! So I guess it's not a software issue rather a hardware one. 
Hope this helps.

---

