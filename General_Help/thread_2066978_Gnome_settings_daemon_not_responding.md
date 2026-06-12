---
title: "Gnome settings daemon not responding"
date: 2012-10-05
forum: General Help
---

### Post by MadCityGeoff on 2012-10-05
I get this message whenever I try to shut down Ubuntu 12.04. It's a fresh installation on a dual-boot system with Windows 7.0 and an ATI 7970 graphics card. Sometimes I can shut down by trying a second time and sometimes the system locks up. I'm running the proprietary driver and not the updated one since it wouldn't activate. Any suggestions would be greatly appreciated.

---

### Post by daslinkard on 2012-10-05
> **MadCityGeoff said:**
> I get this message whenever I try to shut down Ubuntu 12.04. It's a fresh installation on a dual-boot system with Windows 7.0 and an ATI 7970 graphics card. Sometimes I can shut down by trying a second time and sometimes the system locks up. I'm running the proprietary driver and not the updated one since it wouldn't activate. Any suggestions would be greatly appreciated.

Are you able to properly shutdown by running the following sudo command:
```

sudo shutdown -h now
```

---

### Post by MadCityGeoff on 2012-10-06
Yes, running that command line shut down the system perfectly.

---

### Post by daslinkard on 2012-10-07
> **MadCityGeoff said:**
> Yes, running that command line shut down the system perfectly.
Are you happy with the result and want to consider this thread solved?  If so, please mark as such....if not let me know what I can do to help!  Thanks!

---

### Post by MadCityGeoff on 2012-10-07
I'd much rather be able to shut down the system from the menu instead of having to run a command line every time. Plus, the error about the Gnome settings daemon makes me wonder if there's something wrong that'll turn up in other ways. So, yes, I'd appreciate further suggestions. Thanks very much!

---

### Post by sandyd on 2012-10-07
can you open your terminal (Unity Dash -> Type in "Terminal")

And run (your password will not show, even if it is entered)

```

sudo apt-get update
sudo apt-get upgrade

```

Restart your computer later, and see if the issue still persists. If it does, post back.
Thanks!

---

### Post by MadCityGeoff on 2012-10-07
I ran the update and upgrade commands as you specified, but I'm still getting the Gnome settings daemon error when I try to shut down. Any other thoughts?

---

### Post by GreatDanton on 2012-10-07
I had slightly different problem in 12.04, so I am not 100% if this is going to solve your problem, but you can try. If this will not work you can still change it back to the previous state.

