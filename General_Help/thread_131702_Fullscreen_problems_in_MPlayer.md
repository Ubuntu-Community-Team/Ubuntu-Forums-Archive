---
title: "Fullscreen problems in MPlayer"
date: 2006-02-16
forum: General Help
---

### Post by rkakkar on 2006-02-16
For certain codecs, like RealPlayer or DivX files, the video size remains constant (original size) irrespective of whether i resize the window to double or make it full screen. Anyone else found this problem? Any possible solution?

---

### Post by soulestream on 2006-02-16
goto preferences and make sure you driver is set to use xv.

Although I don't think that will be codec specific.


soule

---

### Post by rkakkar on 2006-02-17
Okay will try (its on my home machine). Uncompressed avi files were being displayed properly in full screen mode. That's why I think it could possibly be a codec problem.

---

### Post by nanotube on 2006-02-17
i had a similar problem, before, but switching the video to xv from the default x11 solved it for me. so i think it should work for you too. (right click>preferences>video and choose xv.)

---

### Post by ubuntu27 on 2006-02-17
Go to PREFERENCES.
VIDEO TAB, select X11/xv and click on OK. Then restart Mplayer.  :)

---

### Post by CFMV on 2006-05-29
This worked for me instead of the change suggested here in preferences:

> 
*Originally Posted by **duminas***
Run this on the terminal (Applications > Accessories > Terminal):

echo "zoom=yes" >> ~/.mplayer/config

In case you're curious, that just appends "zoom=yes" (without quotes, of course) to the .mplayer/config file in your home directory. Should fix the issue--it fixed mine without using the vo=xv bit (which also spat that error you're mentioning).

Original thread here: [FullScreen MPlayer]("http://ubuntuforums.org/showthread.php?t=114583&highlight=mplayer+resize") (reply #6).

PS.
I know this thread is old but i just spent like 1hr trying to play a .bin video file and finally found this, thanks again Duminas!

---

### Post by tanari on 2006-06-11
when I choose XV, I see error message:
> Error opening/initializing the selected video_out (-vo) device

[I]ATI RADEON 8500SE
Duron 700 MHz[/I]

Don't know what to do :(

---

### Post by KillrBuckeye on 2006-06-15
Changing to xv worked for me in the standalone player to achieve video scaling, but it's not working for my Firefox plugin.  How can I make the MPlayer Firefox plugin scale videos to full screen as well?  Thanks.

EDIT:  Sorry, I'm an idiot.  I figured out 20 seconds after I posted that I could right-click and configure the video for the plugin.

---

