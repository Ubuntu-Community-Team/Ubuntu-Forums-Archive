---
title: "1280x1024 resolution not seen"
date: 2012-02-12
forum: General Help
---

### Post by sumithar on 2012-02-12
I have installed 11.10 on a brand new PC with a Zotac GE Force 210 graphics card.
This PC also has Windows installed and when booting that up my resolution is set to 1280x1024.

But when I boot up in Ubuntu I don't see that resolution when I go into System Settings->Displays, only 1024x768.

I went to zotac web site and downloaded the Linux Display Driver x64 AMD64 (since this is a PC with an AMD 64 processor) but I don't know what to do with this .run file
NVIDIA-Linux-x86_64-290.10.run

Any suggestions would be very welcome...

---

### Post by TeoBigusGeekus on 2012-02-12
Open a terminal, navigate to the location of the file and give
```
sudo ./NVIDIA-Linux-x86_64-290.10.run
```

---

### Post by sumithar on 2012-02-12
> **TeoBigusGeekus said:**
> Open a terminal, navigate to the location of the file and give
```
sudo ./NVIDIA-Linux-x86_64-290.10.run
```
THanks.  I did this.  I had to go to ctrl alt f1 to stop the xserver which I did using the lightdm stop command.
THen I installed the driver and it seemed to go thru fine.

But now when I boot up I get a blank screen.
i went back to ctrl alt f1 and did 
sudo service lightdm start
but no luck

(I fortunately have another functional PC, so I can post back to this discussion!)

Rgds

---

### Post by RedRat on 2012-02-12
Are you running 11.10 32 bit or 64bit. Driver must match the OS version.

---

### Post by sumithar on 2012-02-12
> **RedRat said:**
> Are you running 11.10 32 bit or 64bit. Driver must match the OS version.
I downloaded ubuntu-11.10-desktop-amd64.iso and burnt it to CD to use for the install.  So I'm pretty sure it's the 64bit OS.

---

### Post by efflandt on 2012-02-13
You should have just installed the nvidia driver using **Additional Drivers** within Ubuntu.  That would get you the proper driver that updates automatically with kernel updates. If you install the drivers using a non-Ubuntu script, you may need to redo that after any kernel update.

However, for nouveau and nvidia drivers to cooperate, you need to use **nomodeset** kernel boot parameter so they are modules instead of using kernel modesetting (kms). You can test that by hitting **e** during grub menu and adding or inserting it in options of linux line.  Then you can make it stick by editing following line like this in /etc/default/grub (using **sudo nano** or **gksu gedit**)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Then run **sudo update-grub**

---

### Post by RedRat on 2012-02-13
Have you tried just using the open source NVidia driver that comes with Ubuntu and NOT the one from NVidia? Granted, you may not be able to run all the bells and whistles such as compiz and the rotating cube, but when first installed, did you get the correct resolution?

---

### Post by sumithar on 2012-02-13
> **efflandt said:**
> You should have just installed the nvidia driver using **Additional Drivers** within Ubuntu.  That would get you the proper driver that updates automatically with kernel updates. If you install the drivers using a non-Ubuntu script, you may need to redo that after any kernel update.

However, for nouveau and nvidia drivers to cooperate, you need to use **nomodeset** kernel boot parameter so they are modules instead of using kernel modesetting (kms). You can test that by hitting **e** during grub menu and adding or inserting it in options of linux line.  Then you can make it stick by editing following line like this in /etc/default/grub (using **sudo nano** or **gksu gedit**)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Then run **sudo update-grub**

Hi, thanks for replying...
I did try to use Additional Drivers 1st before I went to the Zotac website. It showed that I was using some kind of nVidia drivers but there was no option to install additional driver.

I tried both the options you said
a) added nomodeset to the linux line after hitting 'e' when booting up and showing grub menu.  It didn't seem to do anything except that on the black screen it showed [OK] on the top left corner.
b) I then hit Ctrl-Alt-F1 and from command prompt edited the grub file like you recommended.
I saved and did the sudo update-grub.

Then I rebooted (sudo shutdown -r now)...
I chose the first Ubuntu option in grub and it went thru the motions and is still displaying a black screen 

Rgds

---

### Post by sumithar on 2012-02-13
> **RedRat said:**
> Have you tried just using the open source NVidia driver that comes with Ubuntu and NOT the one from NVidia? Granted, you may not be able to run all the bells and whistles such as compiz and the rotating cube, but when first installed, did you get the correct resolution?

Yes...That's what wasn't giving me the 1280x1024 option.

What's frustrating is that this same monitor is used with an older PC running 11.04 and connected to its motherboard VGA port.  I can display 1280 x 1024, no problems.

---

### Post by HiImTye on 2012-02-13
every time I have used the nVidia installs to install drivers it has messed up my installation to the point where I figured that less work is reinstalling. I use a ppa instead as it has always worked for me
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by HiImTye on 2012-02-13
you should be using the 'nVidia X Server Settings' tool not the 'display' one. maybe that will yield better results

