---
title: "Logitech C260 crashes TVtime"
date: 2011-09-20
forum: General Help
---

### Post by fragos on 2011-09-20
TVtime and my old webcam got along nicely other than which one got /dev/video0. Replaced my old webcam with a Logitech C260 and it worked without any configuration as expected. Start TVtime and it crashes. Unplug C260 and TVtime runs fine. If while TVtime is running I plug in the C260 and both work. Here's what I get on the terminal if TVtime is started from the CLI with the C260 plugged in.

fragos@Geo:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/fragos/.tvtime/tvtime.xml
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL 
mixer: attach error: No such file or directory
mixer: Can't open mixer , mixer volume and mute unavailable.
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Found "USB Device 0x46d:0x825 : USB Audio (hw:3,0)"
Channels count non availablefragos@Geo:~$ 

Here's my tvtime.xml

<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Matte" value="4:3"/>
  <option name="Channel" value="3"/>
  <option name="WideScreen" value="0"/>
  <option name="InputWidth" value="768"/>
  <option name="DefaultBrightness" value="45"/>
  <option name="DefaultContrast" value="40"/>
  <option name="DefaultSaturation" value="50"/>
  <option name="DefaultHue" value="50"/>
  <option name="PrevChannel" value="99"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="5.0"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="-1"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="0"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
  <option name="NTSCCableMode" value="IRC"/>
  <option name="Fullscreen" value="0"/>
  <option name="Verbose" value="0"/>
  <option name="WindowGeometry" value="0x600"/>
  <option name="V4LDevice" value="/dev/video/bttv"/>
  <option name="VBIDevice" value="/dev/vbi0"/>
  <option name="Norm" value="NTSC"/>
  <option name="Frequencies" value="us-cable"/>
  <option name="MixerDevice" value="/dev/mixer:line"/>
  <option name="XMLTVFile" value="none"/>
  <option name="XMLTVLanguage" value="none"/>
  <option name="ProcessPriority" value="-10"/>
<option name="ShowCC" value="0"/><option name="DeinterlaceMethod" value="AdaptiveSearch"/></tvtime>

Any ideas anyone? I created /dev/video/bttv with a udev rule to solve the random video0 problem.

---

