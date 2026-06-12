---
title: "Resolution and Display issues"
date: 2010-01-04
forum: General Help
---

### Post by Moonstorm on 2010-01-04
I'm pretty much brand new to the linux scene, so my knowledge is very limited. I apologize if this is a common problem and I just used the wrong keywords to search for it. 
The problem:
during the startup cycle, my laptop doesn't display anything prior to the login screen on it's primary screen, but it does display it to my VGA output. The login screen is visible, but the virtual screen size is larger than the actual one, putting everything off-center. Then once in ubuntu itself, the screen resizes to a slightly less off-kilter display, but still too large for the screen. 
I've tried mucking about in the console and in xorg.conf, but nothing I do seems to help. 
I'm running karmic on a Dell inspiron 1545, and I'll can give details as to hardware and stuff if it's needed.

Cheers.

---

### Post by alwayshere on 2010-01-04
on startup pushing Esc then  choose recovery mode(the line 2nd from the top .

then let it do its thing when the optrions menu shows up choose the xfix option and see if that helps ya .

---

### Post by Moonstorm on 2010-01-04
had two possible recovery modes, tried both. In the 2.6.31-16 kernel, halfway through the repair my laptop screen comes on and mirrors my VGA, in the other, 2.6.28-17, nothing. Once that's done I get the options menu from both, but xfix wasn't avaliable. IIRC: resume, clean, dpkg, grub, netroot, and root were the only options. After trying resume, I tried throwing commands out, and one of the packages avaliable was xfig, thought maybe you typo'd and tried to install it. It errored out and so i exited and restarted. Only change is that the resolution of the OS has been reset to the "proper" resolution for the screen, which itself is at the incorrect resolution, so it's still off the side.

IDEA: Just tried running it without ever plugging in the VGA - loading and recovery menu was done blind, then when recovering the screen was at the huge resolution, as was the options menu. exited out and restarted. The options menu, recovering screen, and logon screen are all of the same resolution and it gave me a thought. When I run xrandr it gives me two different resolutions for my screen size, the current being 2048x1536 (my OS oversized screen) and maximum being 8192x8192 (possibly the over-large logon screen). How could I manually edit those numbers?

---

### Post by alwayshere on 2010-01-04
maybe this will help 

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html]("http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html")

---

### Post by Moonstorm on 2010-01-04
Maybe I mistyped: I mean to change the screen size, not the resolution. My laptop's monitor believes that it is larger than it actually is, so while I can change the resolution to my hearts content, it maintains a segment off the side of the screen. I was wondering if there was a way to edit the screen variables, not the resolution of xrandr.

---

### Post by alwayshere on 2010-01-04
In your first post you say "virtual screen size" are you using virtaual box or something ???

---

### Post by Moonstorm on 2010-01-04
I don't know what that is. I meant the bounding area that the computer paints, as opposed to the physical width and height of a monitor.

---

### Post by Moonstorm on 2010-01-05
Maybe I should just start at the first error and try and figure that one out first.
My laptop displays anything prior to logon to an external screen. How can I change it so that it displays on my main monitor?

---

