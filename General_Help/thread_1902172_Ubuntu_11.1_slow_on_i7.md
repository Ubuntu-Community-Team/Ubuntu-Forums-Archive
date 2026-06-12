---
title: "Ubuntu 11.1 slow on i7?"
date: 2011-12-30
forum: General Help
---

### Post by hatashii on 2011-12-30
I've installed Ubuntu 11.10 on my computer today. Everything works fine, all the hardware is detected and functional etc.. but my problem is the fact that when I move a window it starts lagging really badly; I looked at the processor usage while I moved a window and it went up to 80% and that is waaaay to much.

My processor is an i7 860 3.4Ghz, with turbo boost and hyper threading.
My graphics card is an Nvidia GT240 1GB
and I got 8GBs of RAM DDR3 @3333Mhz
x64bit system

How can I fix this problem? I installed and activated the nvidia driver which it detected by itself but it didn't make a difference. So I got rid of it, went on the actual nvidia website and got the official linux driver for my card. The problem now is that it is a .run file and I have to open it with terminal - when I do it says I have to quit 'X server' I have no clue what that is or how to stop it, doing a quick google it came up with a bunch of CTRL+ALT+1 options etc... nothing really helped
And I don't think the graphics driver is really my problem, I mean why would my processor usage go up so high then?

I really like Ubuntu but I can't use it if it just starts lagging. I'm new to the forums and any help is much appreciated.

- Hatashi

---

### Post by Mars11 on 2011-12-30
[s]Actually, moving a window has to do with the graphics card.[/s] Did you reboot after installing the nVidia Drivers?

---

### Post by 3rdalbum on 2011-12-30
It's a known problem and usually caused by having a mouse with a very high sampling rate.

It's got nothing to do with graphics drivers; it seems to be a slight problem with Compiz at the moment.

You can turn down your mouse's sampling rate in xorg.conf and the problem will go away; unfortunately I can't remember how to do this, but maybe some searching in Google will help. Or look on Launchpad - there is a bug report.

---

### Post by QIII on 2011-12-30
If that's a slight problem, a grizzly bear is a slight danger...

---

