---
title: "Overall bad sound quality in Ubuntu :( ?"
date: 2010-06-28
forum: General Help
---

### Post by DenDum on 2010-06-28
_**Hello everybody**_

I'm a bit new in Ubuntu, but i am about to get a hang in it.

I have previous use karmic koala and the version before that ( cant remember the name for that )
on my old computer and now i am using ubuntu 10.4 on my new computer.

Ever since I installed Ubuntu for the first time, I noticed that the sound quality wasnt... the best..
there isnt so much wrong with it, but like that this example.

I played a FLAC file with some headphones ( thru Ubuntu ) and the sound quality sucked.. and then i played a mp3 file ( with an ipod ) and the sound quality was much much much better than the FLAC file. 

I tired to play an HD movie over youtube, where on Windows XP it sounds perfect, but with Ubuntu it kinda sux..

the mp3 ( Ipod / windows XP ) is still better, than anything that is being played in Ubuntu.

This is with allmost every sound format i have tried. No matter if i play it with Rythmbox or vlc or some other player, the sound is wrong.

I cant describe how it sounds.. but it is like it is going with a low frequency... or it is compress some how... 
Ever since i tried Ubuntu for the first time Ive noticed that something was wrong, but couldnt never really put my finger on it.

I have dual-booted with windows XP and the sound in XP is really, really good compared to Ubuntu. 

I've looked for some hours at the net, but couldn't find anything that matched my problem.
[U][B]
Can anyone please help me :'( ?

I really love Linux ( ubuntu ) but i need my music ![/B][/U]



Regards


A Ubuntu Noob.

---

### Post by JC Cheloven on 2010-06-28
Hi, and welcome.

There should not be any problem regarding sound quality, if your soundcard is properly supported. Some people do some serious audio work using ubuntu.
So, my tentative guess is some kind of support problem for your soundcard in alsa/linux/ubuntu. 

You can find out your soundcard model opening a terminal and typing 
```
lspci
```
(look for your detected audio device).
Then have a look here to see the support status of your card, along any possible hints:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Hope this helps.

---

### Post by stderr on 2010-06-28
Hello DenDum, welcome to Ubuntu!

In order to figure out what's going wrong, we'll need to know a little about your system's audio hardware and drivers. Could you open a Terminal, execute the following and post the output:

```
cat /proc/asound/cards
cat /proc/asound/modules
aplay -l
pulseaudio --check && echo $?
```

The following might also be helpful:

```
pulseaudio --dump-conf
pulseaudio --dump-modules

```

---

### Post by DenDum on 2010-06-28
> **stderr said:**
> Hello DenDum, welcome to Ubuntu!

In order to figure out what's going wrong, we'll need to know a little about your system's audio hardware and drivers. Could you open a Terminal, execute the following and post the output:

```
cat /proc/asound/cards
cat /proc/asound/modules
aplay -l
pulseaudio --check && echo $?
```The following might also be helpful:

```
pulseaudio --dump-conf
pulseaudio --dump-modules

```


Thanks !

I tried to run the first code in the terminal and this came up:

```

xadgs@XaDgs-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ffc000 irq 16
xadgs@XaDgs-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
xadgs@XaDgs-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
xadgs@XaDgs-desktop:~$ pulseaudio --check && echo $?



```And for the second code, this came up:

```


xadgs@XaDgs-desktop:~$ pulseaudio --dump-conf
### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-0.9.21/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 8
default-fragment-size-msec = 10
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000
xadgs@XaDgs-desktop:~$ pulseaudio --dump-modules


```

And JC Cheloven, about the soundcard, I ran the command in the terminal:


```


xadgs@XaDgs-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:01.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
xadgs@XaDgs-desktop:~$ 


```
But I dont think it isnt anything with my soundcard to do.

On XP, the sound i flawless, but in ubuntu it could be better :/

