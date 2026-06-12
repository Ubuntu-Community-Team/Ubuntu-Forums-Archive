---
title: "Second monitor not working correctly"
date: 2012-02-20
forum: General Help
---

### Post by michaell4 on 2012-02-20
Hi,

I have a dual screen setup which worked fine until I formatted and reinstalled Ubuntu.

The other screen is clearly 'detected' as its white and when I move my mouse onto it the cursor turns into a big black X.

Can anyone offer any pointers?
I've searched around but i'm yet to come across anything that refers to a white screen with a X cursor.

Cheers,

Michael

---

### Post by Pilot6 on 2012-02-20
Use twinview instead of separate x screen. This must be fixed in 12.04.
I use separate x screen, but start applications there with a script with DISPLAY=:0.1

---

### Post by HavarN on 2012-02-20
What graphics card do you use? Could you post the output of the following commands?
```
lspci -nn | grep VGA
```Tells us which VGA card you have.
```
lsmod
```Tells us which driver you use for the card.

---

### Post by Pilot6 on 2012-02-20
It is obvious, that it is Nvidia :)

---

### Post by gordintoronto on 2012-02-20
What version of Ubuntu? What do you see when you run the Monitors program?

---

### Post by michaell4 on 2012-02-27
Hi,

This is the output:

[HTML]01:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1)[/HTML]

This is the output for the 'lsmod' command
[HTML]Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
dm_crypt               22565  0 
binfmt_misc            17292  1 
nvidia              10390874  38 
snd_hda_codec_hdmi     31426  4 
ppdev                  12849  0 
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
joydev                 17393  0 
wacom                  37007  0 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
rt61pci                27493  0 
crc_itu_t              12627  1 rt61pci
rt2x00pci              14202  1 rt61pci
rt2x00lib              48146  2 rt61pci,rt2x00pci
snd_emu10k1           133258  3 snd_emu10k1_synth
mac80211              393421  2 rt2x00pci,rt2x00lib
snd_hda_intel          28358  3 
cfg80211              172427  2 rt2x00lib,mac80211
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13132  0 
snd_rawmidi            25241  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
eeprom_93cx6           12653  1 rt61pci
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
emu10k1_gp             12570  0 
gameport               15060  2 emu10k1_gp
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_ac97_codec        106082  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  5 snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_timer              28932  3 snd_emu10k1,snd_seq,snd_pcm
parport_pc             32114  1 
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  24 snd_hda_codec_hdmi,snd_emux_synth,snd_seq_virmidi,snd_hda_codec_realtek,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_seq,snd_ac97_codec,snd_pcm,snd_hwdep,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
floppy                 60310  0 
r8169                  47200  0 
[/HTML]

I'm using 11.10 at the moment.

Cheers

---

### Post by gordintoronto on 2012-02-27
I think you need to run System Settings, then select "Displays."

---

### Post by michaell4 on 2012-02-28
> **gordintoronto said:**
> I think you need to run System Settings, then select "Displays."

That was the first thing I tried.
The monitor which is detected is listed as 'Unknown'.

Cheers

---

### Post by gordintoronto on 2012-02-28
What brand and model of monitors are you using? How are they connected to your video adapter? (DVI, VGA, HDMI, Displayport) Have you tried switching them? It's a lot easier to help you if you provide relevant information.

---

### Post by HavarN on 2012-03-01
This is an nVidia card, as Pilot6 pointed out was obvious before we got it confirmed, kudos to Pilot6 for that. It also seems like you are using the proprietary nvidia driver. Therefore, you need to use the nvidia-settings tool to configure your monitor setup. You can't use the System Settings->Displays tool. Run this command from ALT+F2 or from a terminal:```
nvidia-settings
```

But you probably knew that already. I have had similar problems on my nvidia computers. I had to switch from LightDM to GDM, for my computers to work properly with the proprietary nvidia driver installed. With gdm, I also had to reconfigure the keyboard-configuration package to use the right layout for my keyboard.```
sudo apt-get install gdm
sudo apt-get remove lightdm
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by michaell4 on 2012-03-03
Hi guys,

I've sorted the issue now. Don't know why, but after the 5th time of removing and reinstalling drivers, it worked.

I already had nvidia-settings tool installed, but that was also having issues detecting the other monitor.

Thanks for your help!

---

