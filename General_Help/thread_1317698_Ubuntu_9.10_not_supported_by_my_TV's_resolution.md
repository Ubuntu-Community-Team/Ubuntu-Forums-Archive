---
title: "Ubuntu 9.10 not supported by my TV's resolution?"
date: 2009-11-06
forum: General Help
---

### Post by cshell_1987 on 2009-11-06
Here is my situation. I have an 8800GT graphics card. I have it connected to my Insignia 32' LCD TV via VGA cable (DVI-to-VGA adapter on graphics card). I did have a dual boot of 8.04 that worked just fine. I went to install 9.10 and after I selcted the install option on the live cd, my TV says resolution not supported. I took my PC to my old CRT monitor and finished the install process of 9.10. I dropped the resolution to 1024 x 768, 800 x 600, and 640 x 480 with a refresh rate of 60. I plugged the machine back into my tv. I get the nice new white glowing ubuntu icon and then resolution not supported. 

My TV's manual says that the following VGA inputs are supported:

640x480/60 Hz, 800x600/60Hz, 1024x768/60Hz, 1920x1080/60 Hz

I'm strongly considering getting something like an HD4850 so I can just run an HDMI cable. Hopefully compiz fusion runs well with the drivers for the card. I have heard stories about ATI drivers and ubuntu though.

In any case, I can't get my display to work with ubuntu, I can't afford a new tv or graphics card right now so I would appreciate your help in this matter. 

Please bear with me as I am a novice in Linux and I know only the most basic commands (I am still a GUI baby) Although I did have a couple of classes of Fedora Core 5 in college. I had the oppurtunity to play with the vi editor, set up an apache web server, as well as play with rpm commands, chmod permissions etc...but it's been a while since I've done all that stuff. Please be detailed in your instructions. Once again, I greatly appreciate your help.

Thanks.

---

### Post by cshell_1987 on 2009-11-07
No solutions?

---

### Post by cshell_1987 on 2009-11-08
Please help!

---

### Post by AW36 on 2009-11-08
perhaps plug both the crt and the tv in at once, do whatever you have to do, disable the crt and voila.

---

### Post by MountainX on 2009-11-08
Did you have any proprietary drivers under 8.04 with your working configuration? Maybe you need to install video drivers for 9.10?

---

### Post by hossdozero on 2009-11-08
first, backup your xorg.conf file. run

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

With your crt monitor hooked up go to 

system > preferences > NVIDIA x server settings

and click on the "X Server Display Configuration" tab 

Adjust your resolution to one of your televisions supported resolutions and click apply. Then click "save to x configuration file" 

When the window pos up click "show preview". copy and paste the text to a file on your desktop called "xorg.conf" (we do this because by default the NVIDIA utility doesn't have permission to modify the xorg.conf file at /etc/X11/xorg.conf) now you can reset your resolution to be more legible on your crt monitor if you wish.

next run 
```
sudo cp /home/yourname/Desktop/xorg.conf /etc/X11/xorg.conf
```

this should start your display in a resolution supported by your television. 

NOTE:

If this does not work you can reset your xorg.conf file by switching to one of your 6 available tty terminals (ctrl+alt+F1-F6) and running 

```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

hope this works out for you.

---

### Post by MountainX on 2009-11-08
9.10 doesn't use Xorg.conf for video card settings, right?

---

### Post by AW36 on 2009-11-08
wrong. also, i believe sudo nvidia-settings also lets you edit xorg.conf. less work that way

---

### Post by hossdozero on 2009-11-09
> **AW36 said:**
> wrong. also, i believe sudo nvidia-settings also lets you edit xorg.conf. less work that way


This.

It is a leap beyond the days of old, when you had to figure out how to configure the xorg.conf file manually. I still have the scars from bashing my head against the keyboard.

---

