---
title: "Need help with X"
date: 2011-01-06
forum: General Help
---

### Post by silameth on 2011-01-06
I was trying to run oblivion with wine(videos of ppl doing it). I could not get to work so I looked on google.
Found out my Xorg.conf is not even there just a Xorg.conf.failsafe
It reads like this:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I have the intel gma 950
How would I fix this? 

One site said start in recoverymode and run X -configure.
I can't even figure out how to get in recovery mode. I am runn Ubuntu 11.04
Any help would be appreciated.

---

### Post by lrgmmc on 2011-01-06
I belive they done away with xorg.conf as of 10.04. what is it you need to change?

---

### Post by silameth on 2011-01-06
I am needing to figure out how to get it to recognize my video card so I can run this game. apparently it has setup for generic video.

Thanks for a quick response

---

### Post by Topsiho on 2011-01-06
Hello,

The first thing you could try to do is so simple that even I can help you: you say you have a xorg.conf.failsafe file (it should be in the directory /etc/X11).
You may try what happens when you copy this (as root) to xorg.conf, and then try to reboot your computer.

Maybe you have to change the driver from "fbdev" to the general purpose driver "vesa". But try the fbdev first, it's not there for nothing.

That's how I solved my problem with my graphic card the other day.
Vesa is a general purpose driver, which doesn't know the fine points of your card, but it probably works.

Topsiho

---

### Post by hansolo4949 on 2011-01-06
Yikes, topsiho, I wouldn't do that unless I was desperate! It only takes one extra space in the wrong place to mess up your system! I think the way to boot into recovery mode is when the computer is booting up, after the bios screen, press e, or shift (I think it's "e"). That will get you into a boot selection screen. simply select Ubuntu (whatever your kerner version is) recovery mode, and viola! you're in recovery mode, and can input your commands.

hansolo4949

---

### Post by silameth on 2011-01-06
Thanks I will try that one....

---

### Post by Topsiho on 2011-01-06
Thanks Hansolo4949,

One can get desperate you know :)
When nothing works except ...
When changing files one should always be very careful.

But thanks anyway, I don't want to give dangerous advice to any one (pun intended!).

Topsiho

---

### Post by lrgmmc on 2011-01-06
have you checked to see if 3d is working now. it might be. and in that case it is probbly the card. intel is not a good card for running any games. esspesialy through wine. 
 
the code to check for 3d is ```
glxinfo | grep render
```

---

### Post by silameth on 2011-01-06
@Hansolo4949 : Pressing e just made it check disk for errors

@IRGMMC : how would I check the 3d? You can slap me later for not knowing....lol

---

### Post by lrgmmc on 2011-01-06
open up termanel and enter this command ```
glxinfo | grep render
```
it will say yes or no.

---

### Post by silameth on 2011-01-06
It says yes so I take it this means I may not be able to play Oblivion?

---

### Post by lrgmmc on 2011-01-06
how did you install it? just with wine or did you use PlayonLinux?

---

### Post by silameth on 2011-01-06
I used Wine. The initial menu comes up but when I click play I just get a white screen with the music playing.

---

### Post by lrgmmc on 2011-01-06
it's elder scrolls right? if so download playonlinux and install the game from there. it sets up wine to work with the game.

---

### Post by silameth on 2011-01-06
I will try that
Thanks
 do I just google play on linux?

---

### Post by lrgmmc on 2011-01-06
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) go down to ubuntu and select 
PlayOnLinux: [[COLOR=#00aaff]PlayOnLinux_3.8.8 .deb[/COLOR]]("http://www.playonlinux.com/script_files/PlayOnLinux/3.8.8/PlayOnLinux_3.8.8.deb"). download it and then install it

---

### Post by silameth on 2011-01-06
Now will i always have to be online to play or just for the install, cause I don't always have net.

---

### Post by lrgmmc on 2011-01-06
just to install. after that no.

---

### Post by silameth on 2011-01-06
Thanks for all the help, I installed play on linux now it is just taking forever to update the app list. But I will let you know how it works when I get to try. 

Thanks again

---

### Post by lrgmmc on 2011-01-06
did it finish updating?

---

