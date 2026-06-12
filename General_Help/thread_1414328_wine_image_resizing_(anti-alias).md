---
title: "wine image resizing (anti-alias)"
date: 2010-02-23
forum: General Help
---

### Post by artheus on 2010-02-23
Hi!

I've got a Wine question.. I've searched around for this.. but have only found how to make wine fonts smoother with anti-aliasing.

But my problem is that Images, when they are resized in Wine applications they won't get resized smoothly, the images gets pixly and does not look good at all.. Good example of this is Spotify.

Cheers,
Artheus

---

### Post by tom4everitt on 2010-02-23
Not sure if you did this already, but an easy fix might be to use to newest wine instead of the standard one:

sudo apt-get remove wine
rm -rf ~/.wine (NOTE: This will remove all your wine settings and installations)

sudo apt-get install wine1.2
 
Spotify works a lot better for me at least with wine1.2 (which really is wine 1.1.37 or something like that). Not sure whether it will fix your image problem though.

---

### Post by artheus on 2010-02-24
I've already got the 1.1.37 (1.2) beta release. And I agree to that it works better with a lot of windows applications. Including Spotify.

But the image resize problem is still a problem.

//Artheus

---

### Post by tom4everitt on 2010-02-24
Okay. Best is probably to check with the wine team directly in that case...

[http://www.winehq.org/help/](http://www.winehq.org/help/)

---

### Post by artheus on 2010-02-24
Okay, thanks!

I am asking this in the Wine Forum.

Post url:
[http://forum.winehq.org/viewtopic.php?p=40227](http://forum.winehq.org/viewtopic.php?p=40227)

Cheers,
Artheus

---

