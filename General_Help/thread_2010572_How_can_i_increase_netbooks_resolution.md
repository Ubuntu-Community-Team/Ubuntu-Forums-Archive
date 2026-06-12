---
title: "How can i increase netbooks resolution?"
date: 2012-06-25
forum: General Help
---

### Post by ubuntoneedhelp303 on 2012-06-25
When i had windows 7 installed on my net book i could increase the resolution by editing something in regedit im wondering if there is something like that in Linux (Ubuntu 12.04).
The highest resolution is 1024x600, I realy wanted to increase it to 1024x768. Please if anyone can help it would be appreciated.  :popcorn:  ALSO: I tried using newrez but my mouse keeps getting stuck in the original size of the screen. The creater made an alternate script called newrez-v but i couldn't find out how to use it.

                                                           
                                                                                                                    Thanks - :cool::cool::cool:

Newrez link:[http://http://gtk-apps.org/content/show.php/?content=134686](http://http://gtk-apps.org/content/show.php/?content=134686)

---

### Post by Derxst on 2012-06-25
Most netbooks have a native resolution of 1024x600. Depending on the model, I would imagine that you are already set to the highest resolution possible, unless you are attaching an external monitor.

---

### Post by ubuntoneedhelp303 on 2012-06-25
Yes i am but i just need to increase it to 1024x768 cause it's an well known resolution for full screen applications.

---

### Post by ubuntoneedhelp303 on 2012-06-25
Maybe ill get some help over night or tomorrow wish me luck. ):P

---

### Post by CaptainMark on 2012-06-26
but your netbook screen only has a vertical pixel count of 600, why increase the amount past what your screen is capable of displaying

---

### Post by Mark Phelps on 2012-06-26
> **ubuntoneedhelp303 said:**
> When i had windows 7 installed on my net book i could increase the resolution by editing something in regedit im wondering if there is something like that in Linux (Ubuntu 12.04).
IF your netbook really only does support 600 pixels vertical, then you were using some kind of virtual desktop that allowed for more pixels.

That is controlled by the video driver you are using, and MS Windows video drivers don't work in Linux.

---

### Post by insane_alien on 2012-06-26
> **Mark Phelps said:**
> IF your netbook really only does support 600 pixels vertical, then you were using some kind of virtual desktop that allowed for more pixels.

That is controlled by the video driver you are using, and MS Windows video drivers don't work in Linux.

actually it is possible to force some monitors(analogue in particular) to 'display' more than their native resolution. of course, this appears terrible because you end up missing lines out so nothing looks right.

native res is best.

---

### Post by idoitprone on 2012-06-26
> **insane_alien said:**
> actually it is possible to force some monitors(analogue in particular) to 'display' more than their native resolution. of course, this appears terrible because you end up missing lines out so nothing looks right.

native res is best.

that is what windows does. This is how manufacturers promote 1024x768 for netbooks through screen resizing

---

### Post by PhilGil on 2012-06-26
You may find [this thread]("http://ubuntuforums.org/showthread.php?t=1389533") helpful. There are scripts for enabling 1024x768 resolution in both panning mode and compressed mode.

The thread is a bit dated so I'm not sure how well the scripts will work with a modern Ubuntu version, but it's worth a try.

---

### Post by sudodus on 2012-06-26
> **Derxst said:**
> Most netbooks have a native resolution of 1024x600. Depending on the model, I would imagine that you are already set to the highest resolution possible, unless you are attaching an external monitor.
+1

You can certainly use an external monitor to get higher resolution. Send the video output ***only*** to the external screen, and I expect that the video chip and provide higher resolution than 1024x600.

---

### Post by ubuntoneedhelp303 on 2012-06-27
Thanks for all the help ill  might get Monitor or something.

---

### Post by silentstone on 2012-06-28
@ubuntoneedhelp303: Having the same 1024x600 max resolution on my netbook, I tried the **newrez-v** script, installing the prereqs of **vnc4server** and **gdm** along the way.  Once everything had been installed, running the newrez-v script automatically opened a vncserver x-session at a larger resolution. Moving the mouse to the top of the screen drops down a configuration dock for vnc, and right-clicking on the empty desktop gives an OpenBox-based application menu.  The colors were a little off once I opened a test program, but I don't care.  It was awesome!

Thank you for sharing that tip!  It's great to be able to play games without their windows running off screen.
[]("http://ubuntuforums.org/member.php?u=1678290")

---

