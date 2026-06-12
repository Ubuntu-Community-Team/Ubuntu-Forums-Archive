---
title: "Option to Enable mouse while typing in 11.10?"
date: 2011-11-01
forum: General Help
---

### Post by _glook on 2011-11-01
Hello,

For the life of me, I can't seem to find the option to allow the mouse to function while typing. The mouse works just fine when holding down ctrl, shift, or alt, but it completely stops responding when pressing any other key, such as "Space Bar" or "A", which is driving me nuts. Unfortunately, I've found nothing on Google.

I've searched "System Settings -> Input Devices" for anything, including the Keyboard, Mouse, and Touchpad tabs, and all of the subtabs. I also tried opening up synaptiks, but the option there for "Disable touchpad while typing" was already unchecked. Checking it didn't seem to do anything.

Thanks for your time!

---

### Post by tartalo on 2011-11-01
Helps?
[http://kubuntuforums.net/forums/index.php?topic=3118383.msg273206#msg273206](http://kubuntuforums.net/forums/index.php?topic=3118383.msg273206#msg273206)
EDIT: Didn't read your message properly, sorry.

---

### Post by _glook on 2011-11-02
Thanks, but unfortunately, no. The link provided seem to point me in the direction of the synaptiks thing I mentioned.

---

### Post by christopher.wortman on 2011-11-02
> **_glook said:**
> Hello,

For the life of me, I can't seem to find the option to allow the mouse to function while typing. The mouse works just fine when holding down ctrl, shift, or alt, but it completely stops responding when pressing any other key, such as "Space Bar" or "A", which is driving me nuts. Unfortunately, I've found nothing on Google.

I've searched "System Settings -> Input Devices" for anything, including the Keyboard, Mouse, and Touchpad tabs, and all of the subtabs. I also tried opening up synaptiks, but the option there for "Disable touchpad while typing" was already unchecked. Checking it didn't seem to do anything.

Thanks for your time!

Works fine here... try reinstalling Kubuntu. I hope you have your /home as a different partition, sounds like some wacky bug. Are you using proprietary 3D drivers? If so what card? If not, try installing them, and if it is the nvidia driver disable it and enable the other one and see if it fixes things or simply reinstall the graphics driver. Maybe something got screwed up on download.

---

### Post by _glook on 2011-11-02
> **christopher.wortman said:**
> Works fine here... try reinstalling Kubuntu. I hope you have your /home as a different partition, sounds like some wacky bug. Are you using proprietary 3D drivers? If so what card? If not, try installing them, and if it is the nvidia driver disable it and enable the other one and see if it fixes things or simply reinstall the graphics driver. Maybe something got screwed up on download.
I'll try and reinstall it when I get a chance, but this is a work computer, so I'll have to find some downtime between projects to do so.

As far as the driver, it is Nvidia, although when I look at the Additional Drivers, I see two proprietary drivers, one labelled "(version current) [recommended]" and one labelled "(post-release updates) (version current-updates)". I'll try activating the other one and see how that goes.

The really weird thing about all of this is that I actually do have a touchpad and the touchpad doesn't suffer from this issue: I can type as much as I want and the touchpad never stops or stalls. It's only affecting my mouse. That's why I assumed there was a separate option for just the mouse as opposed to the touchpad.

But judging from the replies, I guess I've run into some sort of bug :(.

---

### Post by _glook on 2011-11-02
The alternative driver didn't help, so I guess there's just some bizzare bug. Maybe it has to do with this being a Macbook Pro 6,2.

Kubuntu itself has had a lot of problems on this machine, so maybe it's time to go back to something else for a while until the company allows me a new machine. Overall, I really like Kubuntu, but there seems to be more hardware issues on it than Ubuntu, at least with my current setup.

Thanks for your help though!

---

### Post by _glook on 2011-11-09
> **christopher.wortman said:**
> Works fine here... try reinstalling Kubuntu. I hope you have your /home as a different partition, sounds like some wacky bug. Are you using proprietary 3D drivers? If so what card? If not, try installing them, and if it is the nvidia driver disable it and enable the other one and see if it fixes things or simply reinstall the graphics driver. Maybe something got screwed up on download.
So I took some time and downloaded the latest iso. The firs ttime I did this with the 11.04 iso, it wouldn't even load up the installer, so I had to use the non-GUI version, which may have been where my problems were. In addition, 11.10 bring back decent support for MacBookPro 6,2 so that may have partly to do with this as well (not to mention that the regular liveCD actually worked this time). Now I can happily type and navigate again!

Thanks for the help!

---

