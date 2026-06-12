---
title: "No HDMI Out to TV"
date: 2010-11-14
forum: General Help
---

### Post by onaridge on 2010-11-14
Though I had solved this but I was premature. Here are the details.

When I use HDMI to connect to my lcd TV it works fine in Windows7. (I have dual partitions W7/Ubuntu),but when I boot into Ubuntu and use HDMI, nothing happens. Some of this info may help?


lori@lori-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lori@lori-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0400000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd0310000 irq 19


also when I open the Gnome Alsa Mixer, under the HDMI tab, there is just a blank screen. I believe I have the latest Alsa releases. Can anyone help me please?

---

### Post by sohlinux on 2010-11-14
its a laptop right?

 when I boot with ubuntu and use my hdmi tv I always have to hit FN and F7 to switch the tv output.

if that doesnt work check your display settings/resolution  in -  system - preferences - monitors

---

### Post by onaridge on 2010-11-14
Yes and I went to try out your suggestion and as soon as I plugged the HDMI cable in it worked. The only thing I did was install the latest alsa from the terminal. Maybe I didn't have the latest?

---

### Post by efflandt on 2010-11-14
Are you having trouble with HDMI video too, or just audio?  For a laptop with ATI video, if you boot with an external display already on, BIOS usually switches to that display, and by default X picks a resolution it thinks will work mirrored on both displays.

But the only laptop I have with ATI is too old for proprietary drivers, so it uses default drivers and has VGA external and defaults to using 1024x768 for both displays.  I use a script with xrandr commands to change that when connected to external display, but that might not work with ATI proprietary drivers.

I got HDMI sound working for my nvidia on a desktop in 10.10 with options for snd-hda-intel in one file and an /etc/asound.conf to cooperate with Sound Preferences (pulse).  But I don't know if it works the same for ATI, especially if **alsamixer** does not show anything at all if you use F6 to show HDA ATI (at least one, if not more, S/PDIF).

If you are running a version of Ubuntu before 10.10 you may need to update your alsa version to 1.0.23 to do HDMI audio.

---

### Post by onaridge on 2010-11-14
It was both, no nothing just a blue TV screen when I switched over to HDMI2 which is the computer input.  Any searches I did on this problem frequently mentioned Alsa and that's the only thing I changed. But yes I have the latest version now and I am running Lucid so I bet that's it. I downloaded it from the unstable repository now that I think of it so the version available on the stable Ubuntu repositories is older than the latest version I got from unstable. That must have been the fix.

---

