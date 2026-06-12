---
title: "Problem with graphics, refuse to boot"
date: 2009-07-05
forum: General Help
---

### Post by NIghtstalker1993 on 2009-07-05
after swapping from an nVidia card to an ATi card, booted up ubuntu and it says it have problems with the graphics and wants to boot up in low-graphic mode and asks me what to do. i select reconfigure graphic settings(or something like that) and reboot. it rebooted succesfully. 

After that, I tried turning on Compiz and it refuses to. So i tried to update my graphics using the synaptics and downloaded the ATi stuff and removing the nvidia softwares. after it finished downloading, it crashed while in the midst of installing(pc unresponsive with caps and scroll lock light blinking).

I shut down the pc manually and after it booted up, It showed me a screwed up display and does nothing, not even the boot-up sound. only key it'll respond to is the power button where after clicking, it will show the shutdown screen and shutdown like normal.

Tried to boot into Live CD and pc crashes with the 2 blinking lights a short while after booting.

video of booting:
[http://www.youtube.com/watch?v=U2f7w28nJlU](http://www.youtube.com/watch?v=U2f7w28nJlU)

---

### Post by ivanvajar on 2009-07-05
There are some issues with ATI drivers right now. Go to Recovery mode and do repair of x server. See if that helps.

---

### Post by NIghtstalker1993 on 2009-07-05
sorry bro, i just started using ubuntu a week ago. mind explaining how to?

enter recovery mode by hitting esc before booting, but how to repair xserver?

thanks bro!

ps: the card is a Radeon 9600 on AGP8x

edit: before posting this, i tried selecting the last option in the list within recovery mode(x11 something, description says to repair graphic problems), and it did not work neither.

---

### Post by NIghtstalker1993 on 2009-07-05
Bump. Need help!

---

### Post by mhgsys on 2009-07-05
2 reset the X server to defaults, switch to console with Ctrl + Alt + f1 (f2,f3,f4,f5, etc)

```

sudo /etc/init.d/gdm stop

```

```

sudo dpkg-reconfigure xserver-xorg

```

```

sudo /etc/init.d/gdm start

```

---

### Post by NIghtstalker1993 on 2009-07-05
pc won't respond to any keyboard inputs after booting.

tried doing that in recovery mode under the root option.

did the first command, then the 2nd command and it says 'xserver-xorg' is not installed and no info is available or something like that.

if i typed the command without the sudo prefix, it launches a screen with a few options, and ends with the same error shown after i did the xfix command in recovery mode.

---

### Post by NIghtstalker1993 on 2009-07-05
Bump~

still having problems.

---

### Post by ivanvajar on 2009-07-05
Start recovery mode. At one point you will be asked to choose option. Then choose to try fixing x server

---

### Post by ivanvajar on 2009-07-05
Or start NETROOT mode and try > sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

---

### Post by NIghtstalker1993 on 2009-07-06
sudo dpkg-reconfigure xserver-xorg gives this.

[IMG]http://img.photobucket.com/albums/v655/Nightstalker1993/DSCN0797.jpg[/IMG]

same command, without the sudo prefix.
[IMG]http://img.photobucket.com/albums/v655/Nightstalker1993/DSCN0799.jpg[/IMG]

after choosing all the defaults for the keyboard and stuff.
[IMG]http://img.photobucket.com/albums/v655/Nightstalker1993/DSCN0801.jpg[/IMG]

sudo /etc/init.d/gdm start
[IMG]http://img.photobucket.com/albums/v655/Nightstalker1993/DSCN0802.jpg[/IMG]

pc running on dual boot with XP if anybody's wondering.

edit: whoops, first one typed 'xerver' instead of 'xserver', either way, still won't boot.

---

### Post by mhgsys on 2009-09-10
Could you post the output of 
```

 nano /etc/X11/xorg.conf 

```


wtf, topic last posting till mine was july?

---

