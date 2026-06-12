---
title: "Change Resolution / Driver Issue"
date: 2011-12-22
forum: General Help
---

### Post by deathrune on 2011-12-22
Hi, I am new to Linux.

I've just installed 
Ubuntu on to my older machine, It has an Nvidia GeForce 9600.

The problem is it doesnt let me change the resolution to higher than 1024x768. I want it on 1280x800.

I've tried using many terminal commands I've found and all of them seam to come up with an error.

I am using the driver "Nvidia accelerated graphics driver (version current) [reccomended].

There is another one and drivers with post release updates.

I got minecraft running before but it was quite low fps, hold on i'll look now, yes so its running minecraft at 5-15
where as on windows xp it was definitively higher fps, no lag whats so ever, it does have a goodish graphics card.

So can someone help me here, I would really appreciate it, someone tell me easy steps to add the resolution or sort out these drivers.

thanks

---

### Post by Basher101 on 2011-12-22
do you have all the other necessary packages? If you use 11.10 Synaptic Package Manager is not installed by default...so you would have to look it up with the software centre and install it. Next open it up and type in the search box "nvidia". All installed packages have a green square to the left. Now scroll down and see if the following packages are installed: nvidia-common | nvidia-settings | nvidia-current 

if one of those is missing you can right click them, then mark them for install and click apply.

---

### Post by deathrune on 2011-12-22
> **Basher101 said:**
> do you have all the other necessary packages? If you use 11.10 Synaptic Package Manager is not installed by default...so you would have to look it up with the software centre and install it. Next open it up and type in the search box "nvidia". All installed packages have a green square to the left. Now scroll down and see if the following packages are installed: nvidia-common | nvidia-settings | nvidia-current 

if one of those is missing you can right click them, then mark them for install and click apply.

alright, thanks. I will do as you said and report back from there

---

### Post by deathrune on 2011-12-22
ok, I have all of those packages installed
did already have those

---

