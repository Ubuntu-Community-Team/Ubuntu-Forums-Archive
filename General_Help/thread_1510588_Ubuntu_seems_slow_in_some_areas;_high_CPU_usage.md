---
title: "Ubuntu seems slow in some areas; high CPU usage?"
date: 2010-06-15
forum: General Help
---

### Post by Momotombo on 2010-06-15
I've been using Ubuntu consistently for about three days now. I really, really love the interface and how everything works and all that, but I've been having a couple of weird problems with speed.

Graphics things seem to work really well. When I go into the overview of all my workspaces, it's instant and looks great. The problem is when I open and use some applications.

For example, when I open up the software center, it takes longer than it did the first time to start up. Also, when I drag windows off from being maximized, it takes literally about five seconds for it to show up as being dragged around by my mouse.

When I look at the system monitor, about 20% of my CPU cores are constantly being used. That's 20% each. I have a 3-core CPU, could that be the problem?

Another example: when I went to youtube just now, it would take a second for any volume changes in the video to register.

And I also have smooth scrolling in firefox, but it's very unresponsive now. It's slow as all hell. Even notifications are showing up more slowly.

So, what's the deal? What could I have done wrong?

CPU: AMD Phenom II X3 2.8Ghz
GPU: ATI Radeon HD 4860 1gb
RAM: 4gb

One more thing: I have really bad screen tearing when I try to move windows around, as if there isn't any vsync on. Where can I turn it on or fix this?

Thanks. I'm still pretty new to Ubuntu and Linux, but I'm an advanced computer user. Since I feel linux is killing my CPU I think I'm going to boot back into Windows 7 for now, but if I can fix this problem I think I want to keep Ubuntu as my main OS after this, having Windows for games, unless I can get Wine to work right with them.

---

### Post by Momotombo on 2010-06-15
Let me also point out that on Windows again, webpages look cleaner and everything really is a lot faster for the most part compared to Ubuntu. I blame it on lack of hardware support.

---

### Post by Momotombo on 2010-06-15
Anything at all?

---

### Post by warfacegod on 2010-06-15
I'm guessing you need to install the driver for your video card.

Go to: System> Admin.> Software Sources> Ubuntu Software tab> enable Software restricted... (Multiverse)> Other Software tab> enable "partner" (top of the list)> Updates tab> enable Unsupported... (backports)

When you click Close, it will ask you to Reload, do so. Now go to: System> Admin.> Update Manager> install all updates

Now you'll want: System Admin.> Synaptic> search for ubuntu-restricted-extras> right click it and Mark for Installation> click Apply

Finally: System> Admin.> Hardware Drivers> click Activate for the (Recommended) video driver, if there is one.

---

### Post by Momotombo on 2010-06-15
When I first installed ubuntu, I got an icon in the top-right corner saying something about restricted drivers. I realized it was the video drivers, and I allowed it to install them. I have Catalyst now and everything, but I'll try these steps anyway. Maybe I don't have good drivers.

Also, when I enable extra effects such as wobbly windows, those are really fast. It's applications loading and working that seems slow for the most part.

---

### Post by warfacegod on 2010-06-15
Another thing you can do is go to: System> Prefs.> Startup Apps. Disable whatever you don't need to start when you boot your system Bluetooth, Ubuntu One, Check for drivers, etc.

This won't help until you reboot, obviously.

---

### Post by warfacegod on 2010-06-15
How much RAM do you have? From what you're describing, it sounds like you don't have enough. Matter of fact, you should post your system specs and which version of Ubuntu you are using.

---

### Post by warfacegod on 2010-06-15
Never mind just reread your first post. Your specs are more than enough. Turn Smoothscrolling off.

---

### Post by Momotombo on 2010-06-15
Main system specs are in the OP. Ubuntu is running off an IDE HDD, though most of what I try to do is on a 1tb SATA. I have 4gb of RAM, more than enough for anything IMO.

---

### Post by Momotombo on 2010-06-15
> **warfacegod said:**
> Never mind just reread your first post. Your specs are more than enough. Turn Smoothscrolling off.

Is there a problem with smooth scrolling in ubuntu or something?

Anyway, I need to go for a while, I'll try your steps when I get back.

---

### Post by warfacegod on 2010-06-15
Take a look at your System Monitor and watch for anything that's using allot of CPU.

System> Admin.> System Monitor> Processes tab

---

### Post by warfacegod on 2010-06-15
> **Momotombo said:**
> Is there a problem with smooth scrolling in ubuntu or something?

Anyway, I need to go for a while, I'll try your steps when I get back.

It makes things very jerky and rips the screen and tends to use a tremendous amount of VRAM and processor time. I had the same problem in Windows XP three years ago. If you let the icon install the driver, then the driver that shows in the last step will already be activated. Go through the steps anyway, it will give you access to other things such as mp3 playback.

---