[http://ubuntuforums.org/showpost.php?p=12056341&postcount=2](http://ubuntuforums.org/showpost.php?p=12056341&postcount=2)

Regards.

---

### Post by MadCityGeoff on 2012-10-07
That didn't work either. I followed the instructions in your link and added "acpi-force" to grub and updated. I restarted a couple of times, but the Gnome error message is still there whenever I try to  shut down.

---

### Post by daslinkard on 2012-10-07
> **MadCityGeoff said:**
> That didn't work either. I followed the instructions in your link and added "acpi-force" to grub and updated. I restarted a couple of times, but the Gnome error message is still there whenever I try to  shut down.

What about purging the current gnome-shell and then re-installing?

Either by doing:
```
sudo apt-get purge gnome-shell
```

Then 
```
sudo apt-get install gnome-shell
```

Then reboot....

or you can go with Gnome 3
```
sudo add-apt-repository ppa:gnome3-team/gnome3
```
```
sudo apt-get update
```
```
sudo apt-get install gnome-shell
```Maybe one of these will work at solving the issue for you....let us know!

---

### Post by MadCityGeoff on 2012-10-08
Well, this is interesting. I tried the purge command to get rid of gnome-shell and got "Package gnome-shell is not installed so not removed." It seems like I'm getting the error about the gnome settings daemon even though gnome isn't installed.

Anyway, I tried to install gnome by doing:

sudo apt-get install gnome-shell

It did a bunch of stuff and then I rebooted. When I got back, the UI looked like it always did, so I don't know if I should have done something else to install gnome. Anyway, when I tried to shutdown using the menu option, I got the same old settings daemon message.

I'm totally befuddled. Any other suggestions?

---

### Post by MadCityGeoff on 2012-10-08
I didn't try installing Gnome 3 due to aesthetic preferences, but I may give that or KDE a shot eventually. I'd really like to get the default shell working if possible.

---

### Post by MadCityGeoff on 2012-10-08
I'm really out of my technical depth here, but I wonder if this settings daemon problem has anything to do with the fact that I installed the 32-bit Ubuntu on my 64-bit system.

---

### Post by daslinkard on 2012-10-08
> **MadCityGeoff said:**
> Well, this is interesting. I tried the purge command to get rid of gnome-shell and got "Package gnome-shell is not installed so not removed." It seems like I'm getting the error about the gnome settings daemon even though gnome isn't installed.

Anyway, I tried to install gnome by doing:

sudo apt-get install gnome-shell

It did a bunch of stuff and then I rebooted. When I got back, the UI looked like it always did, so I don't know if I should have done something else to install gnome. Anyway, when I tried to shutdown using the menu option, I got the same old settings daemon message.

I'm totally befuddled. Any other suggestions?

The good thing is that you have rebooted your system for Gnome to take effect.  The next thing that you would want to do is to log out of your current session and log back in.  Now prior to logging back in you will see an icon to the right of your user name.  Please click on that and you should have the option to select Gnome when you log in.  If I am not mistaken Gnome Classic will also be an option.  

Once you have selected the shell you want to log in with, you will enter in your password and the Gnome shell should appear for you.  Try it and let me know if you notice the desktop is different.

---

### Post by MadCityGeoff on 2012-10-08
I started a new session and clicked the icon next to my name on the login screen and selected "Gnome" from the list. Eventually, I got a blank desktop wallpaper that was the same as the Ubuntu default. The mouse pointer functioned, but everything else was locked up. I turned off the power and tried again. This time, the Ubuntu login screen was locked up. It seems like the system is totally nonfunctional. I'm working off Windows now. Help please?

---

### Post by daslinkard on 2012-10-08
1st please try rebooting your system and then log off, log back in that way.  If that still gives you the same problem I want you to try logging in to your guest account and see if it loads properly.

---

### Post by MadCityGeoff on 2012-10-08
I rebooted and this time the Ubuntu login screen worked. I selected "Gnome" which got me the same blank, frozen wallpaper. I rebooted and selected the guest account, which worked and started the familiar Ubuntu UI. I came on to the forum here and started typing a message when the system locked up again. I'm back in Windows. One concern at this point is that I'm constantly rebooting the locked computer by turning off the power.

---

### Post by daslinkard on 2012-10-08
I'm wondering if it may be an issue with your graphics card (at this point)?

---

### Post by MadCityGeoff on 2012-10-08
It's an ATI Radeon 7970. I downloaded the driver during the installation. As I recall, there were two drivers. One of them had "updates since release" or something similar, but it wouldn't activate for me. I installed the standard driver instead.

---

### Post by daslinkard on 2012-10-08
> **MadCityGeoff said:**
> It's an ATI Radeon 7970. I downloaded the driver during the installation. As I recall, there were two drivers. One of them had "updates since release" or something similar, but it wouldn't activate for me. I installed the standard driver instead.
Here's a [link]("http://ubuntuforums.org/showthread.php?t=1935339") on your GC.

---

### Post by MadCityGeoff on 2012-10-09
Thanks for the link. I read that thread and others about problems with ATI video cards. If there's a solution, it's way over my head. At this point, my system is constantly locking up requiring me to shut off the power. Perhaps I'll try another version of Ubuntu in the future.

---

### Post by MadCityGeoff on 2012-10-09
Well, after wandering off in a huff, I decided to take one last try. I deleted the 32-bit version of Ubuntu 12.04, reformatted, and installed the 64-bit version. I activated the proprietary ATI driver and now everything seems to be working perfectly. There's no more "gnome settings" error when I log out. Plus, I seem to be getting the transparency and other visual effects that were missing before. For the moment at least, I'm enjoying Ubuntu very much. Thank you all for your help!

---

### Post by daslinkard on 2012-10-10
> **MadCityGeoff said:**
> Well, after wandering off in a huff, I decided to take one last try. I deleted the 32-bit version of Ubuntu 12.04, reformatted, and installed the 64-bit version. I activated the proprietary ATI driver and now everything seems to be working perfectly. There's no more "gnome settings" error when I log out. Plus, I seem to be getting the transparency and other visual effects that were missing before. For the moment at least, I'm enjoying Ubuntu very much. Thank you all for your help!
Sweet!  I'm glad this is working....I'm going to be able to add this to the bag of tricks of when there is an issue making sure which OS is installed.  

Please mark this thread as solved and at any point in time we can be of assistance here in the forum do not hesitate.  Good luck my friend!

---

### Post by smgendler on 2012-11-18
I realize this is solved.  The solution of going to 64bit worked!!  I even took a chance and hand installed the 64bit ATI drivers and they work (I was pretty sure I was gonna have to rebuild again on that one, but, lo and behold, it's working...[Article link here]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513")).  More than the "GNOME settings daemon" error disappearing, a bug where the GUI has terminal commands appearing in the middle of the graphics screen, they disappeared, too!!  AND, also fixed, the built in sound card works.  I have an Asus P8Z77-V Pro MB and before I had to go to Realtek and download and install their linux sound drivers, but now sound works right off the Ubuntu-alternate install disk.  I wonder if that fix has something to do with me using a 12.04._1_ installer instead of the original 12.04 installer.

So, here's my question:

_Why_ did going to the 64bit version of 12.04 work??? I realize CPUs are 64bit, but I don't understand why this works better than 32bit ESPECIALLY since Ubuntu recommends the 32bit version.  Anybody got any ideas?

Sadly, I've been using Ubuntu for about four years, and I still consider myself a beginner.  I'm still trying to figure linux out.

---

### Post by Robbin505 on 2012-12-05
This does not appear to be solved because although going to 64-bit worked to get the gnome settings daemon problem to stop I cannot get the drivers to install, I have a 7850 and every time I install it freezes on restart.  I am completely new to linux so this is really confusing for me.  I tried going to amd and manually downloading and installing but I apparently have no clue how to do that either.  I would really like some help, I wanted to avoid putting any Microsoft products on this computer.

---

