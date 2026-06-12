---
title: "I have no sound on ubuntu 9.10"
date: 2009-12-06
forum: General Help
---

### Post by muse3332 on 2009-12-06
i requested a cd from the website and i installed it but now thers no sound any ideas?

---

### Post by lidex on 2009-12-06
Run this command in a terminal (accessories>terminal):
```
gnome-alsamixer
```
Make sure your volume levels are not all the way down or muted.

For giggles can you post the output of this command:
```
sudo lshw -C sound
```
You'll need to enter your password for this one - it will not display so don't let that throw you. Hit the enter button after entering commands.

Info here:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by brklynsniper on 2009-12-07
*-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f8600000-f8603fff

i have no sound also that was the output please help it is rather annoying and everything is unmuted

---

### Post by LuisGMarine on 2009-12-07
Who is the manufacturer of your computer?

---

### Post by lidex on 2009-12-07
Check your levels here as well:
```
alsamixer
```

Can you post output of these commands?
```
aplay -l
```
```
aplay -L
```
```
/sbin/lsmod | grep snd
```

---

### Post by brklynsniper on 2009-12-07
I have a HP pavilion laptop and with jaunty the sound worked just fine but since i upgraded it gone completely and i unmuted and tried almost everything that people suggested im at a loss

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0




**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
dustinpramos@Dustins-laptop:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server



/sbin/lsmod | grep snd
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
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

---

### Post by LuisGMarine on 2009-12-07
Try this guide here out, should work I know I used it when I had my toshiba that was using the same sound card. :popcorn:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

---

### Post by lidex on 2009-12-07
We should confirm that your user is set up in pulse group. Go to "system>administration>users and groups". Click the "unlock" button. On the left select your username then click "properties" button on right. Click the "user privileges" tab, scroll down and place check in box for "use audio devices" if not already checked.
Click the OK button.

You should be back at the first window. Click the "manage groups" button. For any "Pulse" groups you see - I have three: pulse; pulse-access; pulse-rt - highlight, click properties and make sure your username is checked off as a group member and click OK. Then close out.

*[COLOR="DimGray"]For future reference: when you enter text output into post, highlight the text and click the "#" symbol to enclose in code tags. Thanks.[/COLOR]*

---

### Post by brklynsniper on 2009-12-07
> **lidex said:**
> We should confirm that your user is set up in pulse group. Go to "system>administration>users and groups". Click the "unlock" button. On the left select your username then click "properties" button on right. Click the "user privileges" tab, scroll down and place check in box for "use audio devices" if not already checked.
Click the OK button.

You should be back at the first window. Click the "manage groups" button. For any "Pulse" groups you see - I have three: pulse; pulse-access; pulse-rt - highlight, click properties and make sure your username is checked off as a group member and click OK. Then close out.
ok i have done that and stuff was unchecked but i still have no sound and pulse reads it as a dummy output, im brand new to linux so idk if pulse has anything to do with it or not

---

### Post by fluffman86 on 2009-12-07
Did you try running the alsamixer command in the terminal?
Use your left and right arrow keys to move, up and down to adjust levels, and press M to mute or unmute each device.  Use Esc to quit.

---

### Post by lidex on 2009-12-07
> **fluffman86 said:**
> Did you try running the alsamixer command in the terminal?
Use your left and right arrow keys to move, up and down to adjust levels, and press M to mute or unmute each device.  Use Esc to quit.

The PCM setting seems to be an issue for some.

---

### Post by brklynsniper on 2009-12-08
Yes i ran alsamixer and everything is unmuted and up all the way

---

### Post by brklynsniper on 2009-12-09
idk if this helps but i have a hp with quickplay and it has the touch sensitive quickplay panels above the keyboard with the play pause stop rewind ff buttons and a mute button and volume button, they worked in jaunty but i noticed the mute button is constantly lit up and when i press it, it mutes and the sound icon on top shows its mute but when i press it again its shows unmuted on the panel on top of the screen but the actually mute button stays lit as mute, when i start up my comp. its blue indicating its not muted and when the OS loads up and asks me to sign in the mute button lights up on its own and i hear the speakers click

---

### Post by lidex on 2009-12-29
Any update with your problem?

---

