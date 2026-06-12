---
title: "Lubuntu audio issues"
date: 2012-04-10
forum: General Help
---

### Post by lun on 2012-04-10
DISREGARD:

> I am running Lubuntu 12.04 Beta2 on my desktop and am having some audio issues.

The issue: The problem comes in multiple parts.

1. On a fresh install i had no audio. Levels were up on alsamixer. I installed pulseaudio and got volume.

2. Here is what is happening. I have an optical out to my sound system. Thus my output is digital. When outputting audio, i have no control over the volume from the PC other than mute. Otherwise the volume coming from the PC is always on the highest level and i can only control it through my sound system.

3. If i run an audio cable, analog out, i can control the volume through the PC.

4. Except for mute. If i mute the volume from the keyboard key, the only way to unmute the volume is by left clicking the audio symbol in the LXpanel and unchecking mute. This occurs whether i am using analog or digital out.


The specs:

-Core i7, thus 64bit
-integrated audio Realtek ALC889
-there is also HDMI audio which it doesnt seem to default to that
-i think these are the important specs.


aplay -l:

card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...


The issue is not Lubuntu recognizing my sound, its configuring Lubuntu to use the sound in the manner i desire.  I know this is possible because i am coming from Ubuntu which has audio settings which allow me to select my audio preferences.  If it helps in Ubuntu i select 'Digital Strereo (IEC958) Output.

Any help would be appreciated, whether it be configuring my audio files to produce desired effect or an audio/volume control/preferences that gives me the option to do so.

Thanks,
nick.
--------------------------------------------------------------------

I spoke too soon. I have installed pulseaudio and pavucontrol on my Lubuntu system. The only issue i have now is getting the volume increase and decrease keys to interact with the Lubuntu volume control. Currently i can only adjust volume using the mouse on the control.

--------------------------------------------------------------------

Fixed. Needed to add the option -D pulse in the openbox rc.xml.
[https://wiki.archlinux.org/index.php/Openbox#Pulseaudio](https://wiki.archlinux.org/index.php/Openbox#Pulseaudio)

So for users having difficulties with their audio settings in Lubuntu, i suggest installing pulseaudio and pavucontrol:
```
sudo apt-get install pulseaudio pavucontrol
```
Restart. In order to get your multimedia keys working, edit your openbox rc.xml:
```
nano .config/openbox/lubuntu-rc.xml
```
and edit the 'Keybinding for Volume management' section to the following:
```

    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%+ unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%- unmute</command>
      </action>
    </keybind>
```
Hope this helps.
nick

---

### Post by Jiraya_90 on 2012-06-17
thank a lot my friend you've been far more than "helpful" may the force be with you! :)

---

### Post by Kevbo on 2012-10-25
Fantastic!  Thanks lun.  Lubuntu on my daughter's aspire one 725 is lightning fast, but she really wanted the function keys for volume.  You saved us from the slower unity desktop.  Again, thanks. :)

---

### Post by crazy iwan on 2012-11-23
I also just wanted to thank a lot for the advice.

I really love Lubuntu right now. Everything runs just smoothly and stable.

greez

iwan

---

