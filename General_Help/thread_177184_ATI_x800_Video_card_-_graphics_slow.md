---
title: "ATI x800 Video card - graphics slow"
date: 2006-05-15
forum: General Help
---

### Post by chadk on 2006-05-15
I've installed Automatix (which rocks) and then I used Synaptic to install the ATI x800 drivers but when I go to shell and type fglrxinfo I get this:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I have libgl1-mesa-dri version : 6.3.2-Oubuntu6breezy1 installed.

here's my xorg.conf (except the font part):
```

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 SE (R420 JJ)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       32-80
        VertRefresh     50-75
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon X800 SE (R420 JJ)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $  
(obviously I'm not very good at this yet so ignore the $ and the lack of a line break on these subsections
I simply don't know how to copy and paste the whole file so I used nano and copied bits and pieces)
      EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1600x1200" "1280x1024" "1280x960" $        EndSubSection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by empthollow on 2006-05-15
it looks like xorg is still using the "ati" driver. for accelerated graphics the driver needs to be "fglrx".  the best way to do this is to use aticonfig:

sudo aticonfig --initial

and then reboot
this should automatically edit your xorg.conf to use accelerated graphics

p.s. the kernel module needs to be installed as well, ubuntu did this automatically for me though :)

good luck

---

### Post by chadk on 2006-05-16
Hmm ok, I'll try that but last time I did it I had to reinstall ubuntu because all I got when trying to switch users was a black screen. - I could log in the first time fine, I just had to reboot the entire machine every time I wanted another user logged in.  Maybe I'll just buy an nvidia card.

---

### Post by ZiLOG_Z80 on 2006-05-16
Ive not used automatix but after installing the official ati driver you need to change from the ati driver included with ubuntu to the fglrx driver. In order to change drivers use ```
sudo dpkg-reconfigure xserver-xorg
``` this lets you change driver and set up your monitor, then use ```
sudo aticonfig --initial
```
also with my ati card i found that totem wouldnt work unless is used```
sudo aticonfig --overlay-type=Xv
```

---

### Post by chadk on 2006-05-17
grrr
```

chad@figment:~$ sudo aticonfig --initial
sudo: aticonfig: command not found

