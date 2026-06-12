---
title: "Sound suddenly stopped working"
date: 2009-10-24
forum: General Help
---

### Post by undecim on 2009-10-24
I like to think that I can solve nearly any trouble I run into on Linux, but this is just flat-out stumping me. It's getting to the point that I'm even considering reinstalling Ubuntu just so I can get sound.

System is a fully updated 64-bit Jaunty running on an HP TouchSmart tx2

My sound has been working fine. Been watching videos online, etc.

I haven't used sound in a couple of days (have all system sounds disable, since I use this computer in class a lot)

But today, it hasn't worked at all. Everything on my computer indicates that it's working fine, but I still have no sound.

I opened the PulseAudio Volume Control (installed from the repositories some time ago) while playing an AVI in Totem, and could see that Totem was streaming to Pulse, which was in turn (according the Pulse) streaming to my ALSA device (HDA ATI SB -ALC268 Analog)

Given this, I thought it was a hardware problem, and stuck in a LiveCD to check, and sound worked fine there.

I've also tried mplayer as root (back in my installed system), and got no errors or sound, indicating that this is not an issue with permissions or user-specific settings. Tried "sudo alsa reload" with no errors.

Relevant info:```
$ uname -a
Linux caffeine 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux
$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

Nothing relevant from dmesg or anywhere in /var/log/. If I left anything out, let me know.

Sound isn't my strong point, but I'm at my whit's end here... I've searched Google, these forums, and the online Ubuntu documentation, but can't find anything.

If anyone could point me in the right direction, I would appreciate it. Thank you in advance for your time.

---

### Post by falconindy on 2009-10-25
I don't think this is a hardware problem. Seems like somewhere, some volume channel is muted or turned way down. Start playing an audio/video file, and pop open the pulse volume control. Does it show any output on the meters? There's actually two relevant volume controls in that widget. Have you checked all the tabs to ensure that none of them are turned down or muted? 

Likely unrelated, but I used to have an intermittent issue where Pulse would... well, I don't know what it did (sound was really quiet), but the solution was always to open the volume control and things would just work.

---

### Post by undecim on 2009-10-25
> **falconindy said:**
> I don't think this is a hardware problem. Seems like somewhere, some volume channel is muted or turned way down. Start playing an audio/video file, and pop open the pulse volume control. Does it show any output on the meters? There's actually two relevant volume controls in that widget. Have you checked all the tabs to ensure that none of them are turned down or muted? 

Likely unrelated, but I used to have an intermittent issue where Pulse would... well, I don't know what it did (sound was really quiet), but the solution was always to open the volume control and things would just work.

I've tried messing with all the volume controls and settings I could. On the pulse volume control, it shows my card under output devices and shows activity the left and right meters, but there is nothing coming out of my speakers or headphones.

---

### Post by moloch42 on 2009-10-25
I had a problem a couple of weeks ago with the same symptoms. I can't tell you the exact cause, but I can give you some information that might help, and I can tell you how I eventually fixed the problem.

A while ago I was messing around with my sound setup to try and enable surround sound via SPDIF. I had installed new versions of pulseaudio and alsa via scripts. I had also made changes to /etc/modprobe.d/alsa-base.conf and a couple of the config files in /etc/pulse. If you have made any similar changes to your setup that would be a good place to start.

The way I ended up solving the problem was by upgrading to karmic beta. During the install I chose to accept the new audio config files rather than keep my customized ones. After the upgrade and the reboot my sound was working again.

Its not a particularly elegant solution, but it worked for me.

---

### Post by falconindy on 2009-10-25
> **undecim said:**
> I've tried messing with all the volume controls and settings I could. On the pulse volume control, it shows my card under output devices and **shows activity the left and right meters**, but there is nothing coming out of my speakers or headphones.
Double check your physical connections then. Try a pair of headphones or another pair of speakers, perhaps.

---

### Post by undecim on 2009-10-25
> **falconindy said:**
> Double check your physical connections then. Try a pair of headphones or another pair of speakers, perhaps.

There are no physical connections. I'm on a laptop with builtin speakers below the monitor and two headphone jacks in front. Both the speakers and headphones work from a LiveCD, so it's not a hardware issue.

Just got an idea... im going to compare configurations between the LiveCD environment and mine.

---

### Post by Favux on 2009-10-25
Hi undecim,

Have you tried adding the line to "alsa-base.conf" described in step 7 of this HOW TO?:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

---

### Post by undecim on 2009-10-25
> **Favux said:**
> Hi undecim,

Have you tried adding the line to "alsa-base.conf" described in step 7 of this HOW TO?:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)
Yes, I added that line when setting up my laptop, and have tried rebooting with and without that line commented out.

My sound has been working fine, but today it just seems to have quit. I haven't changed anything relating to sound, and I don't remember installing any sound-related updates recently.

---

### Post by undecim on 2009-10-25
Okay, a few new pieces of info that are either going to help, or will completely bemuse you.

Under System -> Preferences -> Sound, when using the "Test" button, the audio stream shows up in pulse, but there is nothing on the volume meter for that stream.

Also, in those sound options, I changed Music and Movies to an ALSA device instead of Autodetect. Then, the device didn't show up in pulse, but there was also no output. I tried this for all the available devices and nothing gives me sound.

There were a few errors on some about the device not being available, so I ran "killall pulseaudio" and all those errors stopped, but still nothing gives sound.

So I figured this may be something involving gnome (since it's clearly not an issue with ALSA, unless there is a simlar issue with OSS), and open an avi in mplayer. Mplayer says it's using alsa, but while using mplayer, testing OSS devices in sounds preferences gives an error about the device not being available (but this is not the case with ALSA devices)... So mplayer is using OSS, but think's it's using ALSA? or the Sounds Preferences is backwards?

---

### Post by Favux on 2009-10-25
Hi undecim,

Could you show me what your "/etc/modules" file looks like?

---

### Post by undecim on 2009-10-25
> **Favux said:**
> Hi undecim,

Could you show me what your "/etc/modules" file looks like?
```
undecim@caffeine:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
undecim@caffeine:~$
```

not much to speak of. Since we're talking about modules, here are my currently loaded snd modules:

```
undecim@caffeine:~$ lsmod | grep snd
snd_hda_intel         559028  4 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  3 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
undecim@caffeine:~$
```

---

### Post by Favux on 2009-10-25
Hi undecim,

Just for fun add "fuse" (without the quotes) after 'rtc' in "/etc/modules" and reboot.  See if that gives you sound.

---

### Post by undecim on 2009-10-25
> **Favux said:**
> Hi undecim,

Just for fun add "fuse" (without the quotes) after 'rtc' in "/etc/modules" and reboot.  See if that gives you sound.
Still nothing.

According to modprobe, there is no "fuse" module. Should there be?

---

### Post by claracc on 2009-10-25
Since i received the security and recommended updates in ubuntu 9.04 last friday i have a problem with the sound, pherhaps this updates change something in sound file?. When computer boots the volume control of gnome appears as mute, i have to unmute it and put the master balance to the high (it appears in the lowest level).  

I tell you my configuration of pulse audio, just in case it can help you. I have selected in the volume control preferences: Playback- HDA intel AD198x Analog (pulse audio mixer), the name of my sound card; in system, preferences sound all is put as pulse audio sound server, in predermined tracks of mixer: Playback- HDA intel AD198x Analog (pulse audio mixer). In pulse audio preferences, in simultaneous output, be sure the option add virtual output device for simultaneous output on all local sound cards.

When i have not sound , i run the following commands:
sudo alsa force-reload
pulseaudio -D
and sound comes back.

Anycase, to configure audio in my laptop i have following the guide [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384).
I hope, it helps

---

### Post by claracc on 2009-10-25
Sorry, i forgot to complete the phrase : 

In pulse audio preferences, in simultaneous output, be sure the option add virtual output device for simultaneous output on all local sound cards, "is unthicked"

---

### Post by Favux on 2009-10-25
Hi undecim,

A couple of months ago a TX2z user told me sound didn't work until he put 'lp' and 'fuse' in modules.  It's worked for a couple of other users too.  I don't know how necessary lp (parellel ports) is.  But it's been in there every time anyway.  If I remember right fuse is something like user space file system access.  So far everybody has had fuse.  So I don't know.  I don't know if a change in another module stops it from auto-loading, or what's going on.

---

### Post by undecim on 2009-10-25
ITS WORKING!

I completely purged all alsa, oss, and pulse-related packages via aptitude, and reinstalled the ubuntu-desktop package. There were several packages I removed that didn't get put back when reinstalling ubuntu-desktop, but nothing is missing, and everything works!

Maybe it was those pesky updates? In any case, thanks for your time, everyone! Now I can sleep peacefully tonight.

---

### Post by commbot on 2009-10-25
> **claracc said:**
> 
When i have not sound , i run the following commands:
sudo alsa force-reload
pulseaudio -D
and sound comes back.


I find sound is really annoying with Ubuntu, much as I love the OS, every update seems to break something in audio and being in a situation where one day it works and the next, it doesn't is beyond a joke. I don't know if its a hardware or a software issue but this worked for me, many thanks.

Fingers crossed karmic is going to make thing better next week.

---

