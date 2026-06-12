---
title: "Settings lost after each reboot...Please help!"
date: 2010-05-16
forum: General Help
---

### Post by Toshibawarrior on 2010-05-16
Hello all! I've been googling and testing since yesterday with no luck. The problem is: I installed Kubuntu on my Toshiba A135 with no problems at all...everything works: sound, wifi, LAN, etc...BUT whenever I reboot/restart the computer my Display and Audio settings revert back to default, and it doesn't happen when I log out, just when I restart/shutdown the computer.

I have an Intel 945GM chipset and I have set my external Acer 23" monitor as the default and only monitor with a resolution of 1920x1080@60Hz using KDE's System Settings...And I chose to disable the laptop's internal monitor...but whenever I restart, the display returns to a 1024x800 cloned resolution (the default one)...which by the way looks hideous on a 23" monitor. And also the sound mixer goes back to the default levels.

So, can anyone help me out? I've been using Ubuntu for over 3 years and I've never had any problems like this one. I have just fell in love with Kubuntu, it looks and runs great, but this problem/bug is keeping me from being comfortable with it...

I've been reading some things about XRandr and some commands and stuff and nothing have worked until now.

I wonder, is it a common bug in Kubuntu or maybe an erroneous setting in the session manager....? 

Please, someone, anyone help me! Thanks in advance! :popcorn:

---

### Post by TeoBigusGeekus on 2010-05-16
Search for a tool in your Preferences or Administration menu that is specific to intel chipsets and then run it as administrator in order to make the changes permanent.
I, for example, have an Nvidia card; if I try to make any changes from ubuntu's utility, they are not saved permanently. If however I open the nvidia settings utility with
```
sudo nvidia-settings
```
the changes are written to xorg and they are permanent.

---

### Post by Toshibawarrior on 2010-05-16
Thanks for the reply! Sadly such a tool doesn't exist as far as I know. I've looked everywhere on my Kicker panel and on KPackageKit and nothing seems to do that. The weird thing is that back in Ubuntu I did everything through GNOME's Screen Resolution/Display application from the Preferences menu...I never had any problems with it.

And the worst part is that ever since the Xorg got an update I haven't been able to figure out how to edit the configuration file... :(.

Any ideas?...Should I try to manually edit the conf file?

Edit: I'm running Kubuntu 10.04 by the way and when I was installing it I had the external monitor plugged in...does it have anything to do with the configuration process?...As I said earlier, I had this exact same setup with Ubuntu and I never had any problems (except when I turned both monitors on and set them side-by-side which made Compiz very mad...).

---

### Post by Toshibawarrior on 2010-05-19
BUMP?

I managed to reduce the annoyance level by just putting the computer to hibernate instead of shutting it down...but that's not a solution, just a work around...:( Please help!

---

### Post by ankspo71 on 2010-05-20
Hi,
I used to have this problem with another distribution in the past. What I did was create a startup application entry for xrandr.

try this command from the terminal:
```
xrandr -s 1920x1080
``` 
or this one
```
xrandr -s 1920x1080 -r 60
```

See which one works best, try then to create a startup application entry for xrandr using one of those commands.
Hope this helps.

---

### Post by Toshibawarrior on 2010-05-20
> **ankspo71 said:**
> Hi,
I used to have this problem with another distribution in the past. What I did was create a startup application entry for xrandr.

try this command from the terminal:
```
xrandr -s 1920x1080
``` 
or this one
```
xrandr -s 1920x1080 -r 60
```

See which one works best, try then to create a startup application entry for xrandr using one of those commands.
Hope this helps.

Thank you very much!!! I never thought of that! I made a simple script with that command and it works great!! Thanks for your help!! :)

---

