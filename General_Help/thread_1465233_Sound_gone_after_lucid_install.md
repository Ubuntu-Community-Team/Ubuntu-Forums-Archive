---
title: "Sound gone after lucid install"
date: 2010-04-29
forum: General Help
---

### Post by cmcanulty on 2010-04-29
This is annoying.After Lucid inbstall I can pull up any video and no sound. I messed with this forever and fixed it under Karmic.Did so much I have no idea which thing fixed it. I have downloaded tons of repositories and players with no luck. Sound doesn't work on even music files now.

---

### Post by dino99 on 2010-04-29
install with synaptic: ubuntu-restricted-extras

you can search (into synaptic) about: codec(s) and install the ones you miss

more codecs available with medibuntu repo (see below)

gnome-alsamixer can tweak your wish

---

### Post by cmcanulty on 2010-04-29
the extras are already installed OK my volume icon has full volume but the pulse audio vol control has little red xs next to each speaker icon. But I can't find a way to remove the x's

---

### Post by lidex on 2010-04-29
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by mencial on 2010-04-29
Hello.

I am having the same issue.

Here is my output (some of it is in Spanish):

```

~$ uname -a
Linux pablo 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC889A Analog [ALC889A Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC889A Digital [ALC889A Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A

```

Computer is self-made. I can go and look the make of the board and the on-board sound card if you want.

Thanks and regards!

---

### Post by dnr1128 on 2010-04-29
Related question:  My sound works fine, but there's no volume control where karmic had one up by the clock.  anyway to put one there other than putting a button for the whole sound control panel?

---

### Post by rldsoftware on 2010-04-30
I have the same problem, no sound in new lucid install. I had the development version (beta) and it worked, just installed the new release and sound is gone.

My info:

rvl@ub01:~/Downloads$ uname -a
Linux ub01 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
rvl@ub01:~/Downloads$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rvl@ub01:~/Downloads$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
rvl@ub01:~/Downloads$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

---

### Post by lidex on 2010-04-30
Go to "System>Preferences>Sound" and make sure the correct soundcard is default. Check volume levels in pulse. Check levels in alsamixer.

---

### Post by marshmallow1304 on 2010-04-30
> **dnr1128 said:**
> Related question:  My sound works fine, but there's no volume control where karmic had one up by the clock.  anyway to put one there other than putting a button for the whole sound control panel?

In Lucid, the volume control has been moved from Notification Area to Indicator Applet.  If you're using old settings, you might need to add the Notification Area to the panel.  Alternately, this will add an icon like the one that was there before for the current session.
```
gnome-volume-control-applet &
```

---

### Post by Keith1212 on 2010-05-02
> **marshmallow1304 said:**
> In Lucid, the volume control has been moved from Notification Area to Indicator Applet.  If you're using old settings, you might need to add the Notification Area to the panel.  Alternately, this will add an icon like the one that was there before for the current session.
```
gnome-volume-control-applet &
```
works but soon as i closed the terminal  it dissapeared. I ended  up having to add   it to startup apps. seems kinda odd to have to do this.

---

### Post by lidex on 2010-05-03
For lucid, right-click the panel, click 'add to panel', select 'indicator applet'

---

### Post by cmcanulty on 2010-05-03
Thanks now I have the icon but I still have no sound. Before I just kept adding apps until it worked but I hope there is a more intelligent way to go about it.

---

### Post by lidex on 2010-05-04
> **cmcanulty said:**
> Thanks now I have the icon but I still have no sound. Before I just kept adding apps until it worked but I hope there is a more intelligent way to go about it.

Can you post the info asked for in post #4?

---

### Post by cmcanulty on 2010-05-05
Sorry somehow I missed that:also I installed gnome-mplayer no change

```
cmcanulty@Gateway:~$ uname -a
Linux Gateway 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
cmcanulty@Gateway:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cmcanulty@Gateway:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
cmcanulty@Gateway:~$ head -n 1 /proc/asound/card*/codec#*

```

---

### Post by lidex on 2010-05-05
One more please:
```
head -n 1 /proc/asound/card0/codec97#0/ac97#0-0

```

Also, check your levels in alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by cmcanulty on 2010-05-05
```
cmcanulty@Gateway:~$ head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Conexant Cx20468-31
cmcanulty@Gateway:~$ 
```
screenshot of mixer attached. I had gone into that before but never figured out how to use thanks for the info on the f keys the sound preferences doesn't seem to have a choice for sound card
```

cmcanulty@Gateway:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
cmcanulty@Gateway:~$
```
everything worked until upgrade to Lucid

---

### Post by lidex on 2010-05-05
First thing do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Now do 'Part 1/5' here (only the preparation and installation for 8.10 and higher):
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Report your results.

---

### Post by cmcanulty on 2010-05-05
Wow that worked! Thanks. I had installed pulse  audio trying to fix  this earlier and then deleted it  but now it works.I think the problem was I didn't understand how to adjust the Alsa Mixer though now I see that it is explained on top but I missed that and just got frustrated.

---

### Post by lidex on 2010-05-05
Fantastic. Could you mark the thread as solved using 'Thread Tools' up top please?

---

### Post by cmcanulty on 2010-05-06
Not solved. I turned on my laptop and no sound again. On the pulse audio volume control everything has little red x's next to the speakers which is what it had when I installed it on my own before. The sys volume icon is set all the way up. I am again getting no sound, very frustrating. I changed nothing since last night . I am attaching a screenshot.
I am troubleshooting alsa mixer shows default soundcard. I tried setting it to ati ixp but it won't keep changes.

---

### Post by lidex on 2010-05-06
Alsa likes to reset to default, which is muted. Check alsamixer.

---

### Post by cmcanulty on 2010-05-07
I just reinstalled Lucid after a pulse audio uninstall made my laptop unbootable and now the volume works fine, thanks everyone

---

### Post by amplexus on 2010-05-08
Hello there,

I've lost sound on upgrading to Lucid too. Here's the output that Lidex asked for:

Linux dell-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
paul@dell-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@dell-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
paul@dell-desktop:~$ head -n 1 /proc/asound/card*/codec#*

I've checked the sound levels on alsamixer; they aren't muted. 

V. sad ...

Thanks for your time.

---

### Post by cmcanulty on 2010-05-11
Well now my sound has gone again, I just want to listen to my podcasts! Lucid has been nothing but big trouble.

---

### Post by cmcanulty on 2010-05-11
No sound again!

---

### Post by allxk on 2011-02-23
==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID d

---