To be sure, i asked my friend ( if he could hear anything wrong - he could, clearly ) and also borrowed his HD headphones and the difference, between FLAC and mp3 was... yeah.. :(

---

### Post by stderr on 2010-06-28
> xadgs@XaDgs-desktop:~$ pulseaudio --check && echo $?
xadgs@XaDgs-desktop:~$ pulseaudio --dump-modules

Hmm - you don't seem to be running Pulseaudio, which is strange, especially since you're running 10.04. Whilst it may have nothing to do with that and be purely a sound driver issue, I'd try Pulseaudio first - it should work with snd_hda_intel.

You may want to try closing all applications that output audio and try starting Pulseaudio (this *won't* hold after a reboot if you're concerned):

```
pulseaudio --start
pulseaudio --check && echo $?
```

As an aside, you can kill Pulseaudio with:

```
pulseaudio -k
```

Another thing to check could be that under System->Prefs->Volume Control->Hardware, you have the correct output option selected for your speaker setup (channels, etc).

---

### Post by DenDum on 2010-06-29
hmm
The pulseaudio doesnt seem to have any big effect.

The sound does seem to be better.. i think.. I cant really tell for sure, but it isnt satisfying.
The sound isn't allright, it still sounds better in Windows XP.

I found this site: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Maybe I should try to run this command?: 

```

 
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter


``` I just cant understand why it is that this problem has been there with two different computers and with 3 different versions/updates of ubuntu, but I am the only one who is getting this :S



PS. Thanks for the fast replies. You guys are quick ! 
Sorry for just replying now, but I falled asleep :O

---

### Post by DenDum on 2010-06-29
Anybody got any idea's about why I have bad sound quality ?
The music plays and it isnt because it is like ****, but when High Definition (HD) and FLAC files sound worse than an mp3 file, then something is wrong :confused:

---

### Post by belkinsa on 2010-06-29
You won't hear a difference between MP3 and FLAC through headphones.  Unless you have good sound card and system.

---

### Post by DenDum on 2010-06-29
> **Mechafish said:**
> You won't hear a difference between MP3 and FLAC through headphones.  Unless you have good sound card and system.


Dude.. I did hear a difference and to be sure I asked my friend to listen to and he could hear it too.

Ive tested this so many times. No matter what, the sound quality isn't good....

---

### Post by belkinsa on 2010-06-29
Um, sorry that I said that.

---

### Post by DenDum on 2010-06-29
> **Mechafish said:**
> Um, sorry that I said that.


NP, Im just frustrated over this sound thing. I cant find any reasons for why it should be like this.

I can hear music in okaii quality, but it isn't satisfying at all.

Any idea's why this could be happening :( ?
Im open for idea's

Ive tried to tweak the sound settings and lower the PCM ( even tho i dont know what PCM is ) to see if it helped, cause ive heard that it could make it better, but nothing.


Its like the bitrate decrease or doesn't play as good.. it sounds compressed :S .

---

### Post by DenDum on 2010-06-29
Anybody ?

---

### Post by stderr on 2010-06-29
The ol' lossless/lossy debate :) Personally I've been migrating my library to FLAC for some time now, and can barely stand mp3s that are < ~ 192-256kbps. But I do have a monitor speaker/sub setup and a dedicated soundcard :) It's much harder to tell the difference with normal speakers, and especially headphones. 

Put it this way - when I upgraded from my Logitech Z2300 speakers (not bad - at least, the sub was excellent!) to my current ones (see sig), I suddenly found myself almost unable to listen to the very audible crackling of my mp3s, which I hadn't ever noticed before. 

That said, I don't doubt that what you say holds true, but am somewhat struggling to imagine what could be wrong. You said you thought you noticed a slight improvement in sound quality when running Pulseaudio?

