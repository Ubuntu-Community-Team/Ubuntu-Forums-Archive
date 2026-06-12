---
title: "Guys I need help - Whats your best way to install nVIDIA Drivers?"
date: 2011-04-29
forum: General Help
---

### Post by michaeldz on 2011-04-29
Guys, I did alot of reading on installing nVIDIA Drivers

So far, I did it through the Package Manager. But I got the older 260.* drivers.

I downloaded the main drivers from nVIDIA Page. Ran the RUN file.

I'm running an Giada PC with ION 9400 IGP.

What do you people recommend the best way to install? Custom build? Which I don't know how to...

This is very fustrating. I tried to get vdapu installed as well. But I still get Undefined Rendering in Flash Player. And Boxee plays videos cropped on the left hand side.

Right now I have 270.40.16 drivers installed.

HELP!

---

### Post by teknic111 on 2011-04-29
The easiest way is to go to System->Administration->Additional Drivers and install from there. It's pretty self explanatory once you're there.

---

### Post by michaeldz on 2011-04-29
Hi.

Yes, but doesn't get the nvidia-current packages? Some people say those are buggy, and have problems with it.

I couldn't even reinstall X server. When it did nothing...

Has anyone got VDAPU working with Adobe Flash here? There was a buggy flash version which disabled vdapu.  Do I need to install libvdpau1 separately, or do I need it at all? 

I think /usr/lib/vdpau should show the linking correct?

Any guys with experience on this would be appreciated.

---

### Post by mikewhatever on 2011-04-29
Install the nvidia-current package and Adobe flash player. If you have any problems after that, please detail them.

PS: People say lots of things, not all are true.

---

### Post by kaldor on 2011-04-29
I've always done it from the Additional Drivers utility. Reboot, and you're done.

---

### Post by bab1 on 2011-04-29
I have found that the SGFXI script listed [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://smxi.org/site/install.htm#sgfxi") works for me.  It will install *and remove *the latest nVidia drivers at nVidia's site.

Note that this was developed for Debian Sid, but at the present time it also works for Ubuntu.

If you are having Flash Problems in Firefox, I would recommend the Flash-Aid Plug-in to install the correct Flash, based on your architecture.  It has also always worked for me (8.04 through 10.10).

---

### Post by michaeldz on 2011-04-29
Guys I have no link with the vdpau library!

I believe I have 3D working...

> dwayne@dwayne-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
> dwayne@dwayne-desktop:/usr/lib$ ls libvdpau*
libvdpau.so.1  libvdpau.so.1.0.0
dwayne@dwayne-desktop:/usr/lib$ 
]

> dwayne@dwayne-desktop:/usr/lib/vdpau$ ls 
libvdpau_nvidia.so.1  libvdpau_trace.so.1  libvdpau_trace.so.1.0.0
dwayne@dwayne-desktop:/usr/lib/vdpau$ 
]

---

### Post by michaeldz on 2011-04-29
Okay.

So I installed the nVIDIA Current. Everything is good!

I installed the Flash AID Plugin. It enabled vdpau!

However, I installed libvdpau as well. When I right click on flash video, I get Hardware Acceleration. If I uninstall libvdpau, then I get Undefined Rendering, meaning, no acceleration!

The reason why I uninstalled libvdpau, is because in boxee, I was getting NO VIDEO, or double video! Imagine having double vision and seeing almost 2 of the same things. Pretty neat, but not in this case.

I also noticed some artifacts. Like, when you overclock a GPU. That sort of thing.

Still need help

How do I completely uninstall flash from the system so it doesn't even load in Youtube?

---

### Post by michaeldz on 2011-04-29
It's a bug in BOXEE!


[http://jira.boxee.tv/browse/BOXEE-8239](http://jira.boxee.tv/browse/BOXEE-8239)

---

