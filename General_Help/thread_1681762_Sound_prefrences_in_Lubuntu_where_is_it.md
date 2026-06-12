---
title: "Sound prefrences in Lubuntu? where is it"
date: 2011-02-04
forum: General Help
---

### Post by 4042966262 on 2011-02-04
where is sound preferences in Lubuntu? i have speakers plugged in and lit up, i see the sound icon and can slide it up/down however no sound. i am guessing it is not reading my speakers as the default. Where is sound preferences):P

---

### Post by cavalier911 on 2011-02-05
Install gnome-alsamixer
menu/sound &video/gnome alsa mixer

---

### Post by SteveDee on 2011-02-05
> **cavalier911 said:**
> Install gnome-alsamixer...

...or just open a terminal and type:-
```

alsamixer

```
..its not so user friendly, but once you have your sound working you generally don't need to keep going back to these controls.

---

### Post by 4042966262 on 2011-02-05
alsamixer brings  me to a terminal box with graphical controls. i hit f6 and select my sound card USB Audio Dc then im looking at a signal bar. i don't know if this set the card as default? or what else do i have to do?

---

### Post by SteveDee on 2011-02-05
> **4042966262 said:**
> alsamixer brings  me to a terminal box with graphical controls....

Start by selecting F3 (playback)

Use left/right arrows to select a control, up/down to set the level, and "m" key to mute/unmute. (MM=mute)

Unmute just about everything and bring the levels up until you can hear something from your speakers.

You can also open a second terminal (while alsamixer is still visible in the first terminal) and type:- 
```

speaker-test -t sine

```
...which should give you a sound to work with while fiddling with alsamixer levels

---

### Post by 4042966262 on 2011-02-05
im not doing something right? hitting F3 brings me back to blank terminal

---

### Post by SteveDee on 2011-02-06
> **4042966262 said:**
> im not doing something right? hitting F3 brings me back to blank terminal

When you first launch alsamixer from the terminal, it will probably display the controls for your sound card, as long as your sound card has been properly detected. (see attached example).

If your card name is displayed on this initial screen, you should just need to un-mute controls and adjust levels.

If your card name is not listed, then you may have a sound card problem. Open a terminal and type:-
```

sudo aplay -l

```
This should display sound card info, but if it says something like "no soundcard" then support for your device may be missing.

---

### Post by 4042966262 on 2011-02-06
kimball@kimball-desktop:~$ sudo aplay -l
[sudo] password for kimball: 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kimball@kimball-desktop:~$

---

### Post by 4042966262 on 2011-02-06
kimball@kimball-desktop:~$ sudo aplay -l
[sudo] password for kimball: 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kimball@kimball-desktop:~$

ok.. so how do i unmute levels?

---

### Post by SteveDee on 2011-02-06
> **4042966262 said:**
> 

ok.. so how do i unmute levels?

At the alsamixer screen, muted controls have "MM" at the bottom (in my illustration the "Master M" control is muted).

 - So use left or right arrow keys to move to the muted control (the text colour changes to red when selected).
 - Hitting the "m" key once should un-mute the control, and the "MM" will probably change to "00".
 - Now use the up arrow key to wind-up the level (the 00 will change as the level goes up).

---

