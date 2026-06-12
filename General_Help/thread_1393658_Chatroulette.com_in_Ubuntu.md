---
title: "Chatroulette.com in Ubuntu"
date: 2010-01-29
forum: General Help
---

### Post by thomasboleyn on 2010-01-29
Hi there, has anyone got chatroulette.com working in Ubuntu karmic yet? The flash settings won't let me click on them, so I can't agree to letting it access my webcam and mic. 

Many thanks.

---

### Post by thomasboleyn on 2010-02-01
bump!

---

### Post by t4thfavor on 2010-02-01
I had that problem under an older flash, I recently updated it to the latest x64 on the adobe site, and I can now click on stuff. As for the website, I have no idea.

---

### Post by TeoBigusGeekus on 2010-02-06
Problem confirmed.
So many gifs to troll with but still no access to the site.

---

### Post by DemonDomen on 2010-02-13
Here you go: [http://sourceforge.net/projects/webcamstudio/](http://sourceforge.net/projects/webcamstudio/)

---

### Post by malegria on 2010-02-15
[FONT=Arial][SIZE=3]I have successfully gotten Chatroulette.com to work with my machine. Firstly, I am using Ubuntu 9.10 Karmic and a **[Creative Live! Video IM Ultra Webcam]("http://www.amazon.com/Creative-Labs-Video-Ultra-Webcam/dp/B001NEK0PC")**. 
1. Install WebcamStudio. The instructions for that are simple, and are** [here]("http://www.ws4gl.org/download/installing-on-ubuntu")**.
2. Use this **[webpage ]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html")**to set your Global Flash Settings to always allow access by Chatroulette.com
3. Bring WebcamStudio up before going to Chatroulette.com
4. First Click on "Sources" scroll down to "Webcams" and select your webcam (it should be detected).
5. Next a small window will appear. Click on "Source" and select "Start." At this point your webcam should turn on and show you an image of yourself!
6. Next open up a browser and go to chatroulette.com . It should be working now just fine!

If you want sound you'll have to configure that in your Sound Preferences as "Input." Also, I find Firefox really slows down with this flash website so I prefer using the *newest* Opera which works better for me.

Good luck![/SIZE][/FONT]

---

### Post by Satoru-san on 2010-02-15
it works for me. I dont know what the problem is, it asked me if It was OK for flash to use my webcam, I clicked yes, I dont have a webcam though.

[[IMG]http://imgur.com/SLwd8l.jpg[/IMG]](http://imgur.com/SLwd8.png)

---

### Post by malegria on 2010-02-15
Satoru-san, I think the issue arises ONLY when one does have a webcam. I was able to use it just fine without a webcam, but the flash issue came up when I plugged in my webcam.

---

### Post by hooraycom on 2010-02-18
hi guys, 
my webcam works out of the box, (acer crystal eye, via v4l2) but the start button doesn't appear.
i have my flash from here [http://ubuntuforums.org/showpost.php?p=8841633&postcount=18](http://ubuntuforums.org/showpost.php?p=8841633&postcount=18)
maybe it can help someone..
anybody experienced the start button failure? the upper bar only shows "Entering..." 
greets

---

### Post by xefialtis on 2010-02-22
I just heard about chatroulette and wanted to check it out...
Interesting, but I cannot get my camera to work either...
The Flash thing just doesn't seem to recognize /dev/video0, even though I can use a bunch of other, non-flash, items with the camera...
XawTV, etc, several chat programs, etc... but not Flash...
Is there a way to force Flash to see /dev/video0 and select it as the default device?
My camera is a D-Link DSB-C300, yes, older, but it works fine in other applications.
I am in a fresh and clean install of 9.10, and have Chrome, Opera, Epiphany, and FireFox installed, and all have the same problem.

Thanks for any insight...

---

### Post by Hieronymus Josch on 2010-02-27
I'm running 9.1 and installed WebcamStudio.  When I "start" my webcam I get the error "Device '/dev/video0' cannot capture at 352x288."  I've tried all of the resolutions and get the same result.  I'd love for this to work.  Anybody with similar issues?

---

### Post by Hieronymus Josch on 2010-02-27
I should add, I'm not having any problems with the flash interface on chatroulette.com but when I test my cam from their site, I just get crazy multi-colored lines and no video.

---

### Post by wiljaxon on 2010-02-28
Hello I got my webcam working in Firefox (although this applies to Opera, Konqueror etc by substituting the  application name as the last word):

Type this in your command-line console:

**env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox **

For Opera it would be:
[B]
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so opera[/B]

Worth a try for some types of webcam.

Will

---

### Post by TeoBigusGeekus on 2010-03-06
> **wiljaxon said:**
> Hello I got my webcam working in Firefox (although this applies to Opera, Konqueror etc by substituting the  application name as the last word):

Type this in your command-line console:

**env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox **

For Opera it would be:
[B]
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so opera[/B]

Worth a try for some types of webcam.

Will
No go for Creative Live Cam Vista.

---

### Post by jirah on 2010-03-06
Seriously, I am not one to judge, and the flash issue is serious as far as linux is concerned. But the only reason to use chatroullete is to see some perv wankin his yang on camera and to count how many next'x it took you to get there. That site has no redeeming qualities.

---

### Post by paulgault on 2010-05-16
I had the same problem where the flash setting were not letting me press the allow button to allow chatroulette.com access to the camera and microphone.

i sorted it out by using [this web page]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html") on the Adobe site to always allow access by Chatroulette.com

it now works fine.

---

### Post by Flawd on 2010-05-30
I was having the same problem, and I got the webcam to work by using the Flash settings on the Adobe site, but I'm not getting any text on the page. No chat text, or button text. Any ideas?

---

### Post by cal111 on 2010-06-01
Flawd - I have the same problem.

Could it be just a font issue?

Also I would prefer a better fix than having to change the settings all the time!

---

### Post by Zemblan on 2010-06-01
> **jirah said:**
>  the only reason to use chatroullete is to see some perv wankin his yang

If Ubuntu is ever to become mainstream then helping people to do that sort of thing as and when they please without having to fiddle with their flash setting and cam is one more step along the way.

---

### Post by knokkels on 2011-06-23
> **wiljaxon said:**
> Hello I got my webcam working in Firefox (although this applies to Opera, Konqueror etc by substituting the  application name as the last word):

Type this in your command-line console:

**env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox **

For Opera it would be:
[B]
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so opera[/B]

Worth a try for some types of webcam.

Will
Thanks Will! I was breaking my head over this but your suggestion worked :)

---

