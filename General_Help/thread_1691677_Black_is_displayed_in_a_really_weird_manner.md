---
title: "Black is displayed in a really weird manner"
date: 2011-02-20
forum: General Help
---

### Post by Quchen on 2011-02-20
Hey there.

**The story.**
A few hours ago, I made the newbie mistake of copying old libs to /usr/lib, not thinking about that some of them might be overwritten by older versions. Of course, this was the case. However, I was able to recover the system by copying the current libs back to my system using the Live CD.
The files I'm talking about are [FONT=Courier New]libgd.so.2[/FONT] and [FONT=Courier New]libfreetype.so.6[/FONT].
The system itself is working fine again now.

**The Problem.**
However, when I start a YouTube video, it kind of saves what is displayed in the background. From that moment on, whenever the display shows perfect black (#000000), that flash image is displayed. While I'm writing this post using black font, it's all full of the YouTube video I was watching.
In other words, there seem to be two overlaying screens displayed: One in the background, one on the foreground. The foreground one is my normal Gnome UI, but all the perfect blacks are in fact transparent, showing the background image. This background image is completely black, but at the very place where the (YT-)Flash window was, it displays the last image that window showed.
I could make a few shots of my screen to make this clearer (i.e. digital camera photo of my screen - normal screenshots don't show the error, gah) if that helps.

I so hope someone else has already had this problem ... my first attempt would be re-installing all the lib files to current versions, but I couldn't find a corresponding entry in synaptic.

Thanks in advance,
Quchen

---

### Post by Quchen on 2011-02-20
Alright, tried a few things.
Uninstalling the NVidia drivers, reinstalling the NVidia drivers.
Uninstalling Flash, reinstalling flash.
Reinstalling the libraries that were available in synaptic.
Problem's still there.

On the other hand, I've found a workaround: Changing the screen resolution in the NVidia settings manager temporarily removes the problem (until I reboot). Editing xorg.conf didn't help that the problem reappears after a reboot though.

---

### Post by hhegner on 2011-02-21
I think I have the same prob. Only way for me to remove it is to reboot.

---

### Post by Quchen on 2011-02-21
Well I can't reboot every time I've viewed a YT video, can I? In addition, I usually suspend my laptop. ;(

---

### Post by Cocytuss on 2011-02-22
I am looking into what the problem is as of now. You mentioned you are using the newest Nvidia drives. I am guessing you are using x-swat. A quick fix is just to flush the video buffer with Ctrl+Alt+F1. This will bring you into a "shell" then to get your desktop back with Ctrl+Alt+F7 (F7 in my case since I use compiz with a 6 desktops)

One more thing. The new Nvidia 270 drivers are borked with VMWare's 3D. I would revert back to the 260.18 drivers for now.

---

### Post by arkangl on 2011-02-22
I have the exact same problem.

I have no idea what started it.

Cocytuss's video-buffer-flushing fix works.
It's better than a reboot.

---

### Post by Quchen on 2011-02-22
Reinstalled Ubuntu. The problem is gone, surprise.

---

### Post by arkangl on 2011-02-24
Any idea what could have caused the problem?

I'd rather not have to reinstall.

---

### Post by lewys93 on 2011-02-25
I have exactly the same problem - I took a screenshot for reference, but it doesn't show up

---

