---
title: "Sound Issue."
date: 2010-03-27
forum: General Help
---

### Post by Winterwolf2010 on 2010-03-27
Hello, I am Very New to Ubuntu, This is my first time using Any Linux Operating System. I just received Ubuntu 9.10 desktop edition in the mail this morning. I ran the CD "live" in my HP Pavilion TX2510us Laptop. The laptop has no hard drive due to it failing in the past, So I have installed Ubuntu on a 1 TB external Hard disk. While Running the CD "Live", before installing it, The sound was working. But now that it is installed and booted up it does not work. I did a few searches and came across a few command lines that may help you guys figure out what is wrong. As Follows:

shannon@shannon-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

shannon@shannon-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2400000 irq 16
shannon@shannon-laptop:~$ lsmod | grep snd
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.20 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Realtek ALC268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-15.00]                                                &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;OO&#9474;                                                    &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;                                                    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     77     80<>80    75<>75    0<>0     0<>0      0<>0    75<>75             &#9474;
&#9474; < Master >Headphon   Front   Front Mi Line In   Mic Boos   Beep   Caller I   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by pbpersson on 2010-03-27
That OS is five months old now.  Have you installed all the updates to get you the latest fixes?

I did a Google search on **ubuntu ALC268** and there have been several threads on this but most of them are older.

Do you have ALL the volume controls turned up?  I know on one version of Ubuntu I had to turn up the volume for the back speakers to get mine to work - and I only have two speakers on the computer.

---

### Post by Winterwolf2010 on 2010-03-27
Yes All of my Sound volumes are turned up. Something Interesting, I just stumbled onto a website that helped me get it working temporarily, But the thing is, when I reboot the next time, there is no sound. The Web Link to where I found this is [http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

The Comands I used in order are as followed:

sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

And here are the results.

shannon@shannon-laptop:~$ sudo apt-get remove --purge alsa-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alsa-base*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 479kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141796 files and directories currently installed.)
Removing alsa-base ...
Purging configuration files for alsa-base ...
shannon@shannon-laptop:~$ sudo apt-get remove --purge pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pulseaudio* pulseaudio-esound-compat* pulseaudio-module-udev*
  pulseaudio-module-x11*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 4,760kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141750 files and directories currently installed.)
Removing pulseaudio-module-x11 ...
Removing pulseaudio-esound-compat ...
Removing pulseaudio ...
 * PulseAudio configured for per-user sessions
Purging configuration files for pulseaudio ...
Removing pulseaudio-module-udev ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
shannon@shannon-laptop:~$ sudo apt-get install alsa-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  apmd alsa-oss oss-compat
The following NEW packages will be installed:
  alsa-base
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/270kB of archives.
After this operation, 479kB of additional disk space will be used.
Selecting previously deselected package alsa-base.
(Reading database ... 141623 files and directories currently installed.)
Unpacking alsa-base (from .../alsa-base_1.0.20+dfsg-1ubuntu5_all.deb) ...
Setting up alsa-base (1.0.20+dfsg-1ubuntu5) ...

shannon@shannon-laptop:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pulseaudio-esound-compat pulseaudio-module-udev pulseaudio-module-x11
Suggested packages:
  pavumeter paman paprefs
The following NEW packages will be installed:
  pulseaudio pulseaudio-esound-compat pulseaudio-module-udev
  pulseaudio-module-x11
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/665kB of archives.
After this operation, 4,760kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package pulseaudio-module-udev.
(Reading database ... 141669 files and directories currently installed.)
Unpacking pulseaudio-module-udev (from .../pulseaudio-module-udev_1%3a0.9.19-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package pulseaudio.
Unpacking pulseaudio (from .../pulseaudio_1%3a0.9.19-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package pulseaudio-esound-compat.
Unpacking pulseaudio-esound-compat (from .../pulseaudio-esound-compat_1%3a0.9.19-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package pulseaudio-module-x11.
Unpacking pulseaudio-module-x11 (from .../pulseaudio-module-x11_1%3a0.9.19-0ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up pulseaudio-module-udev (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio (1:0.9.19-0ubuntu4.1) ...
Adding user pulse to group audio
 * PulseAudio configured for per-user sessions

Setting up pulseaudio-esound-compat (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-module-x11 (1:0.9.19-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
shannon@shannon-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shannon/.gvfs
      Output information may be incomplete.
Terminating processes: 4440lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shannon/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shannon/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shannon/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.

So what is it that I am actually doing to get it to work, temporarily until next boot?
What is Causing it to reset with no sound, Is this my only option for getting it to work is to enter these commands every time i log on?

---

### Post by dimoftheyard on 2010-03-27
This is only a little better, but

sudo alsa force-reload

should be all you need to enter after a reboot. The other commands just remove/install packages, and I don't think rebooting changes anything about them.

---

### Post by Winterwolf2010 on 2010-03-27
So yes that 1 command alone After a reboot works. I'm Glad to know that If it has to be done this way every time I log on, to get sound, that its just "copy and Paste" one command, and not 4 of them. Thanks for that bit of info. ;) Now only if I can get it to work after a reboot without having to use that. :D

---

### Post by pbpersson on 2010-03-27
You could put that one command into a script and then put it in your list of startup items so it would all happen behind the scenes without you even needing to think about it

---

### Post by dimoftheyard on 2010-03-29
I thought about putting this in a script too, but that's not so easy... the command needs to be executed as root (or with sudo), so either you have to put it in a script executed by root, which is bad practice, or you need to set up a script file owned by root with the set-user-ID flag. Either way is not exactly a clean solution, especially since there probably is a simple fix that makes sound work across reboots. But I don't know one, currently...

A quick look at google showed that more people have that problem, but I didn't find anybody with a solution... I'll keep my eyes open.

---

### Post by Winterwolf2010 on 2010-03-29
OK, I think I have stumbled onto what may be the cause of this. I reinstalled Ubuntu on my external hard drive, and this time the sound was working right away, as where it didn't before. Which is really odd. Then As soon as I installed the ATI driver for the video card, I'm back at square one, where I have to type in that fore-reload command to get sound again. ](*,) well at least I'm getting somewhere. I hope. Any Idea's? :confused:
Something Else thats interesting, The first time I installed Ubuntu on the external, I did it by putting the CD in and selecting install from the menu, The second time I did it, I was running Ubuntu live, and installed it from the desktop. It seems like it would not have mattered either way, but Oddly I got slightly different results from it.

---

### Post by tetsuo2010 on 2010-03-29
is there any explanation to the sound not working after you unplug and then plug the speakers back in? for some reason the speaker icon dissapears, and sound w/n work even after several reboots. ALSA and pulseaudio are installed fine.

---

