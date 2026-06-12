---
title: "Sound issue after 12.04 upgrade"
date: 2012-04-26
forum: General Help
---

### Post by bmagnus on 2012-04-26
Hi!

As many others I've upgraded from 11.10 to 12.04 today. Everything is working fine, except the sound. It's glitchy and cuts in and out. A soundtest revealed that only the right channel displays this behavior, the left channel is working fine. I've tried removing and reinstalling alsa-base and pulseaudio, but still no luck. 

Has anyone encountered the same problem and managed to fix it? Any help would be deeply appreciated.

---

### Post by bmagnus on 2012-04-27
I still haven't found the source of my problem. However, I've managed to get my sound working properly by disabling Auto-Mute in alsamixer. This seems to work even after a few reboots.

---

### Post by imachavel on 2012-04-27
I was about to post a huge long thread with tons of commands I used from a thread and used them in terminal recovery mode. Terminal recovery mode is kind of a bitch because I couldn't really get kvm working that well, and didn't want to type out the return syntax anyway, when mostly it was 'read write mode'

or 'file cannot be moved'

or 'package is not found'

etc. etc. etc. and some good replies

rebooted and chose 'fix broken packages' after selecting 'recovery mode' from grub

now at this point I rebooted and well I got back in and everything seems fine. Now I'm no computer expert, but fuzzy distorted sound is usually an issue that points to a decoder not working properly. Don't know what decoders Ubuntu LTS uses but it'd be easy enough to find out what they are

find /lib/modules/`uname -r` | grep snd

I don't know maybe that'll help. If it doesn't sorry, google around for listing audio
decoders, sorry I don't have more info. Takes a lot of trouble shooting, which is sometimes a 
pain in the *** and no other way to do it then on your own. If google isn't
giving good hits on where to list installed audio codecs then perhaps bing
will work

---

### Post by imachavel on 2012-04-27
> **bmagnus said:**
> I still haven't found the source of my problem. However, I've managed to get my sound working properly by disabling Auto-Mute in alsamixer. This seems to work even after a few reboots.

oh it was just distortion? Like feedback, except that issue doesn't exist within an audio card unless the irq is set wrong, seems to be a problem that alsa mixer just has on it's own eh?

---

### Post by raja.genupula on 2012-04-27
use this
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by scweston on 2012-04-29
> **bmagnus said:**
> I still haven't found the source of my problem. However, I've managed to get my sound working properly by disabling Auto-Mute in alsamixer. This seems to work even after a few reboots.

I've had a very similar problem I believe on a fairly fresh install of 12.04. Turning off auto-mute in alsamixer has also fixed my problem.

Thanks very much.

---

### Post by jglick on 2012-07-11
Having roughly similar problems with Skype (2.x or 4.x) in 12.04 on a ThinkPad T520; if I make a test call, the audio is fine while the test speaker is talking, but after I record my ten second message and playback begins, there is a brief crackle from the speakers and then they go dead (absolute silence), even though the microphone is still working. Problem persists after reboot, even if /var/lib/alsa/asound.state has been deleted first.

Turning Auto-Mute Mode in alsamixer on *or* off temporarily restores sound to the speakers, but the problem recurs when next talking in Skype. Leaving Auto-Mute Mode disabled does not seem to help, nor does disabling the Skype option "Allow Skype to automatically adjust my mixer levels", nor does killing pulseaudio.

The problem does not seem to occur if I leave my microphone muted during the call.

The exact same problem appears sometimes (not always) with gnome-sound-recorder, so guessing this is not a Skype bug.

gnome-control-center sound-nua shows everything looking normal even when audio is broken; if I have toggled AMM more recently than I have recorded anything (or played back a recording?), so that audio is in fact working currently, then the "Front Left" speaker test is fine but the "Front Right" speaker test plays the test message so softly as to be almost inaudible. Of course this could be coincidental (conceivably a hardware problem) but it seems relevant. "Balance" is set to the middle.

The oddest thing is that it seems to be the act of replaying, not recording, which shuts off audio output. So if I record a few second speech sample in Sound Recorder and save it as MP3, closing Sound Recorder, and then from a shell play that clip, I get the momentary crackle and then audio goes dead until Auto-Mute Mode is toggled. But if I play some other *.wav file it works fine.

Note that everything was working fine when I installed Ubuntu. The problem began suddenly one day, while using Skype; as far as I know I had not made any configuration or software changes to trigger this.

When I try using a headset with microphone, the headset audio is fine, but the microphone does not work at all. I can mute the headset microphone (with a button on its side) in which case the laptop's internal microphone works fine. Needless to say the headset microphone works fine in Windows.

---

### Post by Maheriano on 2012-08-23
Wow, thanks, this was driving me crazy. I turned off auto-mute in Alsamixer and it worked for me too.

For anyone wondering how to do this, open a terminal and type "alsamixer", then scroll across the bottom menu until you get to auto-mute. Hit UP to disable it.

---

### Post by jogor10 on 2012-10-13
I too am having problem after 12.4 upgrade. My sound on videos is running a quick speed and distorted. Any fairly simple fixes for a novice?  thanks

---

### Post by Maheriano on 2012-10-15
> **jogor10 said:**
> I too am having problem after 12.4 upgrade. My sound on videos is running a quick speed and distorted. Any fairly simple fixes for a novice?  thanks

I haven't yet found a permanent fix for this but you can run "kill pulseaudio" in a terminal and it'll work temporarily. I'm hoping the 12.10 update fixes it.

---

