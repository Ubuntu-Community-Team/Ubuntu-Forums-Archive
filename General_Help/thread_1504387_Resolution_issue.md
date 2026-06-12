---
title: "Resolution issue"
date: 2010-06-07
forum: General Help
---

### Post by thedesk on 2010-06-07
I've been using Ubuntu as the only OS for about 2 months(duel'd with XP before) and haven't had any major issues till this morning. I'd been working on the computer and walked away. the only program I had running was amsn. when i got back I saw the screen starting to darken on it's way to the screen saver so i hit a couple random letters to keep it awake. The screen saver came up for about half a second then the unlock screen screen, so I typed in the password and after about 30 seconds(its instant usually) i had about 6 windows pop up on the task bar all titled unknown or unknown document i believe. the top of the window(above file and such) was totally black(its usually a pinkish) and i couldn't touch anything. the mouse would move but thats all I had. so i shut the computer down(manually as I couldn't do it on the computer).When i rebooted the resolution of everything is horrible, and allot bigger then before. It all seems distorted almost.  i checked it and the only options i have are 320x240 and 640x480. the bar holding all my shortcuts is all squished when normally its half empty. the system drop down is cutting half of the Firefox shortcut off. I'm using Ubuntu 8.04 LTS Desktop Edition. Thanks for any help you can give.

---

### Post by wannabegeek on 2010-06-07
Hi

Hopefully someone better qualified will comment on your issue.
I have however recently learned how to change resolutions when the driver for the video card is not providing all the known screen res options.

Check out this page. Try searching xrandr as well.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Basically, you use a program called cvt,  it automatically calculates a bunch of parameters used by xrandr. For a 1024x768  60 Hz
```
cvt 1024 768 60 
```
Then cut and paste everything after 'newmode'

You make a new mode, then add it. Finally, switch to that mode.
If the wiki doesn't make sense, I'll try  to help.

wbg

---

