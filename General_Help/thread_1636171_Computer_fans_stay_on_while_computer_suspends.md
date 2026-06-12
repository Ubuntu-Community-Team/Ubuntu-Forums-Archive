---
title: "Computer fans stay on while computer suspends"
date: 2010-12-02
forum: General Help
---

### Post by LukeLaHood on 2010-12-02
Hello,
     I'm somewhat new to ubuntu and the install went well and all, but I there is one thing I have no idea about. I'm wondering that if you use the suspend option, is it supposed to turn off all of your computer fans as well? At first my suspend option wouldn't work, but then I applied some updates and now it suspends, and I can log in again without a problem. I was just wondering if there is anyway to get my computer case fans to stop spinning like they would in windows 7's sleep mode. Is there some type of configuration text file that I can edit somewhere?

Specs:
Ubuntu 10.10 64 bit
Asrock 890FX deluxe 3 motherboard
HD 4350 powercolor graphics card

---

### Post by wilee-nilee on 2010-12-02
Have you waited a length of time to see if they do stop. Basically suspend leaves power to some things, that is why it comes back up so fast. I never use suspend but thought this question pertinent.

---

### Post by LukeLaHood on 2010-12-02
Thanks for the reply.
The longest I've waited is about a full minute. I'll leave my computer in suspend now for 30 minutes and I will post whether they eventually turn off or not.

---

### Post by efflandt on 2010-12-02
Check /var/log/pm-suspend.log to see if anything there jumps out at you.  Once when I had trouble suspending, the screen would blank, but the video card itself was not turning off, which I could tell because I was not getting the screen saver image from my HDTV itself.

So it could be that some hardware is not going to sleep and that is why you still hear fans and things.

---

### Post by LukeLaHood on 2010-12-02
After fifteen minutes my computer fans keep running, and I got too impatient to go on. Also I realized that not only my fans remain on, but so does my display. My display, although black, is still lit up. 

efflandt,
   I'll check that log thanks for the suggestion

---

### Post by LukeLaHood on 2010-12-02
Hmm I didn't seem to notice anything in the logs... here is the log for the most recent suspend.
Initial commandline parameters: 
Thu Dec  2 17:32:20 CST 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux luke-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_via      62447  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2523725  56 
snd                    64117  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
edac_core              46822  0 
edac_mce_amd            9387  0 
xhci_hcd               58578  0 
joydev                 11363  0 
i2c_piix4              10047  0 
saa7164                63391  0 
lp                     10201  0 
dvb_core              105239  1 saa7164
parport                37032  3 parport_pc,ppdev,lp
tveeprom               14098  1 saa7164
k10temp                 3535  0 
serio_raw               4910  0 
usbhid                 42062  0 
hid                    84678  1 usbhid
pata_via                9248  0 
pata_atiixp             4405  0 
r8169                  42222  0 
ahci                   21857  0 
libahci                26167  3 ahci
firewire_ohci          24679  0 
mii                     5261  1 r8169
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
             total       used       free     shared    buffers     cached
Mem:       2056332     600372    1455960          0      38408     153324
-/+ buffers/cache:     408640    1647692
Swap:     31249404          0   31249404

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.58 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Thu Dec  2 17:32:24 CST 2010: performing suspend
Initial commandline parameters: 
Thu Dec  2 18:01:35 CST 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux luke-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

---

### Post by LukeLaHood on 2010-12-02
I found the following page: [http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html)
So, I tried the following command for the heck of it: **pm-suspend-hybrid**
[FONT=monospace][FONT=Arial]It gave me some types of errors about the USB ports on my computer failing to suspend. It looked like 4 usb ports were failing to suspend. I got like 8 USB ports, but four of the 8 USB ports are USB 3.0 if that makes any difference...
[/FONT][/FONT]

---

### Post by wilee-nilee on 2010-12-02
My usb ports stay powered I think that is normal, what about the fans and screen.

---

### Post by LukeLaHood on 2010-12-02
I don't seem to get any errors about the fans or screen, and didn't see anything in the log file I posted. But yes, all the fans and the monitor remain on. I found the following bug report for usb 3.0: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/522998](https://bugs.launchpad.net/ubuntu-release-notes/+bug/522998) Idk if that helps or not...

Does anyone else have any suggestions?

UPDATE: I also get an error while booting into ubuntu... every time. But, after this error it always goes to the login screen and all seems well... I took a picture of they error message and attached it.
8.820065] saa7164_downloadfirmware() no first image
8.891938] saa7164_downloadfirmware() Upload failed. (file not found?)
8.91979] Failed to boot firmware, no features registered

UPDATE #2: Nevermind the above error, I googled it and the exact model of my TV Tuner came up so that has something to do with my Hauppauge 2250 TV tuner which is next on my list to get working... unless this somehow could cause my Suspend problem.

---

