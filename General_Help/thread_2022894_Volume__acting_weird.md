---
title: "Volume  acting weird"
date: 2012-07-11
forum: General Help
---

### Post by UnknownDiety on 2012-07-11
For me the volume is acting extremely weird.

[IMG]http://i.imgur.com/NbJOP.png[/IMG]

Whenever I try to use the sound. I first of course unmute the volume.

Well after that the only way for me to get ANY sound whatsoever is it bump it up to the Unamplified line.

To get it to be loud enough for me to hear I have to turn it up almost to the 100% line.

Why don't I get sound anywhere before the Unamplified line?

---

### Post by jmfal on 2012-07-11
Click on the alsamixer link below, and post back if you  still have problems.

---

### Post by UnknownDiety on 2012-07-11
> **jmfal said:**
> Click on the alsamixer link below, and post back if you  still have problems.

[http://imgur.com/a/VjEAU](http://imgur.com/a/VjEAU)

Those're all the screenshots I took of the various settings it does when I turn the volume up or down.

Also when the PCM is up in the red like that it adds a slight static type sound to whatever I'm listening too.

If I could get the master volume to start going up before the Unamplified line I'd be happy. From where it stays really low and then does those drastic jumps is why I can't get the sound at a decent volume.

I've tried using my arrows to adjust the master volume and it helps until I go to change the volume using the Sound Indicator's bar, Sound Settings Windows Bar, or the Volume Buttons on my keyboard.

Let me know if there's any other information that you need.

Please let me know if there's anything else you need to know.

---

### Post by jmfal on 2012-07-11
Increase the master, speaker and try turning down PCM at least out of the red

---

### Post by UnknownDiety on 2012-07-11
> **jmfal said:**
> Increase the master, speaker and try turning down PCM at least out of the red

Turning the PCM just below the red makes the static sound go away.

[http://i.imgur.com/3rAo1.png](http://i.imgur.com/3rAo1.png)

Whenever my settings are like that all I have to do is turn the volume down by one tiny notch on the sound settings or sound indicator bar or hit my lower volume button once and the master volume drops down all the way to 0 and then PCM jumps up to 100 (which makes it go red again).

---

### Post by jmfal on 2012-07-11
Try

```
 sudo alsa force-reload
```

Also the s/pdif controls your midi turn them down to about 75

---

### Post by UnknownDiety on 2012-07-11
> **jmfal said:**
> Try

```
 sudo alsa force-reload
```Also the s/pdif controls your midi turn them down to about 75

Just did the force-reload and it didn't help. Exact same thing is happening as before.

Also the S/pdif and S/pdif d things are set to zero and I can't change them using the up/down arrows.

Thanks for taking your time to help me by the way.

---

### Post by jmfal on 2012-07-11
Did you try changing your sound card in alsamixer

F6>>up/down arrows>> press enter >> esc

Then hit F5 and check all controls for that card, you'll have to play with  it

Have some t-storms starting to roll in so I'm shutting down for the night

Good Luck

---

### Post by UnknownDiety on 2012-07-11
> **jmfal said:**
> Did you try changing your sound card in alsamixer

F6>>up/down arrows>> press enter >> esc

Then hit F5 and check all controls for that card, you'll have to play with  it

Have some t-storms starting to roll in so I'm shutting down for the night

Good Luck

Yes.

These are the options it gave me and I tried both the default and the HDA Intel one.

[IMG]http://i.imgur.com/Wwe3V.png[/IMG]

I've tried messing with it, but I can't seem to get it to work the way it should.

Hope you stay safe.

---

### Post by UnknownDiety on 2012-07-13
Daily Bump

---

### Post by UnknownDiety on 2012-07-15
Daily Bump

---

### Post by Pilot6 on 2012-07-15
I had same problem. I fixed it by editing 
/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf

I changed all "merge" to "ignore".
After that reboot, run alsamixer and set all volumes, you've set to "ignore" to 100%. Then volume will be managed by PCM. 
Volume control will work in a right way.

Also remove and install pulseaudio helps without ediding this file in 12.04.

---

### Post by UnknownDiety on 2012-07-15
> **Pilot6 said:**
> I had same problem. I fixed it by editing 
/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf

I changed all "merge" to "ignore".
After that reboot, run alsamixer and set all volumes, you've set to "ignore" to 100%. Then volume will be managed by PCM. 
Volume control will work in a right way.

Also remove and install pulseaudio helps without ediding this file in 12.04.

So reinstalling pulseaudio might help? 

Would it be better to try reinstalling pulseaudio and then if that doesn't work then edit the analog-output.conf?

How would I reinstall it?

Thanks for the reply.

---

### Post by Pilot6 on 2012-07-15
Yes. It makes sense to try to reinstall first.
```

sudo apt-get purge pulseaudio
sudo apt-get install pulseaudio

```

Reboot after this

---

### Post by Pilot6 on 2012-07-15
But it may cause some problems for a newbie. There are some packages which depend on pulseaudio. You will have to install them again too.

---

### Post by jmfal on 2012-07-15
If that doesn't work try

```
 sudo apt-get install --reinstall libasouond2    
```

And check volume in mixer
Play soome music

---

### Post by UnknownDiety on 2012-07-16
> **Pilot6 said:**
> But it may cause some problems for a newbie. There are some packages which depend on pulseaudio. You will have to install them again too.

I am a newbie.

How would I know which packages this'll potentially conflict with?

---

### Post by Pilot6 on 2012-07-16
When you will remove pulseaudio, you will get a list of packages to be deleted. Save this list. and when you install pulseaudio install these packages again.

---

### Post by UnknownDiety on 2012-07-17
> **Pilot6 said:**
> When you will remove pulseaudio, you will get a list of packages to be deleted. Save this list. and when you install pulseaudio install these packages again.

By doing ```
sudo apt-get install packagenamehere
```? Just making sure.

Thanks for the help also.

/Edit

I reinstalled pulseaudio and then reinstalled the other packages again as you suggested and the issue kept happening. (Rebooted after reinstalling. So then I tried reinstalling the libasound2 as you suggested and it still persists.

/Edit 2 I even tried editing the .conf file as you suggested and it's still having the same issue.

---

### Post by jmfal on 2012-07-17
Yes that is how to install from terminal.

Run this in a terminal and post results

```
   aplay -l
```

And
```
 lsmod   
```

---

### Post by UnknownDiety on 2012-07-17
> **jmfal said:**
> Yes that is how to install from terminal.

Run this in a terminal and post results

```
   aplay -l
```And
```
 lsmod   
```

```
Results for the aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
Results for lsmod

Module                  Size  Used by
joydev                 17393  0 
vesafb                 13516  1 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
binfmt_misc            17292  1 
nvidia              10962290  33 
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72919  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
r852                   17901  0 
iwl3945                73152  0 
sm_common              16737  1 r852
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
r592                   17808  0 
iwl_legacy             71134  1 iwl3945
nand_ecc               13070  1 nand
memstick               15857  1 r592
mac80211              436455  2 iwl3945,iwl_legacy
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
video                  19068  0 
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
e1000e                140005  0 

```

---

### Post by jmfal on 2012-07-17
Did you add an option to the  alsa-base.conf. file,  as one op requested.

What model PC/laptop is having problems?

---

### Post by UnknownDiety on 2012-07-17
> **jmfal said:**
> Did you add an option to the  alsa-base.conf. file,  as one op requested.

What model PC/laptop is having problems?

I didn't see anyone mention alsa-base.conf in here unless if I just skipped over it or is it in another thread?

HP Pavillion dv6275us Laptop is what's having the issues.

---

### Post by jmfal on 2012-07-17
I'm sorry helping a couple of others with sound problems, and almost same model laptop.
Run this in a terminal
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf      
```

Enter password in window, and file will open.
Scroll to end of file and add this:
```
 options snd-hda-intel model=hp       
```
Save/close to the etc folder (click on etc>>click save)
Run these three commands one at  a time:
    ```
  killall pulse audio
                    sudo alsa force-reload
                   pulseaudio  _D     
```
Don't worry about errors
Restart laptop
check in alsamixer that all speakers are not muted 
Play some music
If still have cracks/pops play with pcm /volumes in mixer
If that doesn't do it we'll try another one

---

### Post by UnknownDiety on 2012-07-17
> **jmfal said:**
> I'm sorry helping a couple of others with sound problems, and almost same model laptop.
Run this in a terminal
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf      
```Enter password in window, and file will open.
Scroll to end of file and add this:
```
 options snd-hda-intel model=hp       
```Save/close to the etc folder (click on etc>>click save)
Run these three commands one at  a time:
    ```
  killall pulse audio
                    sudo alsa force-reload
                   pulseaudio  _D     
```Don't worry about errors
Restart laptop
check in alsamixer that all speakers are not muted 
Play some music
If still have cracks/pops play with pcm /volumes in mixer
If that doesn't do it we'll try another one

Alright tried all of that and it's still doing what it's been doing.

---

### Post by jmfal on 2012-07-17
OK then , open that file again

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf    
```

And add this to the other option

```
 options snd-hda-intel position_fix=1     
```

Restart laptop
check alsamixer again
play some music
again you may have to play with pcm/ volumes 
If that doesn't do it change "1" to "2".

Also since you say that tha controls jump when adjusting them  try playing with the mouse sensitivity. just a thought

---

### Post by UnknownDiety on 2012-07-17
> **jmfal said:**
> OK then , open that file again

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf    
```And add this to the other option

```
 options snd-hda-intel position_fix=1     
```Restart laptop
check alsamixer again
play some music
again you may have to play with pcm/ volumes 
If that doesn't do it change "1" to "2".

Also since you say that tha controls jump when adjusting them  try playing with the mouse sensitivity. just a thought

Tried 1 and that didn't work so I changed it to 2 and then rebooted and it didn't work either.

When I say the control jumps I don't mean the little arrow or the marker. I'm talking about the actual volume itself jumps alot. Like if I were to have the alsamixer open while I'm moving the volume using the volume bar it stays at 0 until I get to the Unamplified mark. Then it jumps to 23 and then just keeps moving by high amounts like that which makes it difficult to find a good volume to listen to.

Also if I've got the marker to the farthest left of the sound bar (Set to mute essentially) and then move it to the right once the PCM goes to 100%.

---

### Post by jmfal on 2012-07-17
Let try setting "=hp" to "=auto" in the first option

If no, then change "2" back to"1" (no quotes)
 restart 
check alsamixer
try  some music

---

### Post by UnknownDiety on 2012-07-18
> **jmfal said:**
> Let try setting "=hp" to "=auto" in the first option

If no, then change "2" back to"1" (no quotes)
 restart 
check alsamixer
try  some music

Tried doing hp and auto for both 1 and 2 and it's still doing it.

Just to make sure I had the options added properly I'm going to post my alsa-base.conf here:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=hp
options snd-hda-intel position_fix=2
```

---

### Post by jmfal on 2012-07-18
Was the first option   (3rd from bottom of file) there or did you add it?
If you added it, remove it (don't comment out (#))
It is already in the section above.

You can try changing  (=hp) to (=laptop-hp)

---

### Post by UnknownDiety on 2012-07-18
> **jmfal said:**
> Was the first option   (3rd from bottom of file) there or did you add it?
If you added it, remove it (don't comment out (#))
It is already in the section above.

You can try changing  (=hp) to (=laptop-hp)

It was already there.

Still want me to remove it even though I didn't add it or should I just leave it?


Just did the hp to laptop-hp thing, rebooted, and no change.

---

### Post by jmfal on 2012-07-18
Yes remove it .  For all I know its being loaded twice because its there.

Here is where the info is from,

[http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu](http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu)

Go through it and check links, it's probably something simple.

---

### Post by UnknownDiety on 2012-07-18
> **jmfal said:**
> Yes remove it .  For all I know its being loaded twice because its there.

Here is where the info is from,

[http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu](http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu)

Go through it and check links, it's probably something simple.

I checked through the links and I couldn't find my  model being listed even when using Ctrl+F to make sure that I didn't skip over it.

I tried setting it back to model=auto and then doing enable_msi=1, but that didn't work either.

---

### Post by jmfal on 2012-07-18
Try changing =hp or whtever you have there (I forgot)
to =riptide

---

### Post by UnknownDiety on 2012-07-18
> **jmfal said:**
> Try changing =hp or whtever you have there (I forgot)
to =riptide

Tried that and it didn't work either.

---

### Post by jmfal on 2012-07-18
Alright try this
change  =riptide to
=laptop-hpmicsense

Can you do me a favor and post the options we added after you change this one.

---

### Post by UnknownDiety on 2012-07-18
> **jmfal said:**
> Alright try this
change  =riptide to
=laptop-hpmicsense

Can you do me a favor and post the options we added after you change this one.

```
options snd-hda-intel model=laptop-hpmicsense
options snd-hda-intel position_fix=0
```Also now when I move the volume in alsamixer it shows that the master volume is changing at smaller increments (Like it should). Thank you for that.

The PCM jumps to 63 after turning the volume up by one notch and then 100 after going up a second notch, but it doesn't seem to be doing the tiny bit of static thing anymore with PCM at 100 so it seems to be completely fixed.

Thanks very much for using your time to help me. I really appreciate it.

I'll mark the thread as solved now.

---

### Post by jmfal on 2012-07-18
Your welcome
Good luck

---