### Post by james2b on 2011-12-22
That item called; "nvidia-settings" is the graphical display tool to change your video display configuration settings. It should be on the programs menu under system or other, etc. The main file that has screen resolution and others is here; /etc/X11/xorg.conf , here is my thread which concerns the nvidia driver and full 3D functions; [http://ubuntuforums.org/showthread.php?t=1894110](http://ubuntuforums.org/showthread.php?t=1894110)

---

### Post by deathrune on 2011-12-22
> **james2b said:**
> That item called; "nvidia-settings" is the graphical display tool to change your video display configuration settings. It should be on the programs menu under system or other, etc. The main file that has screen resolution and others is here; /etc/X11/xorg.conf , here is my thread which concerns the nvidia driver and full 3D functions; [http://ubuntuforums.org/showthread.php?t=1894110](http://ubuntuforums.org/showthread.php?t=1894110)

ahh, so I changed the resolution using the nbvidia-settings instead of the system settings. Thanks

All good now, I'm guessing the lag in minecraft was because it was java, downloading css through steam on wine right now

---

### Post by wildmanne39 on 2011-12-22
Hi, if you continue to have lag you can look at this link it might help.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

---

### Post by deathrune on 2011-12-22
the computer is incredibly slow now, im only downloading css through steam.

Iv'e tried changing the res through nvidia-settings, it does nothing but it did add the new resolutions to the display settings, but it wont let me change

---

### Post by deathrune on 2011-12-22
wildmanne39 i tried the compiz thing it didnt really help, I'm getting general video lag, move a window it will lag, its not smooth, the video card is more than capable at doing these things.

I'm thinking of changing back to windows or another distro because all iv'e had is trouble

These drivers arnt working for this card.

Hold on css has finished downloading

---

### Post by wildmanne39 on 2011-12-22
Hi, I thought you got that part fixed according to your last post. Here is a couple of links to help with that it sounds like you are going to have to manually set resolution but that is not something I have a lot of experience with, that is why I am only providing the links.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Each link has a different method to fix your issue.

Did you open display settings in ubuntu and try to change the resolution there?

Did you change the settings according in the link in my last post for the slowness?
Thanks

---

### Post by wildmanne39 on 2011-12-22
Hi, are you running in unity or ubuntu classic?

Also I had to use the older nvidia driver and not the recommended one for my card so you might try a different driver but if you do open software center make sure only one is installed at a time or they will conflict.
Thanks

---

### Post by deathrune on 2011-12-23
I am greatful for your links but I don;t like this gnome 3 thing

It is big and clunky, I hate the side bar, I know I'm not used to it but I hate it, I despise it.

So I'm giving up on it.

It gives me a head ache, and I hate this stupid resolution business, its so slow, very slow.

I'm chaning to Mint 11. Realizing Mint uses gnome 3 as well I feal like and idiot even to complain about this, also I see enable 3d acceleration around, this could be a problem?

I meant KDE distros like kubuntu or opensuse

---

### Post by deathrune on 2011-12-23
> **wildmanne39 said:**
> Hi, are you running in unity or ubuntu classic?

Also I had to use the older nvidia driver and not the recommended one for my card so you might try a different driver but if you do open software center make sure only one is installed at a time or they will conflict.
Thanks

Ubuntu 11.10

These are my specs btw:

3ghz Single Core
2gb Ram

---

### Post by deathrune on 2011-12-23
> **wildmanne39 said:**
> Hi, I thought you got that part fixed according to your last post. Here is a couple of links to help with that it sounds like you are going to have to manually set resolution but that is not something I have a lot of experience with, that is why I am only providing the links.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Each link has a different method to fix your issue.

Did you open display settings in ubuntu and try to change the resolution there?

Did you change the settings according in the link in my last post for the slowness?
Thanks

Yes I've tried it through terminal it keeps giving me a new error each time, something to do with no gamma setting anf another about no vga-1 recognized /ignoring this error

---

### Post by wildmanne39 on 2011-12-23
Hi, go way down the page of the first link that I gave you until you see > Setting resolution changes in xorg.conf
then you should be able to set resolution it is easier then the first method you tried.
Thanks

---

### Post by deathrune on 2011-12-24
> **wildmanne39 said:**
> Hi, go way down the page of the first link that I gave you until you see 
then you should be able to set resolution it is easier then the first method you tried.
Thanks

this is the error: 

xrandr --output LVDS --mode 1024x768
xrandr: Failed to get size of gamma for output default
warning: output LVDS not found; ignoring


linux@linux-AcerPower-F6:~$ xrandr --newmode &#8220;1024x768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
linux@linux-AcerPower-F6:~$ 

What is this gamma thing? I doubt it is my monitor, driver problem?

---

### Post by wildmanne39 on 2011-12-24
Hi, I am not talking about setting it through xrandr scroll down until you see this example> Setting resolution changes in xorg.conf

While xorg.conf is largely empty these days, it can still be used for setting up resolutions. For example:

Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"
EndSection
Section "Device"
    Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    Driver          "ati"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection
You just need to change  the resolution in the xorg file.
thanks

---

### Post by deathrune on 2011-12-24
> **wildmanne39 said:**
> Hi, I am not talking about setting it through xrandr scroll down until you see this example
You just need to change  the resolution in the xorg file.
thanks

I just read this in another thread, but you see, how do I edit the xorg file? where is it located?

Or is it through the terminal, please tell me step to step.

thanks you =)

---

### Post by deathrune on 2011-12-24
bump :S

---

### Post by james2b on 2011-12-24
In a terminal type this; sudo gedit /etc/X11/xorg.conf , then give your password, hit enter, make the changes, and save it, exit.

---

### Post by deathrune on 2011-12-24
> **james2b said:**
> In a terminal type this; sudo gedit /etc/X11/xorg.conf , then give your password, hit enter, make the changes, and save it, exit.

oh right thanks, 


gedit /etc/X11/xorg.conf
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit

---

### Post by deathrune on 2011-12-24
oh gedit is a package nvm

---

### Post by deathrune on 2011-12-24
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

error after error after error

---

### Post by deathrune on 2011-12-24
I dont want to sound like im complaining and moaning but this is very annoying.

Something so simple is so hard. I am new to Linux I only installed it yesterday.

I do want to get good at Linux, and soon use more advanced and harder distros but before that I need to learn to do these simple but hard things.

Obviously I need to make the xorg.config file changable or remove the read only rights or something through the terminal, such a command I don't know how.

I googleing it and I always get something that is irrelviant or outdated

---

### Post by wildmanne39 on 2011-12-24
Hi, please copy and paste this command:
```
gksudo gedit /etc/X11/xorg.conf
```
it will ask you for your user password type your password it will open a file that is blank then use the link I gave you to create what you need.

I am not experienced at this part so I can not advise you on creating it, I believe the link gives you a link to a complete guide for doing so though.

I am going to be on very little until Monday I have family in town for Christmas.
Thanks

---

