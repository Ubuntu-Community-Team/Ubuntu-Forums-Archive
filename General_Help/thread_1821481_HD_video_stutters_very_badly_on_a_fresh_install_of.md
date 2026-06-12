---
title: "HD video stutters very badly on a fresh install of 10.04 LTS on laptop"
date: 2011-08-09
forum: General Help
---

### Post by viktor- on 2011-08-09
Hi everyone. I'm having some troubles playing hd videos (720p) on my laptop with ubuntu 10.04 installed. 

I have a dell inspiron 1720 with 4gb ram, dualcore 2,5ghz and a gforce 8600m card so it shouldnt have problem with playback.

I have installed restricted extra package and activated the nvidia driver from the additional driver menu. I have tried using both firefox and chrome for hd youtube content and both media player and vlc for 720p files on my harddrive. All of the above perform horribly (~1 fps). Low definition videos plays smoothly though.

If anyone has any ideas it would be greatly appreciated.

Thanks
/Viktor

---

### Post by 73ckn797 on 2011-08-09
See if installing the files from here might help:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mikewhatever on 2011-08-09
Flash is known to cause these problems on Linux. Do you use a 64bit or 32bit OS? Which version of flashplayer do you use?
As for the files on the hard drive, what are they? Downloaded .flvs or something else?

---

### Post by viktor- on 2011-08-09
Thanks for the replies.

I'm using a 32-bit OS and the flash plugin that came with restricted extra, i.e adobe flash plugin vesrion 10. The downloaded files I've tried are .mkv files.

I installed the Medieubuntu packages as well but no difference.

---

### Post by mikewhatever on 2011-08-09
I don't have any suggestions on playing the p720 flash videos, theoretically, you should be OK playing them, but in practice, flash on linux is extremely frustrating.
VLC lets you choose output modules under advanced video settings. Try gl or gl2 instead of the default one.
Personally, I've had better luck playing HD content with mplayer. It has gtk and QT GUIs as well - gnome-mplayer and smplayer.

---

### Post by drewsus on 2011-08-09
Get the Firefox Flash-Aid addon and run the Wizard. It has an option (that is checked by default) to "Override GPU Validation (improves preformance and solves fullscreen issues)" and another to "Enable Linux HWVideo Decode (allows flash to use vdpau hardware acceleration)"

HD Flash works fine on my box and yours is more robust. Also, maybe let the video load first.

---

### Post by viktor- on 2011-08-09
Thanks for the replies guys but nothing seems to work. I even tried updating to 10.10 but no improvement.

If anyone has any other ideas I would be really grateful.

---

### Post by mc4man on 2011-08-10
You might want to see if lowering the up_threshold on the default ondemand cpu freq scaling  mode helps.
The kernel default of 95  is quite high and may be keeping your cpu(s) at the lowest/lower freq. while playing these videos

It's pretty easy to modify the ondemand script, though worth testing first to see if it does provide any benefit

You can r. click on your gnome panel and add an applet, -  add 2 instances of the cpu freq. one, (no longer use gnome-panel so don't remember exact name
After adding r. click on one of the panel applets, (settings, or pref.'s) and change it to cpu1, so you have 1 applet for each cpu.
Then thru the r. click set each one to 'performance' and try your vid again in vlc or whatever.

If need be I'll give you instr.'s on how to lower the threshold for ondemand thru the ondemand script.

(probably starting in 11.04 vlc will do multi-thread decoding of h.264 which also provides benefit
(or a self built vlc statically linked to a recent ffmpeg

---

### Post by viktor- on 2011-08-12
Thanks all for the different ideas. I've managed magically to get it working decently, though I have no idea what was causing the trouble.

---

