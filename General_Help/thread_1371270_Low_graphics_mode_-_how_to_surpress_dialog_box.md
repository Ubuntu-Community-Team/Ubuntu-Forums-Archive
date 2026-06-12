---
title: "Low graphics mode - how to surpress dialog box"
date: 2010-01-03
forum: General Help
---

### Post by jamoo1980 on 2010-01-03
Hello all

I have an Ubuntu 9.04 Desktop box which I use as a media server. Until recently, I was running it as a desktop machine with a monitor connected to it. However, I would now like to remove the monitor, since I only ever access it via ssh -X from another machine. (Amarok runs on the media machine, with the GUI displaying on my laptop but the sound playing back from the media machine.) The problem is this: when I unplug the monitor from the server and restart, the machine does not fully restart; it displays a dialog telling me that "Ubuntu is running in low-graphics mode." No matter what settings I choose on this dialog, it always seems to reappear the next time I restart with no monitor plugged in.

I could get around the problem by leaving a monitor plugged into the system, for sure. But this seems ridiculous since the machine will be sitting in a cupboard. It also means that I can't use the monitor for anything useful!

All I want is for the machine to start up "as if there were a monitor attached", so that I can ssh -X into it and run Amarok from my laptop, but with the sound playing from the media machine.

I've tried editing xorg.conf with no success; and I've heard that 9.04 doesn't even use this file any more anyway.

I've also considered running Ubuntu using Gnome at all, but I ran into problems configuring PulseAudio to work properly. It seemed a waste of time when it works fine under Gnome...

Any ideas? Is it possible to somehow force Ubuntu to start X with fixed settings (other than by using xorg.conf, which doesn't seem to have worked)? Or is there a way to stop X from detecting the settings of the connected monitor and simply use the most recent? Any suggestions would be very very greatly appreciated.

Thanks :)
James

---

### Post by dinw3 on 2010-01-03
I have same problem , using 9.10 version

---

