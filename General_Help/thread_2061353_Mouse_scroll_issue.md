---
title: "Mouse scroll issue"
date: 2012-09-22
forum: General Help
---

### Post by Warprunner on 2012-09-22
I have an issue that is really driving me nuts. I have checked this with 3 different mice and it still does the same.
I am using 12.10 32 Bit

In Nautilus, using the middle scroll wheel, rotating the wheel forward scrolls up, conversely, rotating the wheel backwards or towards me, scrolls down. Thats what it always has done.

In any browser - Chrome-Firefox-Chromium-Opera.. it is just the opposite.

Anyone have a fix for this. It just started when I upgraded.

Thanks ahead of time!

---

### Post by mIXpRo on 2012-10-10
i have the same problem , ubuntu 12.10 beta 2

---

### Post by Warprunner on 2012-10-10
> **mIXpRo said:**
> i have the same problem , ubuntu 12.10 beta 2

Yeah for got to mention I have Beta 2 also.

BTW nice little riff in your sig!

---

### Post by mIXpRo on 2012-10-10
:p:p thakns .
it's phrygian scale

---

### Post by mIXpRo on 2012-10-13
bump ?!?!?

---

### Post by mardybear on 2012-10-14
Howdy....

Do any of these links help you out?

[http://askubuntu.com/questions/89231/mouse-scroll-wheel-is-in-a-direction-opposite-to-windows/89692#89692](http://askubuntu.com/questions/89231/mouse-scroll-wheel-is-in-a-direction-opposite-to-windows/89692#89692)

[http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu](http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu)

mardybear

---

### Post by mIXpRo on 2012-10-14
thanks a lot , it worked . with ‘.Xmodmap’

it was for me :
pointer = 1 2 3 5 4 6 7 8 9 10 11 12

i changed it to 
pointer = 1 2 3 4 5 6 7 8 9 10 11 12

and now it works fine thanks .

---

### Post by Warprunner on 2012-10-14
Didn't work for me. But now I am thinking I have 2 .Xmodmap's on the system. Will search and see.
Thank you by the way!

---

### Post by Warprunner on 2012-10-14
Exactly what happened is I had 2 of the files. All seems to be fine now!! 
Thank you all!!!!!!!!!!!!!

---

### Post by mardybear on 2012-10-14
> **Warprunner said:**
> Thank you all!!!!!!!!!!!!!

You are very welcome.

FYI: For whatever reason, i often find a google search to be more productive than a forum search to find Ubuntu/Linux solutions. Took about 5 seconds to find the two links provided.

Take care and have fun with Linux.

mardybear

---

