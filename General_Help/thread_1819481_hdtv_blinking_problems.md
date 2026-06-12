---
title: "hdtv blinking problems"
date: 2011-08-06
forum: General Help
---

### Post by mj360 on 2011-08-06
hey anyone, hope y'all having a great day. but i been having a problem. i have for pc connect to my hdtv and sometimes it blinks alot. it like someone is changing the channel. it does it the most when i'm watch a video in movie player. i thought it was just movie player but it does it when vlc player too. oh and it does it too with the nvidia drive on way more. anyone can help me with this ?

---

### Post by SeijiSensei on 2011-08-06
The "blinking" only occurs when watching media content?  Or does it happen all the time, even when just using the desktop and ordinary applications?

What NVIDIA card do you have?  If you have a card more recent than an 8xxx model, you can use its "VDPAU" method to improve video processing.

Start by installing **smplayer** from the repositories.  Then go to Options > Preferences and click on the Video tab.  Choose VDPAU from the list of video drivers.  Does that work?  Does it help with the "blinking?"

Another option you might try first is using the NVIDIA X Server Settings application on your computer and try turning off or on "Sync to VBlank" under the "X Server XVideo Settings" option.  (This application is installed to your computer when you install the proprietary NVIDIA driver.)

---

### Post by mj360 on 2011-08-07
i have a nvida geforce 9200 the pc is acer aspire x1200. i remove the nvida drive. it's not blink so far but it will i no that, cause it been happening for a while. and yes it does blink the most when i'm watching a movie. what happen it. if the video is running in the background and i get on firefox it blink but if it's close it doesn't. now when i play a video it freezes alot now, damn go from one problem to another lol

oh and it's probably not the pc the problem. cause i use windows 7 on it and i have know problems with that. but i use ubuntu all the time, i just can't stay with windows for long lol

---

### Post by SeijiSensei on 2011-08-07
So did you try either of the solutions I suggested?  Did you re-install the NVIDIA driver and turn off (or on) "Sync to VBlank"?  What about using VDPAU?

---

### Post by mj360 on 2011-08-09
ok the Sync to VBlank is off now what's the vdpau ?

---

