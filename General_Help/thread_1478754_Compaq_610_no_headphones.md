---
title: "Compaq 610 no headphones"
date: 2010-05-10
forum: General Help
---

### Post by Bucky Ball on 2010-05-10
Hi all,

At wit's end. I have been screwing around with sound since Skype didn't love Pulse. Anyway, went on a wild goose chase for a couple of days trying to get a USB headset working with Skype, which I achieved, then I was informed today not required but built in mic and speaker was. Hmm. So, I succeeded in screwing things up when really didn't have time to fix it and now completely stumped. 

Problem: Speaker works fine but front headphone socket now dead. Cuts out speaker but no sound. Headphone socket essential for user's day to day computing.

Tech details. Compaq 610 running Ubuntu Hardy 64bit. 

Results of  cat /proc/asound/card0/codec#* | grep Codec

```
Codec: IDT 92HD71BXX
Codec: Generic 11c1 ID 1040
```
* Preferences in System->Preferences->Sound all set to Autodetect except sound capture which is set to alsa. 
* System->Preferences->Default Sound Card is set to: Intel (other option Pulse).
* Option added to  /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=generic
```Any other relevent details gladly supplied!

I have followed every howto and attempted every tweak out there and nothing has worked for me to get this headphone socket alive again. It was working fine before. Bottom line:

HELP! I am stumped and need to get on with other things. :)

---

### Post by Bucky Ball on 2010-05-12
Incidentally, from lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

This is really starting to drive me crazy! Any ideas greatly appreciated. I have tried more fixes and now the Pulseaudio server is working but the headphones still not. Can't see anyhow to turn up or unmute on any mixer. so ..... :(

---

### Post by Bucky Ball on 2010-05-12
Here's something. Pulseaudio Volume Control input and output device is:

ALSA PCM on hw:0 (STAC92xx Analog) via DMA

I have some USB headphones plugged in which worked before all this and they are not working either. Only output front speaker, no recognition I have a headset in at all. !!!

Seems like Alsa and Pulse are sorted but when I right click the playback stream in the volume control and 'Move Stream' it only shows the ALSA PCM description above and gives no option for the USB headset (as described in this thread, post #5: [http://ubuntuforums.org/showthread.php?p=6229529](http://ubuntuforums.org/showthread.php?p=6229529))

Help!

---

### Post by bville09 on 2010-05-12
There is an option in the sound menu that enables different sound ports (and even usb speakers, phones, etc.) to process sound, you just need to change the aplification settings. Unfortunatley I don't exactly have a mental image of what it says, but it does work (I use it for my htpc, to switch between tv speakers, the surround sound speakers and a pair of akg headphones).

I'm on Fedora at the moment, so can't really find these options to give more detail, but it's something like that.

edit: oh wait, yes I can. (gotta love gnome's universal programs)
it's on the "Output" tab in the System > Preferences menu, under the "Connector" menu. It's best to change it to Analog Output (LFE) / No Amplifier for pc speaker (or in my case the tv speakers), and Analog Output / No Amplifier for anything else.

---

### Post by Bucky Ball on 2010-05-12
Thanks but fixed. Pulse working and everything seems normal. Big tip? In Pulse Volume Control, start a playback stream and while it is going, right click and 'Move Stream', and move it to the device you want to use. After I restarted the machine (not logged off) all was good so I started all my sound apps and just moved the stream to the USB headset. Easy as in the end!!!

I will find the page later but it was a matter of installing the 32bit stuff and some other things that did the trick. The sound server started working immediately after. More when I get home ... :)

---

### Post by Bucky Ball on 2010-05-15
Just to tie this off, this is what worked for me. I hunted for hours and this was the only page that really mentioned installing 32bit packages. Anyhow it worked after a restart and Pulse Volume Control, right click Playback stream (when you have one going) and 'Move Stream ...'. And good luck to all who sail in her ...

[http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html)

---

### Post by Bucky Ball on 2010-05-16
Reopening thread! Switched on machine this morning, no changes made at all, mic not working on USB headset! All was fine when I switched the machine off last night.

Honestly, this is getting ridiculous! Such a straightforward requirement has taken me hours to figure out and I'm still not there! Sheesh.

ANY suggestions more than welcome. Everything else works fine but regardless of what I do, can't get the mic working again. As I say, was fine last night. The software goblins maybe tweaked something while I slept just to keep me annoyed.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! (That's me slowly going bonkers.)

* Note: Pulse Volume Meter works fine and tells me the mic is working fine, just not getting into Skype for some reason. When I make a test call I can hear the mic is working and see it on the volume meter for the input device. On skype playback of my recorded message nothing but a hiss. Whacked. Can't figure that out.

---

### Post by Bucky Ball on 2010-05-17
Started off with no headphones and ended up with no mic! Ha! Oh well, seems to be all fixed now and this is how.

After following this link:

[http://www.ubuntugeek.com/pulseaudio...rdy-heron.html]("http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html")

... as mentioned, all worked well, but then suddenly the mic died. So after beating my head against a wall again, I stumbled across this thread tonight:

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

As I am using 8.04, I followed the trail from "After I installed 8.04...". The mic and everything else is working fine now and there were a few steps and packages that weren't in the first link.

Could have been a combination of the two. Worked for me ... so far! Good luck.

---

