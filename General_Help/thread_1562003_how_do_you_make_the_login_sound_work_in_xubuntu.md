---
title: "how do you make the login sound work in xubuntu?"
date: 2010-08-27
forum: General Help
---

### Post by LxxRyuzaki on 2010-08-27
how do you make the login sound work in xubuntu?

Is there any way to make a login sound work in xubuntu 10.4?

---

### Post by x1a4 on 2010-08-27
Run gdmsetup: 
```
gksudo gdmsetup
```

On Hardy the menu path is Settings > Login window

---

### Post by LxxRyuzaki on 2010-08-27
I have tried login window and the terminal text gksudo gdmsetup, and play the login sound is checked, but I don't hear it when I restart xubuntu.

---

### Post by x1a4 on 2010-08-27
Did you specify which sound you want to play?

---

### Post by LxxRyuzaki on 2010-08-28
I'm using Xubuntu 10.4, so, it doesn't let me specify a sound to use.

---

### Post by x1a4 on 2010-08-28
Really?!  That's strange.  I know that recent changes to GDM have taken away many features, but if it's possible to enable sound, it should also be possible to set which sound to play.  

I attached a screenshot of gdmsetup on my system and highlighted where you have to click to set the sound file.  Is this the same as yours?

If you are still unable to to it using the GUI, try editing the GDM config file.  In file [COLOR="RoyalBlue"]**/etc/gdm/gdm.conf**[/COLOR] add 
```
SoundOnLoginSuccessFile=/path/to/sound-file.wav
```
in the **[greeter]** block

---

### Post by LxxRyuzaki on 2010-08-28
I went to etc/gdm, and in there is something called custom.conf, so I added SoundOnLoginSuccessFile=/usr/share/sounds/purple/login.wav to the custom.conf, and I rebooted my netbook, and I heard no login sound, weird. I have Xubuntu, and Xfce.

---

### Post by cottfcfan on 2011-03-08
Has anyone managed to solve this problem?
I'm experimenting with Xubuntu 10.10 and can find no way of getting a login sound.
Is it even possible?

---

### Post by Wobblybob on 2011-03-08
Hi I use Xubuntu 10.10 and have managed to get a startup sound working by creating a script in my home folder that plays a sound then adding it in [Settings], [Settings Manager], [session and Startup], [Application Autostart]

```

#!/bin/sh
#### play sound at startup ####
## reduce volume ##
sleep 5
/usr/bin/amixer -c 0 sset Master,0 60%
## play sound ##
/usr/bin/ogg123 /home/martin/systems_sound.ogg
## increase volume again ##
/usr/bin/amixer -c 0 sset Master,0 85%

```

---

### Post by cottfcfan on 2011-03-09
Thanks for your reply Wobblybob.
Tried your suggestion, but got no joy. I followed your script, but when I ran it in a Terminal it got stuck in a loop, but still no sound.
I'll try again later.

---

### Post by anglican on 2011-03-09
> **LxxRyuzaki said:**
> how do you make the login sound work in xubuntu?

Is there any way to make a login sound work in xubuntu 10.4?Well you could get a login sound by adding an autostarted application something like:
```
play /usr/share/sounds/login.wav
```
You'll need to install sox and gnome-audio.

H

---

### Post by cottfcfan on 2011-03-09
Thanks Anglican.
That works perfectly.

---

### Post by Wobblybob on 2011-03-11
another Hull Linux user, hello mate, small World

did you change the line

/usr/bin/ogg123 /home/martin/systems_sound.ogg

and give a location to a sound of your own and I found .ogg files to be the only ones that work. You should be able to paste your amended line in a Terminal and as a test and hear the sound. You may have to install ogg123

---

### Post by cottfcfan on 2011-03-13
Thanx for your help wobblybob.
They were wav files I was using not ogg, maybe that caused the problem.
Anyway fixed the problem using Anglican's method above.

---

