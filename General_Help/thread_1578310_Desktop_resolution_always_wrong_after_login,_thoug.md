---
title: "Desktop resolution always wrong after login, though correct in settings"
date: 2010-09-20
forum: General Help
---

### Post by zaqz on 2010-09-20
Xubuntu 10.04 (fresh install w/ updates), Radeon video card, radeon driver in use, no errors in Xorg.0.log. 

Seems everything's fine and dandy, but every time I log in to my desktop, the windows (like terminal) and fonts appear WAY too big (a lot bigger than in hardy, which this box was previously running). In display settings, the resolution is 1024x768 like I want it (optimal for my Compaq CRT screen), but somehow those windows and fonts appear larger than they should. The desktop background image comes on as huge but gets scaled back to a better, screen-fitting size (all this happens while the different parts of xfce are being loaded there). Still, those windows and fonts remain unchanged, unless I go to Xfce settings and there in Appearance change the font, NOT its size but for example from regular to **bold** or *italic*. Then the size gets "normalized". 

I just wonder what's going on here, and how to permanently fix this. As there's no longer a xorg.conf for me to tweak (or displayconfig-gtk), I don't know where to begin. It's obviously not a critical crash issue but still a recurring annoyance. I'd hate having to go change the font manually after every login, and a resolution of 1280x1024, which would definitely make the windows and fonts smaller, just doesn't look good at all in my case (much too small). I don't know if anything in my /home folder (preserved from hardy) could be causing this, since I was using 1024x768 previously too.

In display settings, the resolution range is all the way up to 1920x1200, which wasn't available in hardy, not that I would've used such high resolutions anyway. The first option (maybe this is what X is taking as default) on that resolution list is 1280x1024, so is it adjusting the windows and font sizes to that resolution, as opposed to my favored (and selected) 1024x768. If so, is there any way I could put that 1024x768 on top of that list? Now, the system in its infinite wisdom is guessing wrong when it chooses the resolution for my desktop.

---

### Post by zaqz on 2010-09-21
I poked around a little on my own, and at least there's a workaround now. If I go to Appearance and check the Custom DPI setting and give it some value (whatever looks good on screen), that appears to preserve the font size after login (no need to save the session, at least I don't). I still couldn't figure out what's causing the issue in the first place, but as long as this little tweak works, fine. As far as graphics issues after a lucid upgrade, I know I've gotten off pretty lightly here. 

Hope this helps others too. I won't mark this solved yet, since the underlying issue still remains. I wonder if anybody else with Xfce has encountered this in lucid.

---

