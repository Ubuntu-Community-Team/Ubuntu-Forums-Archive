---
title: "Having problems with screen resolution"
date: 2009-09-16
forum: General Help
---

### Post by DemonsBeDriven on 2009-09-16
Ok. I just downloaded Ubuntu and am using it for the first time ever. Now here is the problem. My screen resolution is wayyyy too big. It will not go any smaller that 800x600. It looks just awful on this screen. if there is a way to fix this I would sure appreciate your help

---

### Post by ram2500 on 2009-09-16
By way too big, do you mean that 800 x 600 is too big or too small (as in the size of the print)?

Go to System > Preferences > Screen Resolution and try that.

---

### Post by DemonsBeDriven on 2009-09-16
The writing with 800x600 is huge. And I went to system>display and I can't make it any smaller that way.

---

### Post by ram2500 on 2009-09-16
I think either your video card or your monitor's driver is incorrect or improperly recognized. There's no such thing as a newer 800 x 600 monitor, at least that I know of, so I am guessing you don't have an older monitor/video card. It's likely a driver problem. Have you ran any other OS on this computer at higher resolutions?

---

### Post by duanedesign on 2009-09-16
Lets find out a little more about whats going on.

What release are you running? Jaunty? Hardy? Karmic?

What is your graphics card? Open up a Terminal Applications > Accesories > Terminal and type (or copy and paste) the following command.

```
sudo lspci -v | grep VGA
```

 Post the output.

* If the above command does not return anything, just use lspci -v this will produce a fairly long list. Go through the list and find the one that pertains to your video card and post it. If you do not know which is your card you can put the entire output in a text file and include it as an attachment to your post.

Lets check what modes are available. Again in the Terminal issue the folowing command and post the output.

```
xrandr
```

---

### Post by DemonsBeDriven on 2009-09-16
Yes I had windows xp on this computer before. And had no problem what so ever. But my hd crashed and I lost my xp disk so I switched over to this and figured I would give it a try.

I also had no idea what release this is. I just downloaded it. When I typed that into the command prompt I got this




VGA compatible controller: nVidia Corporation C51[Gforce 6150 LE] (rev a2)

---

### Post by duanedesign on 2009-09-17
Your graphics card requires the nvidia-glx-180-85. Lets make sure it is installed by running in Terminal.

```
dpkg -l | grep nvidia-glx
```

you should get something like the following.

```

ii  nvidia-glx-180              180.18.14-0ubuntu1 
NVIDIA binary Xorg driver

```

if you do not see it run:

```
sudo apt-get install nvidia-glx-180 nvidia-glx-180-dev nvidia-180-modaliases
```
```
nvidia-xconfig
```

Restart and see if your resoloution choices improve.

If you already have that driver and/or it failed to improve the resoloution lets go on and check your xorg.conf for [COLOR="Blue"]HorizSync[/COLOR] and [COLOR="Blue"]VertRefresh[/COLOR] values. This can lead to your monitor having only one resolution that is lower than your card and monitor support.

```
sudo gedit /etc/X11/xorg.conf
```

you are looking for something like.

```
Section "Monitor"
        Identifier   "Monitor1"
        [COLOR="Blue"]HorizSync[/COLOR]    28.0 - 80.0
        [COLOR="Blue"]VertRefresh[/COLOR]  48.0 - 75.0
EndSection

```

If you have[COLOR="Blue"] HorizSync[/COLOR] and [COLOR="Blue"]VertRefresh[/COLOR] values comment them out and save the file.
```
Section "Monitor"
        Identifier   "Monitor1"
        [COLOR="Red"]#[/COLOR][COLOR="Blue"]HorizSync[/COLOR]    28.0 - 80.0
        [COLOR="Red"]#[/COLOR][COLOR="Blue"]VertRefresh[/COLOR]  48.0 - 75.0
EndSection

```

If after restarting your still stuck in 640 x 480 go ahead and remove the comment marks [COLOR="Red"]#[/COLOR] in your xorg.conf. Now lets take a look at your xorg.log. Run the following in Terminal.

```
cat Xorg.0.log > xorg.log.txt
```

This will create a text file in your Home directory (That would be the folder with your name) named xorg.log.txt. If you could attach that text file to a post I would be more than happy to take a look at it for you.

Dh

---

### Post by DemonsBeDriven on 2009-09-19
Thanks for all of your help. I come to find out that it was the computer itself. The motherboard was going out on it. I installed Ubuntu on a different computer and now have none of the problems I was having. Once again thanks for your help

---

