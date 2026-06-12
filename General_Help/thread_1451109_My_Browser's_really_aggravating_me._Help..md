---
title: "My Browser's really aggravating me. Help?."
date: 2010-04-10
forum: General Help
---

### Post by JoeyF on 2010-04-10
*Edit:Skip to page 2. Update*


*Computer:Emachines W3650.
OS:Mint 8 32 Bit(Ubuntu 9.10).
Doesn't matter if I am using effects or not.
(Scrolling)Isn't an issue with the mouse.
Have done:
```

sudo apt-get install xserver-xorg-video-intel
```
```
sudo dpkg-reconfigure xserver-xorg
``` *


It started months ago when I had Ubuntu 9.04 or 9.10 on there. It went away. Came back once. Quit. And has come back since I installed Mint 8.(The scrolling hardly did it back then(I think it did it back then). But does it a lot now)

One thing it does in Firefox(I haven't had it in other browsers yet) is sometimes on Youtube when I move over a link it flashes from the arrow to the hand. I have heard of some other people having that problem(Search:firefox flickering cursor ).

The next problem happens on Chrome as well(Haven't had it on Opera yet)(Can't use Opera because sometimes on Youtube the video play button messes up, And BlogTV messes up too).

The other problem is the scrolling(I'm using the MMB btw). I can be on Yahoo! Answers looking at questions and if I'm scrolling down it will jerk up towards the top. Also if I am scrolling to the top.


Also, When I am scrolling in a folder like My Music is does something similar. It's a little jerky sometimes.


Also, 

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

I have heard something about it being Xorg.



Any ideas?. I really want to get this one working so I can give it to a friend.

Thanks.

---

### Post by mike555 on 2010-04-10
not sure if it will work , but turning off visual effects (compiz) might help....

---

### Post by jwbrase on 2010-04-10
> **mike555 said:**
> not sure if it will work , but turning off visual effects (compiz) might help....

Sigh...

The OP said:

> **JoeyF said:**
> Doesn't matter if I am using effects or not.

---

### Post by JoeyF on 2010-04-11
Bump?.

Thanks.

---

### Post by JoeyF on 2010-04-11
Last bump?

---

### Post by JoeyF on 2010-04-15
Add:
I've tried Smooth Scrolling on Firefox and Chrome. But nothing.

Hopefully I can at least get Chrome working as the cursor thing doesn't happen on it,

Also, I tried removing xserver-xgl but it said not found.

Should I post my Xorg?. How would I go about doing that?.


Thanks.

---

### Post by pastalavista on 2010-04-15
I fixed a similar problem by using Compiz with minimal effects but turning 'Regex Matching' off (I don't even know what that is but it was on by default) but then, I have ATI graphics. Have you tried the old stand-by? ...probably have```
sudo dpkg-reconfigure xserver-xorg
```Good luck finding an answer. Somebody with your setup will see this eventually.

---

### Post by JoeyF on 2010-04-15
> **pastalavista said:**
> I fixed a similar problem by using Compiz with minimal effects but turning 'Regex Matching' off (I don't even know what that is but it was on by default) but then, I have ATI graphics. Have you tried the old stand-by? ...probably have```
sudo dpkg-reconfigure xserver-xorg
```Good luck finding an answer. Somebody with your setup will see this eventually.

I think I may have already tried the reconfigure. I'll try it again.

Thanks.

---

### Post by JoeyF on 2010-04-16
I shortened the question a bit so it makes more sense.


No luck with the reconfigure. 

Thanks though.

---

### Post by JoeyF on 2010-04-18
I'll do some updates with the Update Manager. Some are Firefox Gnome Integration or something. 

Also, Anybody think trying KDE might work?.

But if I had to guess. I would say it's something to do with updates.


Anyways, Thanks.

---

### Post by JoeyF on 2010-04-18
Update:
I decided to plug in my standard, Logitech Mouse into my Laptop and it does it too. But not with my Wacom or Trackpad.

I looked at my Xorg but didn't see anything related to the mouse. Is it because I turned the Laptop on before I plugged the mouse in?.


Something I found:
[http://ubuntuforums.org/showthread.php?t=286124](http://ubuntuforums.org/showthread.php?t=286124)

*See the post by Mahmoud*

Thanks.

---

### Post by JoeyF on 2010-04-21
Bump.

Thanks.

---

### Post by JoeyF on 2010-04-24
Edit:I know it's not my mouse. My mouse is young and worked fine under Windows.


Thanks.

---

### Post by JoeyF on 2010-04-25
Add:The mouse is just a regular USB Logitech.

Also, Once in a Blue Moon the cursor flickers when I hover over a Youtube link.


Thanks.

---

