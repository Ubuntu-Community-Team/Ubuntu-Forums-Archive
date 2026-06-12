---
title: "Touchpad Issues on Pavilion dm4 - Can't right click"
date: 2010-11-27
forum: General Help
---

### Post by Habstinat on 2010-11-27
Excuse the horrid formatting, this was copy/pasted from the #ubuntu IRC and to be extremely honest I can't be bothered to remove every space.

                   Can anyone help me with my mouse issues? I have a 
                   Pavilion dm4 and it has two areas on the bottom of the 
                   touchpad to designate right and left clicks. This mostly 
                   doesn't work on Ubuntu in the fact that it recognizes any 
                   taps on either tap zone as a left click. Instead, I have it 
                   set so if I tap anywhere on the pad it makes a left click. 
                   There should be, and there are, many ways in the mouse 
                   configuration window to simulate a right click using only a 
                   touchpad. None of these work. Changing mouse orientation 
                   doesn't do anything, "dwell click" also does nothing, and, 
                   the oddest part of this problem, whenever I try to turn 
                   "Simulated Secondary Click" off (it doesn't work anyways, 
                   but just to try to toggle it), the entire theme of my 
                   desktop changes to a gray Windows '95ey look. The only way 
                   to get rid of this is to close and reopen the mouse 
                   preferences window.My computer is fairly new and the Ubuntu 
                   installation is less than a day old. I didn't do anything 
                   that I think could cause this. The problem is that I can't 
                   right click. Help, please?

Afterword: I installed two scripts from [http://sansmicrosoft.blogspot.com/2010/10/pavilion-dm4-1160-erratic-touchpad.html](http://sansmicrosoft.blogspot.com/2010/10/pavilion-dm4-1160-erratic-touchpad.html) . They didn't do anything I couldn't already do, and they did not make it possible for me to right click. :(

---

### Post by yousifmagdi on 2010-12-25
I'm having the same problem here. if you found a way out of this problem please pass it out.

---

### Post by ElSlunko on 2010-12-25
Lots of info and possible work arounds here : [http://ubuntuforums.org/showthread.php?t=1388164&highlight=dm4](http://ubuntuforums.org/showthread.php?t=1388164&highlight=dm4)

Here's a link to the bug : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)

---

### Post by gregalynch on 2010-12-26
i'm having the same issue with my new dm4t.  I went through the thread above and nothing worked.  the best I could do it to get right click to work, but then I lose the ability to scroll using the trackpad, as well as the ability to turn the trackpad off while typing.

---

### Post by ElSlunko on 2010-12-26
Try this. There are so many threads about the dm* touchpad. This fix worked the best for me.


> **uppertoe said:**
> Not sure it's been mentioned in this thread, but [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) has a nice bit of advice that worked for my hp 210.

Installing the package at 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167)

worked like a dream - no two finger scroll, but click and drag is working nicely; something I think is a little more important.

Still no physical right click, but I can do edge scrolling or two finger scrolling and best of all I don't have the wild cursor.

---

