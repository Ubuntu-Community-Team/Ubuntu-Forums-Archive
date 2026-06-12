---
title: "Choppy YouTube Videos on 12.04"
date: 2012-06-04
forum: General Help
---

### Post by Kreeyon on 2012-06-04
Hi,

I have a Dell XPS M1330 with an Nvidia GPU.  Video playback on YouTube on both Firefox and Google Chrome is slow and choppy in all playback resolutions.

Playing HD content from MP4 files and straight from the DVD player works fine with no issues but YouTube does not.

I have tried both Nvidia drivers available in the restricted drivers section, I have tried disabling hardware acceleration with flash on Google chrome but nothing seems to work.

I'm running Ubuntu 12.04

---

### Post by wildmanne39 on 2012-06-04
Hi, try what is in this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

---

### Post by Kreeyon on 2012-06-05
Thanks,  this as made a little difference but I'm still getting choppy Video in full screen mode.

---

### Post by Kreeyon on 2012-06-05
Just realised that this choppy video playback is actually happening in all size windows on YouTube and not just full screen mode.

---

### Post by Erik1984 on 2012-06-05
In which format do you watch these videos: Flash or HTML5? HTML5 vids for me are sometimes choppy in the beginning but run fine after a few seconds.

---

### Post by Kreeyon on 2012-06-05
The videos are choppy in both HTML5 and Flash; which is making me think it's an Nvidia Driver issue, but I don't see how videos can play smooth when from a DVD or a local file but then not from YouTube?

---

### Post by wildmanne39 on 2012-06-05
Hi, I had video tearing caused by the nvidia driver, I changed to a different nvidia driver and it solved the issue.
Thanks

---

### Post by Kreeyon on 2012-06-05
I've tried all the available Nvidia Drivers in the additional drivers application and both display the same issues.

---

### Post by brainwash on 2012-06-05
You could install the Firefox extension [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/") to enable playback of Flash videos via a standalone media player like Totem or MPlayer instead of Adobe's Flash Player.

---

### Post by Alpha33 on 2013-04-24
Hi, You may download VLC Player and play Youtube videos without any trouble. This is how you can do it:


[LIST]
[*] All you need to do is go to youtube and copy the URL of the video that you want to watch.
[*]Open VLC Player and press ctrl + N. A new window for Network streaming will appear.
[*]Paste the URL of the video on the window and click "Play".
[*]Now the video will load itself in VLC and you can watch it in full screen mode by pressing "F" without any trouble.
[/LIST]

P.S. Sometimes VLC player might play choppy videos in full screen mode as well. 
[LIST]
[*]In order to remove the choppiness, just open VLC and press ctrl + P.The Preferences window will open.
[*] In the Preferences window, go to Input and Codecs. You will see it on the left side of the window.
[*]Then check the option "Use GPU accelerated decoding" under the Codecs section.
[*]Close VLC and reopen. You should be able to view the Full screen videos smoothly now.
[/LIST]

Good Luck :)

---

### Post by undrline on 2013-07-01
I found this, which helped me immensely:

[LIST=1]
[*][COLOR=#333333][FONT=arial]In address bar type in-- about: plugins  (I added a space, so that : p didn't turn into :p)[/FONT][/COLOR]
[*][COLOR=#333333][FONT=arial]On top right inside the windows click the +Details to reveal more info on all plugins[/FONT][/COLOR]
[*][COLOR=#333333][FONT=arial]Ctrl+F -- Search for the word "Pepper"
[/FONT][/COLOR][COLOR=#333333][FONT=arial]It should be one of the sub-items under Shockwave Flash saying something like this
C:\Users\USER\AppData\Local\Google\Chrom[/FONT][/COLOR][COLOR=#333333][FONT=arial]*e\Application\2X.X.XXXX.XX\PepperFlash\p[/FONT][/COLOR][COLOR=#333333][FONT=arial]*epflashplayer.dll[/FONT][/COLOR]
[*][COLOR=#333333][FONT=arial]It should have its own Disable hyperlink, Disable it.[/FONT][/COLOR]
[*][COLOR=#333333][FONT=arial]Exit out of all Chrome windows.  Wait a few seconds to make sure all the browser processes quit[/FONT][/COLOR]
[*][COLOR=#333333][FONT=arial]Restart Chromium[/FONT][/COLOR]
[/LIST]
[COLOR=#333333][FONT=arial]&#8203;If it doesn't work, you can always re-enable it the same way you disabled it.[/FONT][/COLOR]

---