---

### Post by RedRat on 2012-02-13
If you boot from the LiveCD, what resolution are you getting? Is it 1280x1024 or is it the 1280x768? Usually Ubuntu detects the max resolution of the monitor and video card and goes with that.

---

### Post by sumithar on 2012-02-13
> **HiImTye said:**
> you should be using the 'nVidia X Server Settings' tool not the 'display' one. maybe that will yield better results

I'll be happy to try if you can tell me how to do this from a command prompt

---

### Post by RedRat on 2012-02-13
> **sumithar said:**
> I'll be happy to try if you can tell me how to do this from a command prompt
I believe it is:
```
gksudo nvidia-settings
```

It is important that you run it under sudo or gksudo.

---

### Post by sumithar on 2012-02-13
> **RedRat said:**
> If you boot from the LiveCD, what resolution are you getting? Is it 1280x1024 or is it the 1280x768? Usually Ubuntu detects the max resolution of the monitor and video card and goes with that.

Just tried that- it booted up into 1024x768 but when I went into System Settings, Display, it gave the option to change to 1280 x 1024 which I did.

When I clicked on additional drivers, it said no proprietary drivers are installed.

---

### Post by sumithar on 2012-02-13
> **RedRat said:**
> I believe it is:
```
gksudo nvidia-settings
```

It is important that you run it under sudo or gksudo.

Well, I have to use sudo since I don't have a desktop.

I tried that and am bewildered by all the options it has. What exactly should I be doing- the help screen is 3 pages long?

---

### Post by HiImTye on 2012-02-13
> **RedRat said:**
> I believe it is:
```
gksudo nvidia-settings
```It is important that you run it under sudo or gksudo.
you dont need to use sudo, it actually asks to elevate permissions in recent distros

edit: nevermind, it actually doesn't but you should use gksudo, rather than sudo

to change resolutions, go to X Server Display Configuration

---

### Post by sumithar on 2012-02-13
> **HiImTye said:**
> you dont need to use sudo, it actually asks to elevate permissions in recent distros

edit: nevermind, it actually doesn't but you should use gksudo, rather than sudo

to change resolutions, go to X Server Display Configuration

I don't have a desktop, gksudo is ruled out, isn't it?  I get "cannot open display" message

How do I go to X Server Display Configuration?

---

### Post by RedRat on 2012-02-13
> **sumithar said:**
> Just tried that- it booted up into 1024x768 but when I went into System Settings, Display, it gave the option to change to 1280 x 1024 which I did.

When I clicked on additional drivers, it said no proprietary drivers are installed.

That indicates that the driver shipped with your installation must be able to handle the 1280x1024. Does it give you 1280x1024?  The reason for that message is that you are booting off the LiveCD and there are no proprietary drivers on that disk. If you want that resolution you might just use the driver shipped with your version. You may not have all the bells and whistles of the proprietary driver, but at least you will have your resolution. 

I tend to go with functional and not worry to much about using the nVidia drivers, but then I do not really game and really have gotten over the rotating cube. 

If your installation is bollixed, you might just try wiping out the old installation and just start from scratch. For the time being forget about the proprietary driver from nVidia and go with the open source driver.

---

### Post by HiImTye on 2012-02-13
> **sumithar said:**
> I don't have a desktop, gksudo is ruled out, isn't it?  I get "cannot open display" message

