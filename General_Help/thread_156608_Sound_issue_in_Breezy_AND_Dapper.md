---
title: "Sound issue in Breezy AND Dapper"
date: 2006-04-07
forum: General Help
---

### Post by diskinetic49 on 2006-04-07
I recently bought an Averatec 3700 laptop, and I keep having a peculiar problem with sound.  I have tried searching this site for matching posts, but either the thread diverges from the topic or nothing in general happens.  So, I have decided to post a thread.

Upon installation, both Breezy and Dapper work really well at first with sound.  Then, upon reboot, nothing.  No errors, no changes in ALSA or whatever, just stony silence.  I have unloaded, reloaded, upgraded, re-installed, turned off esd, turned on other things, etc., but the problem remains absolutely unchanged.  The only reprieve is upon install.  During that one session, I have sound.  Flawless, stereo sound.  Being that this is a laptop, having it eternally on isn't an option.  Eventually, I must reboot.  What could be causing this, and how do I fix it?:confused: 

Thanks.

---

### Post by diskinetic49 on 2006-04-07
Yeah, still happening, but thanks for all the suggestions so far guys.

---

### Post by trent dillman on 2006-04-07
What is it you are installing, exactly?

Check in synaptic, and see what files are being installed. Then reboot and check those files for changes...

....also, do a 'lsmod' before and after....

---

### Post by diskinetic49 on 2006-04-07
WEEEEEIRD...

I guess God hates bitter sarcasm, because ten seconds after I posted that reply, Beep (which I just left playing for some reason) piped up to full volume and is now singing merrily away... weird weird weird.  Still, this then falls under that "sporadic loss of sound" issue I've seen floating about.  Any theories on this?

---

### Post by trent dillman on 2006-04-07
[QUOTE=diskinetic49]WEEEEEIRD...

I guess God hates bitter sarcasm, because ten seconds after I posted that reply, Beep (which I just left playing for some reason) piped up to full volume and is now singing merrily away... weird weird weird.  Still, this then falls under that "sporadic loss of sound" issue I've seen floating about.  Any theories on this?[/QUOTE]
I'd say God does...

But keep my suggestion in mind. It will probably happen again....

---

### Post by diskinetic49 on 2006-04-07
to answer your questions:

I'm only installing Ubuntu and mp3s, etc. to play.  I make no major alterations to the install.  Eventually, however, I do occasionally shut down and restart the laptop, and that's when I lose sound entirely (except, it seems, when nothing's happening).  What do you mean by "doing" a lsmod?

---

### Post by diskinetic49 on 2006-04-07
Ahhh, okay, I looked it up... It generated the following:

Module                  Size  Used by
binfmt_misc            10888  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
floppy                 52692  0
usblp                  11776  0
i2c_viapro              7696  0
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
rt2500                150372  1
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  2 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  14 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
via_agp                 9472  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  2 via_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usblp,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  658
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

---

### Post by jonjpeterson on 2006-05-15
[QUOTE=diskinetic49]I recently bought an Averatec 3700 laptop, and I keep having a peculiar problem with sound.  I have tried searching this site for matching posts, but either the thread diverges from the topic or nothing in general happens.  So, I have decided to post a thread.

Upon installation, both Breezy and Dapper work really well at first with sound.  Then, upon reboot, nothing.  No errors, no changes in ALSA or whatever, just stony silence.  I have unloaded, reloaded, upgraded, re-installed, turned off esd, turned on other things, etc., but the problem remains absolutely unchanged.  The only reprieve is upon install.  During that one session, I have sound.  Flawless, stereo sound.  Being that this is a laptop, having it eternally on isn't an option.  Eventually, I must reboot.  What could be causing this, and how do I fix it?:confused: 

Thanks.[/QUOTE]
I have been having the same problem and it seems that your thread just ends before the solution is presented. I don't even mind if  I have to do something at each reboot. I'm new to linux, but have found it to be a pretty easy learning curve. Thanks for any assistance that you can provide.

---

### Post by rcarring on 2006-05-15
I noticed that under dapper the volume control is switching to Mute All on rebooting. Not sure if this is related to my black screen i get on bootup so i have to switch to recovery mode and reboot.

---

### Post by yurtboy on 2006-06-17
with the machine I am working on the same things happens.
My only solution so far is to reboot into XP and then back into Lin.
I've seen this before on an older machine I had too.
This is a via chipset Averatec Laptop 3200 series AMD

---

