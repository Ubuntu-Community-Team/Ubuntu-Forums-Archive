---
title: "The list of problems (help me please)"
date: 2006-01-26
forum: General Help
---

### Post by zapoqx on 2006-01-26
Ok, so after a while of figuring out a bunch of things, here is a list of my problems and maybe I'm not putting in the right search or I find the right search and it doesn't help me much...

First, I am not sure but I don't think Kubuntu had the Powernow! technology on my AMD Turion 64 laptop. So, I was following the instructions on one of the threads here but am stumped about the whole "Making the drivers from the source". I tried following the instructions as best as I could but have for the most part failed as I am stopped at a point.

Second, I think I installed the right drivers for my ati radeon Xpress 200M from ATI's website (from the notebook section of Linux Drivers). However, when my friend tried helping me test if the drivers were working well, he started something with gears in its name in the konsole and it starts fast for like 4 seconds then slows down to a crawl.

Third, I found the thread for repairing Grub and all as well as the instructions to get the clock on the linux side of the laptop to be on time instead of too fast. However, I think one of the times, I accedentally chose Recover mode on Kubuntu and I think it messed up the GRUB use because I find I can't keep that code (noapictimer irqpoll) staying in the line with kernel. Is something wrong with it and I need to reinstall Grub again or what?

4th, I decided to try playing the game Legends The Game on the Kubuntu side to see some of the better features and such compared to the XP side and I can't manage to get it to work. I double click the runlegends and nothing happens. What's going on here?

5th, my wireless is Broadcom and my friend showed me how to use ndiswrapper and got the driver working, but...
A: It doesn't start automatically (any help with this?)
B: I found a few forums about starting the wireless with the ssid, however, I can't access my home's wireless because I can't figure out how to setup to use the WPA-128 bit key that I have (I tried from some of the forums and it keeps telling me it doesn't recognize something).  Any help with that?

6th, is this too many questions I'm asking? I am as new as some of the people in the forums on linux in general :P

Thanks for any help you provide.

---

### Post by pelle.k on 2006-01-26
1. I have a Pentium M 470, at 1.73 Ghz, and powernow(d) is working as it should.
Use Kinfocenter in "System" menu to check if the processor is working at full speed or not. Most of the time mine is, but when i'm not doing much it's at 800 mhz.

2. I think you are refferring to the command "glxgears -printfps". Same here, Kinfocenter -> openGL. What does it say?

3. Don't know what that clock issue you are having is. Or are you talking about the clock being set to GMT instead of UMT or what the h*** it's called?
If you wan't to make grub boot with those line too, do "sudo nano /boot/grub/menu.lst" add the lines and then press control+x and press Y to save it.

4. Cant help you there... sorry.

5. Check "sudo nano /etc/modprobe.d/aliases" out. Is there a line such as "alias wlan0 ndiswrapper". make a search with control+w :)
I >>think<< there should be such a line.
Second, check with nano (sudo nano /etc/network/interfaces) if your card (wlan0 i suppose) is added.

Get back to us with some feedback :)
good luck...

---

### Post by zapoqx on 2006-01-26
Alright, thanks for the help... here is the responses:

1. It says it is an AMD Turion 64 Mobile Technology ML-34 and the cpu MHZ displays 1791.136.

2. Yes! That's it! Well here is what the FPS reports btw:
> 
1468 Frames in 5.1 seconds = 286.232 FPS
1552 Frames in 5.1 seconds = 302.020 FPS
1560 Frames in 5.1 seconds = 303.267 FPS
1560 Frames in 5.1 seconds = 303.129 FPS
That 1560 and on varies then from 5.1-5.2 seconds but the FPS stays around the same.
Here is what it says:
> 
Name of the Display     :0.0
  Indirect Rendering
     Driver
        Vendor         Mesa Project: [www.mesa3d.org](www.mesa3d.org)
        Renderer       Mesa GLX Indirect
        OpenGL Version    1.2 (1.5 Mesa 6.2.1)
        OpenGL extensions
        Implementation specific
  GLX
     server GLX vendor          SGI
     server GLX version         1.2
     server glx extensions
     client GLX vendor           ATI
     client GLX version           1.3
     client GLX Extensions
     GLX extensions
  GLU
     GLU version             1.3
     GLU extensions 

3. Ok, I did that.  It is workin it seems.

4. Ok, I hope someone else can help that at least.

5. There is no "alias wlan0 ndiswrapper" and there is no wlan0 in the interfaces section.

---

### Post by TheIdiotThatIsMe on 2006-01-26
Edit: Oops, didn't see your comment about WPA. Unfortunately, I dont know of any way to get WPA working, but the following works with WEP :rolleyes: 

For problem four, I had the same problem and opened the terminal and typed:

```
sudo nano /etc/modules
```
Add ndiswrapper at the end of the file
Then type:
```
sudo nano /etc/network/interfaces
```
And add an entry that looks similar to:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
```

And to start it automatically when Ubuntu starts, add **wlan0** to the **auto** line.

---

### Post by zapoqx on 2006-01-26
Ok, I understand that a bit, but are you saying add "ndiswrapper" or "ndiswrapper modprobe wlan0" code?

As for part 2, if I do that, does that mean that that is the default it will go to everytime cause I have to go to school with the laptop as well and the wireless (for now) at the school has no encription.

---

### Post by pelle.k on 2006-01-27
Your openGL is NOT from ati 3D driver, thus not working corrctly. MESA is the default built in. Do "sudo /etc/X11/xorg.config" and check "device" section for Driver - you should change this from "ati" to "fglrx" then restart you computer. (IF you have correctly installed your ati driver, else you will end up with a black screen intead of X)
*If you do, just remember this (easy peacy, japaneasy), control+alt+F1 or F2 -> F8 will bring you a command prompt. from there just, "sudo /etc/X11/xorg.config" again and change back to "ati".*

You really sholdn't download stuff then install it, like you usually do in windows, unless you know what you are doing. The best way are really:
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=firegl+ati](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=firegl+ati)

So you want to have two network configs sortof? again (easy peacy)

Make two scripts. which you can activate whenever you want to.
first "mkdir /home/YOURNAME/bin" (this folder is in something called your "path", which will make the scrips accessible from anywhere, just like all other commands)
"sudo nano /home/YOURNAME/bin/wlan-school"
```
#! /bin/sh
iwconfig wlan0 essid YOURESSID
iwconfig wlan0 channel YOURCHANNEL
ifconfig wlan0 up
dhclient wlan0
```

next script

"sudo nano /home/YOURNAME/bin/wlan-home"
```
#! /bin/sh
iwconfig wlan0 essid YOURESSID
iwconfig wlan0 channel YOURCHANNEL
iwconfig wlan0 key restricted s:ASCIKEYASCIKEY
ifconfig wlan0 up
dhclient wlan0
```

make them executable "sudo chmod +x /home/YOURNAME/bin/wlan-*" (star means everything, if you didn't know that already)

Last of all. remove it from the auto line in /etc/network/interfaces (that way it doesn't boot up with a network config wich maybe doen't work, and stalls the bootup procedure)

Now try them out. just "sudo wlan-home" and see if it works :)

[edit]he meant add the word "ndiswrapper" only, to /etc/modules[/edit]

---

### Post by zapoqx on 2006-01-29
Sorry for not following up yet.
I can't do that yet because my laptop is for the most part out of commission (it decided that either the system board is bad or the internal power conversion decided to go out... either way, it ain't gonna stay on longer than 2 minutes at best... 2 seconds in any other scenario).

---

