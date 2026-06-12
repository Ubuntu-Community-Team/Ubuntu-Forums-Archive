---
title: "Question about slowdown/video card/drivers"
date: 2006-02-16
forum: General Help
---

### Post by matts0344 on 2006-02-16
I'm new to Linux/Ubuntu and have a question. When looking at large pages in firefox and scrolling down fast the system kinda slows down (like CPU usage goes REALLY high), same if I even select a lot of icons really fast on the desktop.

Does this mean my video card (Radeon 9600) is not installed right or something, like its not running the effects in hard? Or is this normal?

If not, what should I do? I'm pretty sure the drivers were installed ok, the screen LOOKS great, its at a good resolution but this slowdown is kinda weird.

Thanks for any help you can give.

---

### Post by metafile on 2006-02-16
I`m not sure that web pages rendering depends on video card.
Firefox (such as most of the other browsers) always slows down when browsing pages with a lot of pictures or tables. Webmasters should use divs :)

---

### Post by dcstar on 2006-02-16
[QUOTE=matts0344]I'm new to Linux/Ubuntu and have a question. When looking at large pages in firefox and scrolling down fast the system kinda slows down (like CPU usage goes REALLY high), same if I even select a lot of icons really fast on the desktop.
.....
Thanks for any help you can give.[/QUOTE]
If you are using FF 1.0.7 I would recommend an immediate upgrade to 1.5 (do a search for the HOWTO).

Also check that video Direct Rendering is working with "glxinfo".

---

### Post by matts0344 on 2006-02-16
[QUOTE=dcstar]If you are using FF 1.0.7 I would recommend an immediate upgrade to 1.5 (do a search for the HOWTO).

Also check that video Direct Rendering is working with "glxinfo".[/QUOTE]

I am using FF 1.5 but I checked and Direct Rendering has a 'No' next to it. What does this mean I should do?

---

### Post by simon_is_learning on 2006-02-17
what is your screen resolution rate.

I had the same problem today, when I changed it - now the screen is more stable and it doesn't flicker.

Also this is interesting for me - because I saw an add that sold a Radeon 9600 for 250SEK about 30-35$. Have you had any problems with it?. I'm just curius.

If you would like to check if it's the resolution rate. 
nano /etc/X11/xorg.conf

find these lines:
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160

if your values is lower than mine - it is probobly a slow down in the system.

to change them:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by dcstar on 2006-02-17
[QUOTE=matts0344]I am using FF 1.5 but I checked and Direct Rendering has a 'No' next to it. What does this mean I should do?[/QUOTE]
You need to find if your particular video hardware can have this enabled - the video system will run a lot faster if it is.

Do a forum search for your video card (find out what it is with the "lshw" command - look in the "Display" section) and hopefully you will find a HOWTO on getting hardware acceleration/direct rendering (same thing!) going.

Try this: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

