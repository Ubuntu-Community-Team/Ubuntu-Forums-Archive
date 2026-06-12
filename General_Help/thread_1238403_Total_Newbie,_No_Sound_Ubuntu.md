---
title: "Total Newbie, No Sound Ubuntu"
date: 2009-08-12
forum: General Help
---

### Post by Ericnpeterson on 2009-08-12
I just installed Ubuntu on my desktop and I cannot get any sound to come out of the speakers, does anyone have any suggestions? I checked the levels and they are all up and it is not muted. I dont know what else to do.

---

### Post by rhchia on 2009-08-12
i have this problem when i'm using hardy. 
try this
- right click the volume icon and choose preference.  select HDA Intel (ALsa mixer)
- right click the volume icon and choose open volume control, check all of then is not mute (the lever bar shld be high up)

---

### Post by NightwishFan on 2009-08-12
A simple interface to check volume is alsmixer. Open a terminal: Application -> Accessories -> Terminal

Type this command and then push enter.
```
alsamixer -c0
```
Press esc to exit the alsamixer.

We can help you from there. Also, what are you trying to play sound from.

---

### Post by Ericnpeterson on 2009-08-12
> **NightwishFan said:**
> A simple interface to check volume is alsmixer. Open a terminal: Application -> Accessories -> Terminal

Type this command and then push enter.
```
alsamixer -c0
```Press esc to exit the alsamixer.

We can help you from there. Also, what are you trying to play sound from.


So here is the issue, I have tried using the onboard sound to no avail I have a behringer UCA202 USB sound card that I can use as well. I plugged int he behringer and I can get sounds when I do a test but both VLC and Youtube will not make any sound.

---

### Post by Soapy.Illusions on 2009-08-12
> **Ericnpeterson said:**
> So here is the issue, I have tried using the onboard sound to no avail I have a behringer UCA202 USB sound card that I can use as well. I plugged int he behringer and I can get sounds when I do a test but both VLC and Youtube will not make any sound.
 
Can you go to your terminal and run
 
```

aplay -l

```
 
To see what sound card you have on board

---

### Post by Ericnpeterson on 2009-08-12
> **Soapy.Illusions said:**
> Can you go to your terminal and run
 
```

aplay -l

```To see what sound card you have on board

Sure, here is the response: 

card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by NightwishFan on 2009-08-12
I am not sure of the exact problem. Try this out.

```
killall pulseaudio && speaker-test
```

Do you get any sound?

Here is a reference to sound problems if I cannot help much. I will continue to try while I am still online though.

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Ericnpeterson on 2009-08-12
> **NightwishFan said:**
> I am not sure of the exact problem. Try this out.

```
killall pulseaudio && speaker-test
```Do you get any sound?

Here is a reference to sound problems if I cannot help much. I will continue to try while I am still online though.

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

I did some searching before I posted here and I think I already got rid of the pulseaudio when I ran that command I got this: 

pulseaudio: no process killed

When I ran the speaker test I got no sound, with either the USB card or the onbaord card

---

### Post by NightwishFan on 2009-08-12
Try this in a terminal:

```
pulseaudio
```

Then see if you get any sound in speaker-test or vlc/totem/firefox.

---

### Post by Ericnpeterson on 2009-08-12
> **NightwishFan said:**
> Try this in a terminal:

```
pulseaudio
```Then see if you get any sound in speaker-test or vlc/totem/firefox.

Here is the response:

The program 'pulseaudio' is currently not installed.  You can install it by typing:
sudo apt-get install pulseaudio
bash: pulseaudio: command not found



And let me say thanks to all that have been helping so far. You guys are awesome. I really want to make Ubuntu work for me.

---

### Post by NightwishFan on 2009-08-12
How did you install the Ubuntu system? If you want the standard Ubuntu GNOME desktop, pulse should be installed.

In simple terms, if your system was orange when you installed it, and had 2 panels one at the top and one at the bottom, you have GNOME, and you should run this command.

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by P4man on 2009-08-12
Is it possible you're using a really old ubuntu version?
Pulse audio should be installed by default on anything less than .; what 3 years old?

---

### Post by Ericnpeterson on 2009-08-12
> **NightwishFan said:**
> How did you install the Ubuntu system? If you want the standard Ubuntu GNOME desktop, pulse should be installed.

In simple terms, if your system was orange when you installed it, and had 2 panels one at the top and one at the bottom, you have GNOME, and you should run this command.

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

I ran that and did a restart.

---

### Post by Ericnpeterson on 2009-08-12
> **P4man said:**
> Is it possible you're using a really old ubuntu version?
Pulse audio should be installed by default on anything less than .; what 3 years old?

I know, It was installed. I read else where to uninstall it as part of some other fix but it didnt work.

---

### Post by NightwishFan on 2009-08-13
Any updates? Still not working?

---

