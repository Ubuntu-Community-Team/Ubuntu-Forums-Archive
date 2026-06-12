---
title: "no surround sound"
date: 2011-01-10
forum: General Help
---

### Post by callecx on 2011-01-10
I've tried everything and every combination i can think of lol. Help would be much appreciated.

/// background //////////////////////////////////////////////////////////////////////////////////////////

I have the following setup:
HTPC connected to home threatre amplifier via HDMI cable. Amplifer then connects to the TV via HDMI. 
There is also an optical cable that goes from the amplifer to the TV to replay sound through the speakers
when watching free to air TV.

Note: Everything was working fine before the upgrade to 10.10. Since then, i've reinstalled ubuntu in the
hope that it would fix itself. 


/// os info ////////////////////////////////////////////////////////////////////////////////
Ubuntu 10.10 maverick, 32-bit.
XBMC 10.0 r35648 (Compiled: Dec 17 2010)


/// system->preferences->sound //////////////////////////////////////////////////////////////////////////
In the hardware tab, i have the following profile selected for the only audio device (onboard):
Digital Stereo (HDMI) Output

Note that in the profile drop-down box i have no digitial 5.1 surround sound option (dont think there ever
was one though). Although there is a Analog Surround 5.1 Ouput option. I've selected this option and i 
hear no sound at all.


/// alsa-mixer //////////////////////////////////////////////////////////////////////////////////////////
Everything is unmuted:
[http://i55.tinypic.com/70ubmq.png](http://i55.tinypic.com/70ubmq.png)


/// alsa-info.sh ////////////////////////////////////////////////////////////////////////////////////////
[http://www.alsa-project.org/db/?f=abcbbfc09af7476bae87b16a295437d8fe8e4609](http://www.alsa-project.org/db/?f=abcbbfc09af7476bae87b16a295437d8fe8e4609)


/// xbmc ////////////////////////////////////////////////////////////////////////////////////////////////
The menu sounds play when selecting different menu options. However, when i attempt to play a video file
that supports surround sound (5.1), (.mkv), it fails, stating that i need to check my audio settings.

That audio settings i have selected in XBMC are:
Audio output: HDMI
Speaker configuration: 5.1
Boost volume level on downmix: "checked"
Dolby Digital (AC3) capable reciever: "checked"
DTS capable reciever: "unchecked" - note, it does not seem to matter if this option is selected or not, 
                                    still doesnt play in 5.1.
Audio output device: pulse:alsa_output.pci-0000_00_1b.0.analog-surround-51@default
                     note, if i change this option the previous selected option completely disappears from
                     the drop-down box. The only real option i'm left with is "Internal Audio Digital Stereo
                     (HDMI)". I've tried using this option, i can get audio in some video files only 2.0 and
                     not in the 5.1 enabled video files
Passthrough output device: iec958 - note i've tried selecting HDMI here, doesn't make a difference.


/// xbmc.log debug log file//////////////////////////////////////////////////////////////////////////////
[http://pastebin.com/Tu1HUMXA](http://pastebin.com/Tu1HUMXA)

---

