---
title: "Webcam with Ubuntu 10.04 x64"
date: 2010-07-07
forum: General Help
---

### Post by energybeing on 2010-07-07
Hi I'm having problems getting two different webcams to work with a web browser with Ubuntu 10.04 x64 on two different machines.  Both machines are giving met the same exact problem more or less.  The webcams both work flawlessly with Cheese and VLC capture, but refuse to work with a web browser for Stickam/Tinychat.  Using a script that was posted another thread, I was able to get the webcams on both machines to work properly with Skype. 
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
Unfortunately this same script did not work with either "chromium-browser" or "firefox" inserted in place of skype.  With Stickam, I click to go live and get a black box where the video should be playing.  With Tinychat, I get a little flashing popup that reads: "Click 'Allow', 'Remember' and then
You clicked 'Close' without enabling your cam or mic."
The popup also contains the buttons "Try Again" and "Close".  
The webcam on my desktop is a Logitech Webcam C200 046d:0802 and the webcam on my netbook is the built in webcam for the Eee PC 1001P "13d3:5111 IMC Networks".  Any help would be greatly appreciated.

---

### Post by energybeing on 2010-07-07
> With Stickam, I click to go live and get a black box where the video should be playing. With Tinychat, I get a little flashing popup that reads: "Click 'Allow', 'Remember' and then
You clicked 'Close' without enabling your cam or mic."
The popup also contains the buttons "Try Again" and "Close". 
I figured I should clarify that the problems are identical with Firefox and Chromium.  Thanks again.

---

### Post by energybeing on 2010-07-07
bump

---

### Post by energybeing on 2010-07-07
Anyone help me please?  This is really frustrating.

---

### Post by energybeing on 2010-07-07
bump again  >.>

---

### Post by energybeing on 2010-07-07
bump

---

### Post by energybeing on 2010-07-07
bump

---

### Post by lockalidiot on 2010-07-07
Man, I'm sorry you are not getting the help you need. I personally have no idea how to fix this issue either. Although bumping a thread after every hour isn't probably the best idea...

I hope someone who is familiar with the subject comes in to help you out soon.

---

### Post by energybeing on 2010-07-07
Ah, thanks for the advice.  I'm new to using the forums as you can see.  I've never had to post a thread before as I've been able to google for all my problems in the past, usually ending up finding a thread on these forums with the answer that way.

---

### Post by energybeing on 2010-07-07
After a bit of googling around and looking some more on these wonderful forums, I have fixed my problem.  Here is the solution:
> === Bug in recent version of Adobe flash player ===

In Ubuntu Hardy you were used to be asked to grant permission to the website you were visiting to take control on your webcam (through some flash popup with the settings). It seems that recent versions of Adobe flash player (the updated ones for Intrepid and Jaunty since June 2009, at least, and probably before also) have a bug which doesn't ask the user to grant access to a site when visiting it. Like ustream.tv for streaming using your webcam, as example.

The workaround is to grant access to that website by default without attempting to ask you each time.

* You need to go to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

* Choose the "Website privacy settings" * Select the site from the list of visited websites. * click on the option "always allow" above the list.

You should see that the icon on the left of that site in the list changes from yellowish to green colour. That's it.

Try again visiting that website, ustream.tv in this example, and your webcam should be streaming again as it used to do back with Hardy.

Enjoy! 

---