The two areas of suspicion that come to mind are a) your audio drivers, i.e. the kernel module snd_hda_intel or whatever it was that we identified on the previous page, and b) configuration files such as ~/.asoundrc, /etc/pulse/*, etc.

However, one wonders what was running before you started Pulseaudio (ALSA, OSS, ...), and *why* Pulseaudio wasn't running. Perhaps it was unable to start for some reason - if that's the case, it normally outputs errors to /var/log/syslog, so that may be a good file to browse through.

---

### Post by stderr on 2010-06-29
Ah, another stupid suggestion, but have you checked the sound output type? System->Preferences->Volume Control (or might be called Sound xxxx[Something] instead depending on your Ubuntu version). Under the Hardware tab (might be different on yours), you can select an output profile, the main distinctions of which are the audio channels to output on. If you are outputting either the wrong channels, or the right channels through the wrong ports, then that could explain really poor audio quality.

It might even be the case that Ubuntu's confused over them and specifying things explicitly in ~/.asoundrc resolves the issue. I had a similar problem with the Creative XtremeAudio soundcard when I wanted to output on two ports simultaneously - one for the subwoofer, one for the speakers.


edit: looking back over your original post, it sounds like the above could be a valid possibility: 
> but it is like it is going with a low frequency.

And another idea - installing & running JACK audio server might work around whatever the problem is. You'd do best to read a tutorial on it before jumping in, because it's very different to something like Pulseaudio (and a pain in the ** in comparison for normal everyday audio stuff). I wouldn't recommend it as a permanent solution, but might be useful to test to see if it sounds any better. NB: without installing a realtime kernel too, and without hacking the configuration parameters to seriously increase the audio latency, you'll probably get loads of buffer underruns, causing gaps in audio playback. This is normal.

Finally, the Pulseaudio-related packages you sought to install - they're all standard, and I can see no reason not to install them. I think I have all of those installed. 

edit 2: my *final* stupid suggestion of the night: ensure that all audio volume controls on all channels are turned to the max, and then adjust the volume in the application you're playing sound from.

---

### Post by RJARRRPCGP on 2010-06-29
> **stderr said:**
>  buffer underruns, causing gaps in audio playback. This is normal.


That's usually because of not enough RAM or crappy HDD performance. 
I would not recommend having less than 512 MB of RAM and I would not recommend using a 5,400 RPM HDD!

I can play audio with a regular kernel without gaps. 

Oh, an edit here:

I suggest trying a smaller buffer size, because a large audio buffer can cause pausing!

---

### Post by stderr on 2010-06-29
You're definitely right about disk IO in my case - I experience severe problems and have to increase latencies considerably on the odd occasion I run JACK. I typically run ~ 6-7 HDDs simultaneously; all are 7.2k+, and they all have large caches. My CPU's reasonable too, but Linux's seemingly chaotic IO handling means that even small spikes in disk activity seem to produce sufficient IO wait time (not that IO would spike much on a system monitor) for the CPU to have insufficient time to populate the buffer before it's exhausted. I even get the occasional Xrun with **huge** audio buffer sizes. It's also very possible that it could be more related to insufficient bus bandwidth on the motherboard than CPU/scheduling alone (i.e. data in/out of PCI soundcard etc), especially considering my motherboard has 2 separate SATA controllers, and data read/write speeds seem to be dependent on which controller the drive is connected to, and in the case of writing, which drives you're writing from and to. A realtime kernel would go most of the way to solving (well, masking :p) these problems without requiring better hardware. But it would also ruin everyday computing hehe.

The one thing I am sure of though - I've more than enough RAM for JACK ;)

---

### Post by DenDum on 2010-07-02
> **stderr said:**
> Ah, another stupid suggestion, but have you checked the sound output type? System->Preferences->Volume Control (or might be called Sound xxxx[Something] instead depending on your Ubuntu version). Under the Hardware tab (might be different on yours), you can select an output profile, the main distinctions of which are the audio channels to output on. If you are outputting either the wrong channels, or the right channels through the wrong ports, then that could explain really poor audio quality.

It might even be the case that Ubuntu's confused over them and specifying things explicitly in ~/.asoundrc resolves the issue. I had a similar problem with the Creative XtremeAudio soundcard when I wanted to output on two ports simultaneously - one for the subwoofer, one for the speakers.


edit: looking back over your original post, it sounds like the above could be a valid possibility: 


And another idea - installing & running JACK audio server might work around whatever the problem is. You'd do best to read a tutorial on it before jumping in, because it's very different to something like Pulseaudio (and a pain in the ** in comparison for normal everyday audio stuff). I wouldn't recommend it as a permanent solution, but might be useful to test to see if it sounds any better. NB: without installing a realtime kernel too, and without hacking the configuration parameters to seriously increase the audio latency, you'll probably get loads of buffer underruns, causing gaps in audio playback. This is normal.

Finally, the Pulseaudio-related packages you sought to install - they're all standard, and I can see no reason not to install them. I think I have all of those installed. 

edit 2: my *final* stupid suggestion of the night: ensure that all audio volume controls on all channels are turned to the max, and then adjust the volume in the application you're playing sound from.


Heii 

Sorry for being slow, with this.

I have installed Realtime Audio and Jackd, by following these guides:

[http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related](http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related) ( realtime audio )

[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4) ( JACK )

Ive installed and configured the settings.

The sound has improved, its much much better, even tho there was a bit of lag and jumps in the sound, at first, it stopped tho, its better. But it is a long way from what is normal.
When i turn up the sound when i play example a FLAC file the sound, is like crap. its like its being played through bad speaker/headphones, when using ubuntu, but in Windows there isnt any problems. 

Even tho ive installed JACK and configured the settings, the problem persists. 

The sound is still wrong.

It is allmost like the sound is hollow/hole. Not in the way that it is being played in a hollow room, but the sound itself sounds hole.

Any new ideas :S ? I am out of ideas.

---

### Post by DenDum on 2010-07-04
Nothing ?

---

