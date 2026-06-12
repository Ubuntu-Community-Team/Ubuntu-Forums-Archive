---
title: "Unusual Urban Terror problem in Ubuntu 9.10"
date: 2010-02-13
forum: General Help
---

### Post by vizitorq on 2010-02-13
Hey everyone, I recently re-installed Ubuntu 9.10 because of a bug in Nautilus that was beyond me. Anyway, I've been able to configure everything in my system back to the way it was before, if not, it's even better.

However, the last thing I'm trying to do is get Urban Terror to function properly. I remember having problems with crashing on exit, and during gameplay, the audio would just go out maybe after the first couple of minutes, sometimes even in the menu screen. But this happened when I downloaded the .zip file from the urban terror website and just ran the executable that was found inside the folder once I unzipped it.

Then after doing some research I found that someone put together a debian package for hardy, and after adding the repository, I was able to install it just fine, and it worked perfectly after that with no problems, so I was under the impression that I'd found a timeless solution.

This is not the case. After setting up my Ubuntu 9.10 desktop all over again, I find the deb, change the repositories, and install it. But now, I still have the same exact sound problem and crash on exit.

So I do some more research, and I find out that it has something to do with pulseaudio. So, I install pulseaudio. Now, when I run urbanterror in the shell, it doesn't load, but instead everything goes WHITE. And I mean EVERYTHING. It's so weird... Compiz still works, but the cube, and every window turns completely white. I can't do anything. Nothing is happening. I have NO idea what to do, as I have never heard of this problem before...

At least if everything wasn't white I'd at least be able to see what the shell has to say about it, but I can't even do that.

Any suggestions????

---

### Post by vizitorq on 2010-02-13
I was able to fix this problem by sudo apt-get remove urbanterror. then re-installing it with aptitude again... I guess pulseaudio should be installed FIRST, THEN install urban terror

---

