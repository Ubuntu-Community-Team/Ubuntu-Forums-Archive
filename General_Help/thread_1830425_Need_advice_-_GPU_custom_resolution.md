---
title: "Need advice - GPU custom resolution"
date: 2011-08-21
forum: General Help
---

### Post by vmicovic on 2011-08-21
Hello,

i need help, right now have nVidia GPU which cannot setup custom resolution (because of HD Ready TV) because of closed drivers.
And want to change GPU to ATI, which model (max. 150e)?
I need experience who success setup custom resolution on HD ready TV (maybe nVidia?) on ATI?

thank you!

---

### Post by vmicovic on 2011-09-28
bump bump :)

---

### Post by papibe on 2011-09-28
Hi vmicovic,

Do you want to connect you computer to a HDTV? I've done that using an nvidia 9500 GT, and an ION system.

What model is your card?
What brand and model is your TV
Have you installed the Nvidia proprietary driver?

Regards.

---

### Post by vmicovic on 2011-09-28
Hi, thank you for answering.

Yes i wan that and i install proper driver (have all menu from nVidia).
GPU is geforce 9600
TV is LG 32LB76


tnx.

---

### Post by papibe on 2011-09-28
Have you tried [this]("https://help.ubuntu.com/community/NvidiaMultiMonitors") guide? Check the section 'Setting up Multi Head'.

Hope it helps,
Regards.

---

### Post by vmicovic on 2011-09-28
The problem is that i done that, all is ok except resolution on hd ready tv, i cannot setup custom (1804x1026) ...

---

### Post by papibe on 2011-09-28
> **vmicovic said:**
> ...i cannot setup custom (1804x1026) ...
That's an odd resolution. Is it the TV's default?

What others resolutions do appear on the field 'Resolution' (usually set to auto)? 

Could you open a terminal on the TV and run:
```
$ xrandr
```

Regards.

---

### Post by vmicovic on 2011-09-28
yes is odd, i use that in windows because my tv is HD READY and cannot get resolution on him 1920x1080 
Open windows cannot be in center ..

---

### Post by papibe on 2011-09-28
Are you sure your TV support that resolution?

In that sense a TV is not that different that a monitor, and just can be set to the resolutions that it supports.

May be you are suffering from another problem: [Overscan]("http://en.wikipedia.org/wiki/Overscan")

Are you missing the edges of your screen? Like the TV is zooming your signal, or that is cropping the image?

If so, then we need to solve the problem in another way.

Regards.

---

### Post by vmicovic on 2011-09-28
hmmm, yes that is the problem "missing the edges of your screen, Like the TV is zooming your signal"

i have problem like on this pic.
[IMG]http://upload.wikimedia.org/wikipedia/commons/0/07/Overscan_examples.svg[/IMG]
and it`s a little cutting, like red area on image ...

---

### Post by papibe on 2011-09-28
Ok, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the options is easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") article.

Tell us how it goes,
Regards.

---

### Post by vmicovic on 2011-09-29
oh man, all this years with nvidia GPU drivers i did not know for this option, in link which you give me. Probably because is look like he is inactive and i did not ever touch that! :)  now all is ok! thank you very much for opening my eyes! ;)    

 p.s: how to save this settings? when i restart X he back to old configuration ..


and now on login i got this many errrors in taskbar

---

### Post by papibe on 2011-09-29
:D Glad it's working for you now.
> **vmicovic said:**
> how to save this settings?
First, you have to run the Nvida X Server Settings as root:
```
$ gksudo nvidia-settings
```
Then select 'X Server Display COnfiguration' on the right. Then on the left press 'Save to X configuration File', and save the file.
> **vmicovic said:**
> i belive that he cannot decide which is primary display? :s
Yes, I have that issue too. It seems that the primary display (the one that get into text mode when you press Ctrl+Alt+F1), is predefined by hardware. What I did is to swap the monitor and TV cables, and problem solved.

Regards.

---

### Post by vmicovic on 2011-09-29
i setup that (with left screen and right) and do save and that`s ok, but this "overscan compensation" don`t want to save.

and please read my post again, i do little change, i got many many errors in taskbar all over the time :)

and primary monitor is this HDTV, you suggest to switch to smaller as primary? then all will be opening on him, right? :s

---

### Post by vmicovic on 2011-09-29
and i cannot use dual screen as one? (like in windows)
i have only twin and separate screens :/

---

### Post by RoyLongbottom on 2011-09-29
That TV has a natural resolution of 1366 x 768 and that might be the only option via a DVI/HDMI connection. A VGA connection might do VESA standard resolutions from 640 x 480 to 1360 x 768. These numbers are usually in the supplied manual.

---

