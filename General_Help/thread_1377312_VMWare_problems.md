---
title: "VMWare problems"
date: 2010-01-10
forum: General Help
---

### Post by DeMus on 2010-01-10
Hi,

I just installed VMWare on my Jaunty-64. In VMWare I setup a virtual machine using Linux Mint 8-64 as guest OS. Things run fine except for the sound. It doesn't matter what I play: music from disk, music from a radio station on the internet, system sounds, everything is played with sound-on, sound-off, sound-on, sound-off, ..... in a 1 sec. rhythm.
I have changed the audio device used by VMWare - no luck.
I have changed sound settings in Mint - no luck

What could be this problem and where can I change what to solve it?

EDIT: Just noticed it is not only sound it is also video. When I play a flash from the net the picture is starting and stopping just like the sounds does. What is this?

---

### Post by iponeverything on 2010-01-10
It might be related to realtime.

[http://ubuntuforums.org/showthread.php?t=1090906](http://ubuntuforums.org/showthread.php?t=1090906)

---

### Post by DeMus on 2010-01-11
> **iponeverything said:**
> It might be related to realtime.

[http://ubuntuforums.org/showthread.php?t=1090906](http://ubuntuforums.org/showthread.php?t=1090906)

Thanks for your answer. In the mean time, late last night, I have found the solution however. I had to install pulseaudio in my host OS. That fixed it.

---

