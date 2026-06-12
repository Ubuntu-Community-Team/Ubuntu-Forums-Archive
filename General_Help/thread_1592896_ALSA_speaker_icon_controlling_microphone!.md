---
title: "ALSA speaker icon controlling microphone!"
date: 2010-10-11
forum: General Help
---

### Post by Bucky Ball on 2010-10-11
Hi all. Here's one for ya.

I have just removed Pulseaudio, updated ALSA and my USB headset seems to be working fine. Can't work out why speakers are not working for music. Put mouse over speaker icon in the tool bar and it gives me the volume level of the microphone!

Microphone: 76% 

!

Has anyone got any ideas what's happening? I have had nothing but trouble with sound on this Compaq 610. The headset worked great for Skype using Pulse but couldn't get it to ring through the speakers (a cinch with ALSA) but better than nothing. Then sound just died for no apparent reason about two weeks ago (my wife's machine and she does not tweak with it - I set and forget and only go near it if anything goes pear-shaped, therefore rarely - so nothing had been changed in about two months).

Really like to get to the bottom of this once and for all. I have two other machines running ALSA and using any kind of USB handset faultlessly ... AND ringing through the external speakers.

Input appreciated.

---

### Post by Bucky Ball on 2010-10-11
Well, I changed the empty file asound.conf to contain this:

```
pcm.!default {
    type hw
    card Intel
}
ctl.!default {
    type hw
    card Intel
}
```... 'Intel' being the name of my card in ```
/proc/asound/card
``` That fixed the speaker icon in the tool bar to show:

Master: 100%

... but, alas, still no sound.

---

### Post by Bucky Ball on 2010-10-11
I reinstalled Pulseaudio as I couldn't get ALSA working. When I put ```
pulseaudio -version
``` in a terminal I get this:

```
anna@katie:~$ pulseaudio –version
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:sad:snd_ctl_open_noupdate) Invalid CTL front:1
W: alsa-util.c: Cannot find fallback mixer control "PCM".
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
ALSA lib control.c:909:sad:snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:sad:snd_ctl_open_noupdate) Invalid CTL front:0


```
?

---

### Post by Bucky Ball on 2010-10-11
Current situation:

ALSA is kinda working. Sound through speakers but nothing through headset, although I can hear the mic through the headset. 

I can see the I can logon to Skype but when I go to Options->Sound Devices, change to the headset and try to make a test call, Skype crashes. Actually, it just shuts and disappears. Doesn't crash the machine and opens again just fine. Strange.

Just ask if you require any more detail.

---

### Post by dino99 on 2010-10-11
have you opened alsamixer ?

---

### Post by Bucky Ball on 2010-10-11
Yep. This might help:

```

anna@katie:~$ pulseaudio -v
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-hal-detect.c: Trying capability alsa
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0"  with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor"  with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument:  "device_id=1  sink_name=alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0").
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1  "alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0"  with sample spec "s16le 1ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 440 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #1; argument:  "device_id=1  source_name=alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0").
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with  sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument:  "device_id=0  sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 3 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #3; argument:  "device_id=0  source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for  too long, suspending ...
I: module-suspend-on-idle.c: Source  alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0  idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor  idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0  idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

anna@katie:~$ pulseaudio -v
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-hal-detect.c: Trying capability alsa
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0"  with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor"  with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument:  "device_id=1  sink_name=alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0").
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1  "alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0"  with sample spec "s16le 1ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 440 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #1; argument:  "device_id=1  source_name=alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0").
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with  sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument:  "device_id=0  sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 3 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #3; argument:  "device_id=0  source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for  too long, suspending ...
I: module-suspend-on-idle.c: Source  alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0  idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor  idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0  idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

anna@katie:~$ pulseaudio -v
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-hal-detect.c: Trying capability alsa
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0"  with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0  "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor"  with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument:  "device_id=1  sink_name=alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0").
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1  "alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0"  with sample spec "s16le 1ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 440 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #1; argument:  "device_id=1  source_name=alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0").
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with  sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument:  "device_id=0  sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 3 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #3; argument:  "device_id=0  source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for  too long, suspending ...
I: module-suspend-on-idle.c: Source  alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0  idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor  idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink  alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0  idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```

---

### Post by Bucky Ball on 2010-10-11
Quite odd. I now have Pulse back and working sort of. I can hear the Skype login sound and everything else through the USB headphones. Great. The problem, which was the reason I finally decided to go back to ALSA (a further disaster), is now this:

When I make a test SOUND everything works perfectly. I hear it no problem.

When I make a test CALL Skype closes, disappears without trace, no error message or kiss goodbye. I need to open it again.

I've had it with the sound probs on this machine. Namely Skype and Pulseaudio.

---

### Post by Bucky Ball on 2010-10-12
I have all running on ALSA. My only problem is how to get Skype ringing through speakers and call on headset. I swapped the USB headset with a regular line in/out plug headset I had.

---

