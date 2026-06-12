---
title: "screen resolution totaly wrong on live disc"
date: 2010-02-11
forum: General Help
---

### Post by threee6 on 2010-02-11
i have just tried ubuntu 9.10 runing the "try ubuntu without changing" mode and the screen resolution was totaly off, it was 800 x 600 and there was only one other optinion wich was even worse , my screen res on windows is 1366 x 798.... Is this a problem that would rectify itself if i installed ubuntu properly or is there something i need to do?? i'm a total noob at this so please speak simply and slowly lol.... Any help would be mutch apreciated, thanks, threee6

---

### Post by Arenlor on 2010-02-11
Under System > Administration > Hardware Drivers does it list anything for you?

---

### Post by threee6 on 2010-02-11
> **Arenlor said:**
> Under System > Administration > Hardware Drivers does it list anything for you?

it just says "no proprietary drivers are in use on this system" .... could this be somethink that might be resolved after a full install or is that not relivent? i wont ubuntu as the only OS on this laptop but obviosly i don't want to get rid of windows if i cant solve this problem. thanks for the help

---

### Post by Arenlor on 2010-02-11
I had been hoping there would be a proprietary driver in use on the system. What is the graphics card/integrated chipset?

---

### Post by threee6 on 2010-02-11
> **Arenlor said:**
> I had been hoping there would be a proprietary driver in use on the system. What is the graphics card/integrated chipset?

um , i wouldent even know how to find out lol

---

### Post by koanhead on 2010-02-11
The problem may or may not rectify itself on installation depending on what hardware you have. Most likely it will.
It is probably possible to fix the resolution on the liveCD, but it may not be worth the effort since you'd have to do it again each time you reboot.
If you install Ubuntu and the problem persists, the information (and helpful people) here in the forums can most likely help you get it sorted.

---

### Post by houseworkshy on 2010-02-11
First System>Administration>Software Sources.  Go to the tab marked "third party software.  Then make sure that all the boxes except "source code" are ticked.  Then close the window.  You will be asked to update the lists, do so and close the box.

Next System>Administration>Update.  Choose to update, you may be asked to enter your password, do so and the update will proceed.  This will take a few minuets because as it is a new install you will need to get eveything since the iso was releaced.  After this you will be asked to reboot, do that.

Then System>Administration>Hardware drivers.  Password again.  One of the possable drivers should be highlighted and marked as recommended.  Make sure that it is highlighted then click the enable button.  Let it do it's thing, close the window and then once again reboot.  That should be it.

When you are done with that this is worth looking at [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)

It's a brief beginners guide and a good start.

---

### Post by threee6 on 2010-02-11
> **houseworkshy said:**
> First System>Administration>Software Sources.  Go to the tab marked "third party software.  Then make sure that all the boxes except "source code" are ticked.  Then close the window.  You will be asked to update the lists, do so and close the box.

Next System>Administration>Update.  Choose to update, you may be asked to enter your password, do so and the update will proceed.  This will take a few minuets because as it is a new install you will need to get eveything since the iso was releaced.  After this you will be asked to reboot, do that.

Then System>Administration>Hardware drivers.  Password again.  One of the possable drivers should be highlighted and marked as recommended.  Make sure that it is highlighted then click the enable button.  Let it do it's thing, close the window and then once again reboot.  That should be it.

When you are done with that this is worth looking at [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)

It's a brief beginners guide and a good start.

after a full install and trying this i still get "no proprietary drivers are in use on this system" anyone have any other ideas :(

---

### Post by patchwork on 2010-02-11
Open a terminal and type:

```
lspci |grep VGA
```

and please post the output here.  This will tell us what video card you have installed.

This is not mandatory, but may make your life a lot easier in the long run:
get the program read-edid from the repositories, and then run the program to see if your monitor is properly sending it's edid information (my guess is it's not):

```
sudo apt-get install read-edid
sudo get-edid

```

If your monitor is not sending the full edid information, you will see an error such as this (from my 1366x768 laptop):

```
Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

```

Also, if you can post your /etc/X11/xorg.conf and your /var/log/Xorg.0.log here, that would help.

---

### Post by efflandt on 2010-02-11
Although, many 720p displays call themselves 1366x768, they might actually be slightly different.  For example WinXP uses 1360x764 (which is sharp), or when I looked through /var/log/Xorg.0.log it showed a 1360x765 mode.  Although, System > Preferences > Display did not offer that mode (maybe because it only activated modes that it saw in EDID for both laptop and external VGA).  When I tried a 1280x720 mode it did offer, that was way overscanned (maybe due to laptop display being 1280x800)

So I used **cvt 1360 765** to find a modeline for that, and xrandr commands to try it out.

Just an example that worked for me.  Note, see what **xrandr** shows for your video device which may be something other than VGA1 (for example ATI might be VGA-0).  And if cvt comes up with a different modeline, try that:

```
xrandr --newmode "1360x765_60.00"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
xrandr --addmode VGA1 1360x765_60.00
xrandr --output VGA1 --mode 1360x765_60.00
```

---

### Post by houseworkshy on 2010-02-12
This is not a fix but may be an easier way of finding and posting the sort of information which will allow more knowlageable people to help.
In a terminal ( Applications>Acessories>Terminal ) enter "sudo apt-get install sysinfo" Then enter your password ( there will be no stars or blobs to show that you are doing it, this is normal )
This will install sysinfo.
Exit the terminal and Applications>System tools>Sysinfo
In the program which pops up  File>Save  navigate to your desktop ( or where ever ) call it something like report.txt and save it.  Posting what is in that will help people to work out what is going on.  Good luck.  Oh and as I don't know just how badly your display is messed up "sudo shutdown -r now" entered in the terminal will restart without needing the gui shutdown button or the pc power button. Very annoying if one can't get at the top right corner sometimes.  Good luck.

---

### Post by Grenage on 2010-02-12
You'll most likely be able to get the correct resolution with a custom xorg.conf, it certainly looks like an EDID issue.  I have a guide [here]("http://www.grenage.com/xorg.html") which should take you through some easy steps to get it done.

---

