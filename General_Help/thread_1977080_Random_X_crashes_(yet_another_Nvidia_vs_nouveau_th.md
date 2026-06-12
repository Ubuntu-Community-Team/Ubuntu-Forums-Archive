---
title: "Random X crashes (yet another Nvidia vs nouveau thread)"
date: 2012-05-09
forum: General Help
---

### Post by azangru on 2012-05-09
Okay, I am one of those unlucky ones who have random X crashes in Precise (which look as if a sudden logout) that might be related to the NVidia proprietary driver, which I enabled during the installation.

I wanted to ask my specific questions, so I started a new thread.

1. I tried both proprietary drivers that Ubuntu suggested (NVidia accelerated driver current and Nvidia accelerated driver version-update). Experienced crashes on both of them. I then pressed the "Remove" button for both and now am running on nouveau. However, when I reboot my computer I have this moment of video card going crasy:

[IMG]https://lh3.googleusercontent.com/-a1gwpwl54No/T6reMT3rDpI/AAAAAAAABXM/3WUDLGWFzKM/s800/1.jpg[/IMG]
Booting. Notice no Ubuntu sign. And just at the moment when it used to appear I now have this:

[IMG]https://lh6.googleusercontent.com/-l4fYz0mE06U/T6reMbVaEvI/AAAAAAAABXI/5P-hjp1UOyA/s800/2.jpg[/IMG]
It lasts for only a couple of seconds but it is very disturbing. Is there any way to fix this?

There is no Xorg.conf file in /etc/X11 (if this is of any importance).

2. If I use nouveau, does it mean I am stuck with Unity2D? I kind of liked Unity3D when it didn't crash.

---

### Post by pbrane on 2012-05-09
> **azangru said:**
> 
It lasts for only a couple of seconds but it is very disturbing. Is there any way to fix this?

There is no Xorg.conf file in /etc/X11 (if this is of any importance).


I think the nouveau driver hasn't cleared the video RAM at this point. It's nothing to worry about.

The absence of a xorg.conf file doesn't mean anything, xorg can work without one.


> **azangru said:**
> 
2. If I use nouveau, does it mean I am stuck with Unity2D? I kind of liked Unity3D when it didn't crash.

nouveau doesn't have much 3D support yet.

 I have been using the proprietary nvidia drivers for years without any issues. You might try using the x-swat ppa version. They do a good job of testing the driver before they release a version in the ppa.

here is a link: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by azangru on 2012-05-09
> **pbrane said:**
> I think the nouveau driver hasn't cleared the video RAM at this point. It's nothing to worry about.

Weird. Of course I don't understand how video cards and their drivers work, but when I installed Ubuntu and it rebooted the first time after installation (it must have been running nouveau, because I hadn't activated proprietary drivers yet) I didn't get this ugly artifact.
So everyone with the same graphic card as mine who use nouveau driver will have the same picture during bootup?


> **pbrane said:**
> I have been using the proprietary nvidia drivers for years without any issues. You might try using the x-swat ppa version. They do a good job of testing the driver before they release a version in the ppa.

here is a link: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Could you please suggest the commands for this? I start with 

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

right? What do I do next?

---

### Post by markbl on 2012-05-09
> **pbrane said:**
> 
nouveau doesn't have much 3D support yet.
[/URL]
That is not true anymore. I have also used the nvidia drivers for years but due to the crashes in 12.04 (in v295-40, v295-49, and v302.07) I have switched back to nouveau and am surprised to see it runs Unity 3D and gnome-shell fine. That note in the "Additional Drivers" settings tool that you need the proprietary driver for Unity + 3D is out of date and should be corrected.

To the OP, yes I see that video fuzz at boot up also now on the nouveau driver but it quickly clears and ubuntu boots up and works fine. At least virtual consoles (ctrl+alt+f[1-6]) works with nouveau unlike the recent nvidia drivers.

---

### Post by azangru on 2012-05-09
> **markbl said:**
> To the OP, yes I see that video fuzz at boot up also now on the nouveau driver but it quickly clears and ubuntu boots up and works fine.

Sigh. I was hoping there was a way to get rid of it :(
Did you also first activate the proprietary Nvidia drivers and then remove them and switch back to nouveau or did you stick with nouveau from the start? Can this fuzz be due to some residual effect of removal of NVidia drivers?

> 
I have switched back to nouveau and am surprised to see it runs Unity 3D and gnome-shell fine.

I am also very much impressed with it. Shouldn't have activated the proprietary drivers in the first place.

---

### Post by markbl on 2012-05-09
> **azangru said:**
> 
Did you also first activate the proprietary Nvidia drivers and then remove them and switch back to nouveau or did you stick with nouveau from the start?
No. I [started with the nvidia driver](https://bugs.launchpad.net/unity/+bug/982485/comments/136).

---