```

---

### Post by seth0x2b on 2006-05-17
This is the step by step I followed and I set up my card with no problem( in Hoary, in Breezy it's slow but at least it's not Mesa :-D  )
[http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue)


Cheers

---

### Post by mjziegle on 2006-05-17
In /etc/xorg.conf change 

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 SE (R420 JJ)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

to

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 SE (R420 JJ)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

then restart X

/etc/init.d/gdm restart

then test with 

fglrxinfo

Don't waste your time with dkpg-reconfigure or complicated howto's

-matt

---

### Post by chadk on 2006-05-17
Thanks Matt but when I do that I get "No Video Signal" from my monitor... perhaps it's my cheap flat panel LCD?  It's a Sceptre X9G Naga V.

---

### Post by chadk on 2006-05-17
Still nope. :(

---

### Post by jadacyrus on 2006-05-17
Just FYI, Don't use Automatix, use [EasyUbuntu]("http://easyubuntu.freecontrib.org/") .. It's much safer.

---

### Post by mjziegle on 2006-05-18
No video signal is a head scratcher.  Does the splash screen show up on boot?  Do you see the bios?  There shouldn't be any reason for the video signal to turn off.  So if you see the bios or the splash you're in good shape.

Likely what is happening is that your xserver is set to a resolution higher than what your LCD can display.   Therefore what you will need to do is find out the max resolution of your LCD or the native resolution.

Then boot into the recovery mode so you get to the prompt.  Then run dpkg-reconfigure xserver-xorg and make sure you choose the maximum resolution that corresponds to your LCD.  Uncomment all the wierd ones that are too high or your LCD isn't likely to support.  Check the manual.  Also the refresh rate may be a problem.  Most LCDs have a vertical refresh of 60Hz (75Hz tops).  So set that as well.  The ranges that are in xorg.conf can cause problems.

Good luck,

Matt

[QUOTE=chadk]Thanks Matt but when I do that I get "No Video Signal" from my monitor... perhaps it's my cheap flat panel LCD?  It's a Sceptre X9G Naga V.[/QUOTE]

[QUOTE=punkybouy]Do you have a firewall installed?  I am using Firestarter and found it was blocking the incoming traffic from my Windows box both XP Professional and XP Home.  Also I can't see my Share in Windows Networking but I can map a drive to it.  I found when mapping a drive the only way I could connect was to click the button "connect as a different user" and log in with my unix name and password even though its the same as my Windows name and password.  I have a UNIX to Windows user map but that did not help.[/QUOTE]

---

### Post by ZiLOG_Z80 on 2006-05-18
try downloading and installing the driver form the ati site, see if you have any better luck with that

---

### Post by empthollow on 2006-05-18
i got a black screen using "aticonfig --initial" as well. i fixed it by adding 2 lines to the monitor section, make sure it is the monitor section referenced by the server layout section.

HorizSync	28.0 - 64.0
VertRefresh	43.0 - 60.0

---

### Post by mjziegle on 2006-05-18
It's the exact same driver as in the repositories ...

[QUOTE=ZiLOG_Z80]try downloading and installing the driver form the ati site, see if you have any better luck with that[/QUOTE]

---

### Post by mjziegle on 2006-05-18
Agreed with the refresh rates.  Also you may want to delete all resolutions above 1024x768 until you get something.  You can then tweak later.

[QUOTE=empthollow]i got a black screen using "aticonfig --initial" as well. i fixed it by adding 2 lines to the monitor section, make sure it is the monitor section referenced by the server layout section.

HorizSync	28.0 - 64.0
VertRefresh	43.0 - 60.0[/QUOTE]

---

### Post by ZiLOG_Z80 on 2006-05-18
[QUOTE=mjziegle]It's the exact same driver as in the repositories ...[/QUOTE]
Are you using the one from synaptic? cus chadk says he is and he doesnt have the aticonfig comand. any ideas?

According to the wiki they are different [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")

---

### Post by chadk on 2006-05-18
I deleted all the refresh rates above 1024.  I modified the horiz and vert sync rates based on the stats supplied with my monitor (looked them up on newegg).  I give up on the ati card.  My wife needs a new card anyway so she can have mine and I'll get a new one ;)

---

### Post by empthollow on 2006-05-18
i was missing the aticonfig command until i installed the driver from synaptic

```
sudo apt-get -y install xorg-driver-fglrx
```

if you've done this and you still don't have the command, check your /etc/apt/sources.list file to make sure you have the proper repositories.
you can find some good repositories here [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by mjziegle on 2006-05-18
[QUOTE=ZiLOG_Z80]Are you using the one from synaptic? cus chadk says he is and he doesnt have the aticonfig comand. any ideas?

According to the wiki they are different [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")[/QUOTE]

There's no evidence to support your point.  ATI provides a binary package.  The repositories provide a binary package.  It's the same binary.  ATI doesn't provide any source code so there isn't any opportunity to admit changes.  These are two installation methods NOT two different drivers.

do a which aticonfig

Matt

---

### Post by graigsmith on 2006-05-19
"because all I got when trying to switch users was a black screen."

thats because ati's driver crashes when you try to switch users, it's a known bug in ati's drivers..  all you can do is wait till they fix the bug, or try nvidia.  i have an x800 too, and it's a pretty serious and annoying bug.  

i use my ati 9200 because it has open source drivers with opensource 3d drivers.. unfortunately you cant get open source drivers for the x800.

edit, since you are considering a new card. get nvidia, ati has serious driver problems.  at least untill they fix that bug where switching users crashes the computer.  whenever they fix it, im gonna plug my x800 back in. till then, im just gonna wait,  or possibly try to sell my x800. not sure yet.

---

### Post by ZiLOG_Z80 on 2006-05-19
[QUOTE=mjziegle]There's no evidence to support your point.  ATI provides a binary package.  The repositories provide a binary package.  It's the same binary.  ATI doesn't provide any source code so there isn't any opportunity to admit changes.  These are two installation methods NOT two different drivers.

do a which aticonfig

Matt[/QUOTE]

I have had to do a fresh install of ubuntu so i decided to try out the ubuntu provided driver and ati's to see if there was any difference in performance using ```
glxgears -printfps
``` and ```
fgl_glxgears
```

With the ubuntu repositories driver i got 1860 fps for glxgears and 413 fps for fgl_glxgears

With the ati driver glxgears gives 2634 fps and fgl_glxgears 624 fps

---

### Post by mjziegle on 2006-05-19
This might be valid if glxgears was actually a benchmark ...

Try a 3D game.

---

### Post by chadk on 2006-05-19
Thanks for the help gang.  I didn't know it was a known bug.  I've been beating myself up for not being able to figure it out. :)  I USUALLY run nvidia but I thought, hell I'd heard good things about ATI lately so I'd try one.  It's fine on doze but I still prefer my nvidia.

---

### Post by ZiLOG_Z80 on 2006-05-20
[QUOTE=mjziegle]This might be valid if glxgears was actually a benchmark ...

Try a 3D game.[/QUOTE]

Have done and performance with ati's driver is better on my machine. I'm not gonna argue with you, its pointless you think what you want. You say I cant prove they're different but just the same you cant prove theyre the same. Lets just leave it

---

