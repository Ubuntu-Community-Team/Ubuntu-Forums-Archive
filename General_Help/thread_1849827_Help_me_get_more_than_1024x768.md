---
title: "Help me get more than 1024x768"
date: 2011-09-25
forum: General Help
---

### Post by meior on 2011-09-25
[FONT=Verdana]Hello guys, I have google my *** off trying to find a way to make my screen go to the resolution of 1920x1200 which is what I have it on atm with windows.

I have this make monitor LG - W2452T and an nvidia GTX 260 graphics card.

Every tutorial I follow works for a little bit and then somewhere down the line it will say unknown location or folder or folder does not exsist

For example 
[/FONT]```
sudo apt-get install envyng-core envyng-qt 
```[FONT=Verdana]

[/FONT][FONT=Verdana]that works I type in my password but then guess what? The next part 
doesnt work, it says go to applications > system tools > envyng
but  dont have system tools there and I have manually searched for "envyng"
and I cant find it[/FONT].

I'm really giving up hope ive been using linux for just 1 day and already
im furiated by not being able to do one thing..... It's unusable
because everything is so freaking huge cos of he resolution.

There was also a command I cant remember for use but it was something 
like:

s```
udo gedit /etc/X11/xorg.conf
```

```
Then I type in this 

Section "Device"
	Identifier	"Configured Video Device"
Driver    	"vboxvideo"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
   Identifier    "Default Screen"
   Device    "VirtualBox graphics card"
   Monitor    "Configured Monitor"
DefaultDepth    24
   SubSection "Display"
         Depth     24
         Modes     "1024x768"
   EndSubSection
EndSection
```

when I click save it says unknown location or something....

How hard can it be to just install a driver...

---

### Post by Elfy on 2011-09-25
Envyng is no longer supported.

Did you try the driver available in Additional Drivers?

---

### Post by meior on 2011-09-25
Can you help to locate where this might be? I even followed this tutorial to the T

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=)

but ofcourse half way through when I have to add "nvidia" to the list it says unknown folders... im sure its something to do with ect/X11 I must be missing something even though ive downloaded and installed all the 225 updates :/

---

### Post by Elfy on 2011-09-25
You need to check first the dates of threads - it's not always the case that information current 2 or more years ago will be of use now :)

I assume you are using ubuntu 11.04 - hit the windows key - type additional - does an app appear in the dash ? IF it is there - select it and open it.

If you can't find it - open a terminal 

Ctrl+Alt+T - type

gksudo jockey-gtk

and enter, password will be needed


[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by meior on 2011-09-25
Thanks for that. I did it and it says no propierator drivers found

---

