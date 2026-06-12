---
title: "No sound icon/slider in 10.04?"
date: 2010-07-02
forum: General Help
---

### Post by dzwestwindsor on 2010-07-02
In order for skype to work properly, i had to get rid of pulseaudio.

Now skype works, all the sounds works, but....

I don't have a volume control..... I can't even open up the volume/sound dialogue box!!!!

It just says "waiting for sound system to respond" which it never does.

Does anyone know why? Isn't pulse audio optional? so its safe for me to remove right? Then why do i not have volume/sound control anymore? 

ALl the help appreciated :)

---

### Post by mc4man on 2010-07-02
> It just says "waiting for sound system to respond" which it never does.

Does anyone know why?
no pulseaudio

>  Isn't pulse audio optional? 
On ubuntu not at all..

> so its safe for me to remove right?
I gather so ( I've disabled it on one lucid install, not removed

> Then why do i not have volume/sound control anymore? 
No pulseaudio,  no sound control applet (gnome-volume-control) or pulse audio volume control (separate control

I'm sure someone can present you with some way to adjust in the absence of pulse.

Edit
possibly this ppa to get a volume control with no pulseaudio
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

What I did on one install

Being a 5.1 with external volume control I don't usually need a system volume controller but do ocassionally want to adjust the Master Volume, defaulted at 80 here,  so..

I made 2 panel launchers, 1 an up icon (raise volume), 1 a down icon (lower volume)

They are set to raise or lower 1dB per click (about 3%)
They can be clicked on very fast  - sorta like turning a volume knob
The parameters/target are adjustable, -  see man amixer

For up
amixer -c 0 set Master 1dB+

for down
amixer -c 0 set Master 1dB-

---

### Post by kostkon on 2010-07-02
> **dzwestwindsor said:**
> In order for skype to work properly, i had to get rid of pulseaudio.
Why? Skype works just fine with PulseAudio.

---

### Post by Leppie on 2010-07-02
try resetting the gnome-panel:
```
gconftool-2 --recursive-unset /apps/panel | killall gnome-panel


```

alll personalizations of the gnome-panel will be lost though.

---

