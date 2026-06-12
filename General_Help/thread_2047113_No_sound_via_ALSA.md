---
title: "No sound via ALSA"
date: 2012-08-24
forum: General Help
---

### Post by natomb on 2012-08-24
Good day,

I upgraded my system to an Intel i3770 and an Asrock board with B75 chipset. Now I am not able to configure ALSA to playback sound (recording was not tried until now).

My configuration:

```
Asrock B75-M mainboard
Intel i3770 CPU
Samsung LE40M86BD screen
connection via HDMI on port #2

```

This is what aplay -l returned:

```

root@mythwz:~# aplay -l
**** Liste der Hardware-GerÃ¤te (PLAYBACK) ****
Karte 0: PCH [HDA Intel PCH], GerÃ¤t 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sub-GerÃ¤te: 1/1
  Sub-GerÃ¤t #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], GerÃ¤t 3: HDMI 0 [HDMI 0]
  Sub-GerÃ¤te: 1/1
  Sub-GerÃ¤t #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], GerÃ¤t 7: HDMI 1 [HDMI 1]
  Sub-GerÃ¤te: 1/1
  Sub-GerÃ¤t #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], GerÃ¤t 8: HDMI 2 [HDMI 2]
  Sub-GerÃ¤te: 1/1
  Sub-GerÃ¤t #0: subdevice #0
root@mythwz:~#

```

I also created an asound.conf file.

```

root@mythwz:~# cat /etc/asound.conf
pcm.!default {
  type asym
  playback.pcm {
    type hw card 0 device 8
  }
  capture.pcm {
    type hw card 0 device 0
  }
}

```

With this configuration I am able to use VLC and playback video with sound.

Speaker-test also provides sound.

```

speaker-test -D plughw:0,8 -r 44100

```

But other programs, particularly VirtualBox, cannot playback sound. I think it is because of a configuration problem with ALSA.

I found many discussions around this topic, starting from adjusting alsa-base.conf file, unmuting in the mixer, etc. I tried several of them. The only thing I could not try is to change volume / unmute IEC968, because I do not have it in the mixer (alsamixer).

Can you provide me with some hints on what else I can try?

Thank you very much
  Bjoern

---

### Post by Rexilion on 2012-08-24
You did not mention the workarounds you tried. I found one here:

[http://ubuntuforums.org/showthread.php?t=1102581](http://ubuntuforums.org/showthread.php?t=1102581)

Other threads that are mentioned are:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but is probably only a good reference.

---

### Post by natomb on 2012-08-26
Hi,

thank you for those two links. Some of the proposals described there is on my list "done without success". Yet, I repeated all the steps.

[http://ubuntuforums.org/showthread.php?t=1102581](http://ubuntuforums.org/showthread.php?t=1102581) => I appended the "ac97_quirks=3" to the existing snd-intel8x0m line and rebootet the system. No effect.

aplay -l as well lspci return my sound card. On the alsa project web page linked in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) there is no sound card driver for the Ivy Bridge listed. However, I also could not find the well existing snd-hda-intel driver there, thus I assume the webpage has some "extremly advanced" navigation exceeding my limited capabilities or the webpage of the project is simply outdated.

I also did modprobe snd-hda-intel but no effect.

Finally I added the user to the audio group, rebooted, but again no effect.


The steps left out are reinstalling alsa from scratch, compiling alsa from source code and reinstalling ubuntu from scratch. As I have a fresh install of Ubuntu I am not sure if reinstalling Ubuntu over a fresh install of Ubuntu might change something.


Summarizing: **the problem still exists.**

---

### Post by Rexilion on 2012-08-26
Big jump, try an rc kernel? E.g. (did not in anyway test this):

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git ~/linux-git
cd ~/linux-git
cp /boot/config-$(uname -r) .config
make -s oldconfig
cp .config ~/config_new
make -s distclean
cp ~/config_new .config
make -s
make -s install
make -s modules_install
```

Reboot.

---

### Post by natomb on 2012-08-29
Good morning,

to keep you updated here is what I have tried in the meantime:

Following post #2041 in [http://ubuntuforums.org/showthread.php?t=205449&page=205](http://ubuntuforums.org/showthread.php?t=205449&page=205) but no effect.

Following the guide in [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#heading=h.vwklkhv4ivnd](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#heading=h.vwklkhv4ivnd), in particular steps Aa, Ab, Ac, Ad, Af, Ag and B. I also followed step D, with the resulting link:

Your ALSA information is located at [http://www.alsa-project.org/db/?f=373733c84d9bf9a2c869c264949bbd1f60163afe](http://www.alsa-project.org/db/?f=373733c84d9bf9a2c869c264949bbd1f60163afe)



I also found directions to upgrade from alsa 1.0.24 to 1.0.25, which I will try too.


EDIT: after following the google guide, VLC does not playback anymore as well. Thus, the whole PC is "silent" now. Also reinstalling ALSA using "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" and "sudo apt-get install linux-sound-base alsa-base alsa-utils mythbuntu-desktop" did not fix it.

---

### Post by natomb on 2012-08-30
Ok, I have reinstalled mythbuntu to the point where VLC is working but ALSA is not. This is an analysis file of ALSA's situation:

[http://www.alsa-project.org/db/?f=3a7fd95aa4ffd07bf5647d8a057767b0e2f15e41](http://www.alsa-project.org/db/?f=3a7fd95aa4ffd07bf5647d8a057767b0e2f15e41)

What I am confused about is that (1)
```

!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25

```

=> shouldn't it be all 1.0.25 ?



and (2)
```

!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116, 10 Aug 30 19:13 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  9 Aug 30 19:13 /dev/snd/hwC0D0
crw-rw---T  1 root audio 116,  8 Aug 30 19:13 /dev/snd/hwC0D3
crw-rw---T  1 root audio 116,  7 Aug 30 21:51 /dev/snd/pcmC0D0c
crw-rw---T  1 root audio 116,  6 Aug 30 21:51 /dev/snd/pcmC0D0p
crw-rw---T  1 root audio 116,  5 Aug 30 19:13 /dev/snd/pcmC0D2c
crw-rw---T  1 root audio 116,  4 Aug 30 21:46 /dev/snd/pcmC0D3p
crw-rw---T  1 root audio 116,  3 Aug 30 21:46 /dev/snd/pcmC0D7p
crw-rw---T  1 root audio 116,  2 Aug 30 21:50 /dev/snd/pcmC0D8p
crw-rw---T  1 root audio 116,  1 Aug 30 19:13 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Aug 30 19:13 /dev/snd/timer

```

=> shouldn't there be /dev/snd/hwC0D7 and /dev/snd/hwC0D8 ?


So, still working on the problem but without solution. However, many thumbs up for the ALSA analysis file. I wish that all such files are as clearly written as this one.


Bjoern

---

### Post by natomb on 2012-08-31
And some more info, following the guides here:

[http://wiki.ubuntuusers.de/Sound_Problembehebung#Soundsystem](http://wiki.ubuntuusers.de/Sound_Problembehebung#Soundsystem)
[http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung](http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung)

```

myth@mythwz:~$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

```

```

root@mythwz:~# lsmod | grep "snd"
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

```

```

root@mythwz:~# head -n 3 /proc/asound/card0/codec#0
Codec: Realtek ALC662 rev1
Address: 0
AFG Function Id: 0x1 (unsol 1)

```

```

root@mythwz:~# head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: »/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden

```

---

### Post by Rexilion on 2012-09-01
Could you post the output of the following command (entirely)?

```
sudo dmesg
```

Paste it at pastebin.com and place the link here please.

---

### Post by natomb on 2012-09-01
Hi Rexilion,


thank you very much for your support so far. I have posted the output of dmesg in pastebin ([http://pastebin.com/G3wT86be](http://pastebin.com/G3wT86be)) .

---

### Post by Rexilion on 2012-09-02
I notice this:

> [   36.821076] init: alsa-restore main process (1097) terminated with status 19

Could you open alsamixer (again) and really check if they are muted? You can see the 'mute status' on the two 0's (00) in alsamixer.

Furthermore, I see more HDMI/HDA messages after this. So I guess the kernel handles stuff just fine. However, lines like these are odd to me. Maybe you have  a clue?

> input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15

I'm not a sound guru but Line-***_out_*** is not 'input'. Could be wrong though.

---

### Post by natomb on 2012-09-03
Hi,

here is the alsamixer with the above asound.conf file. I also changed the asound.conf file to a more simple one (just playback and capture in one device) but nothing changed.

I am really close to go upstream and try new kernel. But I am afraid that then I will miss all the kernel updates and have to take care by myself.

---

### Post by Rexilion on 2012-09-03
> **natomb said:**
> Hi,

here is the alsamixer with the above asound.conf file. I also changed the asound.conf file to a more simple one (just playback and capture in one device) but nothing changed.

Looks good to me, did you try pressing F6 and look for other cards?

> **natomb said:**
> I am really close to go upstream and try new kernel. But I am afraid that then I will miss all the kernel updates and have to take care by myself.

The whole point of 'going upstream' is to receive the latest code/updates/(bugs)/fixes. You can safely revert back to the stock kernel, but with git it's also really easy to update your kernel. That is a matter of

```
git pull
```

and then rebuilding the kernel. Git is specifically build for this purpose.

---

### Post by natomb on 2012-09-09
Hi,

I have done two things (without success):

(1) compiling and using Linux 3.5 kernel series, following the steps from your proposal (except using the latest stable, instead of latest trunk).

(2) upgrading to quantal.

In (1) the system failed to boot because it could not initialize network, which is crucial if your root partition is on a iscsi target.

In (2) the system failed to mount root because it could not start the iscsi subsystem.

For (2) I will post a bug so it might get fixed for the final release.

Thus, so far the only sound is with VLC :(


Cheers
  Bjoern

---

### Post by natomb on 2012-09-09
Wonders do happen, I think.

After installing the last dist-upgrade with the 3.2.0-30 kernel, I could get sound using the following command:

```

aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Left.wav

```


Thus, I assume that alsa is working - somehow. Now the question is how to configure it so I can have sound with e.g. VirtualBox. In VirtualBox I can just set "Alsa" as the audio system, but if I do so I will not hear anything. I assume that alsa selects one of the other sound outputs and not device 8. Here is the output of aplay -l again:

```

**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: PCH [HDA Intel PCH], Gerät 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 7: HDMI 1 [HDMI 1]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 8: HDMI 2 [HDMI 2]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```

---

### Post by Rexilion on 2012-09-09
Kind of weird that this does work with VLC though...

VirtualBox uses SDL for audio which is not a good combination. Don't know much about SDL though...

---

### Post by natomb on 2012-09-10
Ok, quest solved.

It appears to me that Ubuntu uses the PulseAudio settings for default Alsa output, regardless what is the configured default output for Alsa (i.e. vie /etc/asound.conf or ~/.asoundrc). After installing **pavucontrol** (grapical frontend for PulseAudio) and playing around with the sound card settings there, audio out via HDMI works.

Still, very strange that Ubuntu seems to ignore alsa settings in alsa configuration files. Especially because most tips and guides around this topic work with /etc/asound.conf

---

### Post by Rexilion on 2012-09-10
Good thing you solved it! Congrats. :guitar:

I wouldn't be suprised to the fact that Ubuntu patched the software so that it prefers Pulse above Alsa by default. Not sure though. One thing is clear, this is making stuff hopelessly complicated/complex/hard to understand for someone who just wants to make stuff 'work'.

---