How do I go to X Server Display Configuration?
I got you, this thread is kind of all over the place. I would try:
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```hopefully that will give you a usable desktop

---

### Post by sumithar on 2012-02-14
> **HiImTye said:**
> every time I have used the nVidia installs to install drivers it has messed up my installation to the point where I figured that less work is reinstalling. I use a ppa instead as it has always worked for me
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

No idea what all of this does, but I followed the instructions blindly and I have  a working desktop.  Thank you very much.

Now, I still need to figure out how to get the 1280x1024 resolution.
I did the additional drivers thing and this is what that looks like (see attachment)

But the display settings still doesn't show 1280x1024.  See attachment.

Any thoughts?

THanks!

---

### Post by TeoBigusGeekus on 2012-02-15
Open a terminal and give
```
gksu nvidia-settings
```
Do all your tweaking from there; once finished, don't forget to press the "Save to X configuration file" button.

---

### Post by RedRat on 2012-02-15
I would have selected the recommended driver in that list shown in your first picture instead of the second one. I remember way back a couple of years ago running into trouble selecting that second one, but my memory fails me as to what happened.

I am wondering if you are selecting the correct monitor here. The settings are dependent on the card you have but also the monitor. Perhaps you have entered a monitor model that the data says doesn't support that 1024 resolution. Perhaps your monitor data is outdated or you have the selected the wrong monitor. 

Definitely try the nvidia-settings as recommended above first and foremost.

---

### Post by sumithar on 2012-02-15
> **RedRat said:**
> I would have selected the recommended driver in that list shown in your first picture instead of the second one. I remember way back a couple of years ago running into trouble selecting that second one, but my memory fails me as to what happened.

I am wondering if you are selecting the correct monitor here. The settings are dependent on the card you have but also the monitor. Perhaps you have entered a monitor model that the data says doesn't support that 1024 resolution. Perhaps your monitor data is outdated or you have the selected the wrong monitor. 

Definitely try the nvidia-settings as recommended above first and foremost.

Thanks both.  I went back and chose the recommended driver.  Then did the gksudo nvidia-settings.
(Btw, I have 2 icons that show up in the application launcher or dashboard or whatever it's called, if I search.  See attached.)

It seems to recognize my monitor all right.  See figure attached.

I was able to get the settings to be what I wanted but despite saving the configuration, **every time I restart, it goes back to the 1024x768**.

But, I'm definitely further along than I was 2 days ago, again, thanks for bearing with me all along...

---

### Post by TeoBigusGeekus on 2012-02-16
Can you post us your /var/log/Xorg.0.log as well as your /etc/X11/xorg.conf files?

---

### Post by sumithar on 2012-02-16
> **TeoBigusGeekus said:**
> Can you post us your /var/log/Xorg.0.log as well as your /etc/X11/xorg.conf files?
Sure- I have uploaded them both...Thanks for looking into this.  I had to copy and rename the files with a .txt extension.

Btw, today I'd a slightly different scenario.  I rebooted my machine and initially when I went into the X-settings panel, it didn't identify my monitor and showed CRT 1024x768!
I then logged off and logged back on again and this it showed the right monitor tho the resolution was still 1024x768.
I changed it back to 1280x1024.

Gosh you guys are most helpful!

---

### Post by TeoBigusGeekus on 2012-02-17
Ok, last try:
```
gksu gedit /etc/X11/xorg.conf
```
Change these lines
```
Section "Screen"

# Removed Option "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
# Removed Option "metamodes" "1280x1024 +0+0; 1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

to

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "1280x1024"
    EndSubSection
EndSection
```
save, reboot, post us what happened.
If it works, don't ever open the nvidia tool again.

---

### Post by sumithar on 2012-02-17
> **TeoBigusGeekus said:**
> Ok, last try:
```
gksu gedit /etc/X11/xorg.conf
```
Change these lines
```
Section "Screen"

# Removed Option "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
# Removed Option "metamodes" "1280x1024 +0+0; 1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

to

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "1280x1024"
    EndSubSection
EndSection
```
save, reboot, post us what happened.
If it works, don't ever open the nvidia tool again.

So this is what I did. 
At this point I have used the nvidia tool to set the res to be 1280x1024, right?
I shut down and restarted.  Predictably the display reverted to 1024x768.  I made the changes to the xorg.conf file like you suggested above.
I rebooted and display was still 1024x768.
The xorg.conf file looked the same as before the boot, i.e. with the changes you suggested to make.

I used the nvidia tool to set the resolution to 1280x1024.  Now the bottom of the xorg.conf file looked like this
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


FWIW, I overwrote this again with what you recommended and rebooted yet again.

Resolution was back to 1024x768.

It's as if it refuses to recognise the values in the xorg.conf file when it boots up but when I use the tool, it records it in xorg.conf, anyway.

I could live with this if there was some way to do thru a script what I am doing thru the nvidia tool and then I can add this script to the logon proc.

Thanks!

---

### Post by TeoBigusGeekus on 2012-02-18
What can I say mate...
One more thing you could try is to use the open source nvidia driver (nouveau) instead of the proprietary one; perhaps you'll get lucky with this one.

---

### Post by sumithar on 2012-02-20
> **TeoBigusGeekus said:**
> What can I say mate...
One more thing you could try is to use the open source nvidia driver (nouveau) instead of the proprietary one; perhaps you'll get lucky with this one.

Oh well...I don't know how to do that, I can't find those drivers.  I will get by, I guess.

This is very mysterious.  Should I raise a ticket with Ubuntu team, you think?

Maybe I should check with the Zotac people- they might have some customer support.

---

### Post by RedRat on 2012-02-20
> **sumithar said:**
> Oh well...I don't know how to do that, I can't find those drivers.  I will get by, I guess.

This is very mysterious.  Should I raise a ticket with Ubuntu team, you think?

Maybe I should check with the Zotac people- they might have some customer support.

I am sympathetic. I also run 8.04 and found that Ubuntu and video drivers seem to have problems. It took me about 6 months before I got my Nvidia card and 8.04 to get along. If Ubuntu has a weak point, it seems to be graphics. It may well be that the people who make your card have introduced some proprietary influence between the Nvidia chip and their chips so that Ubuntu doesn't quite recognize it.

I found great difficulty getting the proprietary drivers to work but could get along with the open source ones. But then I don't utilize all the bells and whistles of compiz.

---

