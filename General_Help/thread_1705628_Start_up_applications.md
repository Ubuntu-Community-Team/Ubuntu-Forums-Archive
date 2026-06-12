---
title: "Start up applications"
date: 2011-03-12
forum: General Help
---

### Post by UKBB on 2011-03-12
Google Chrome keeps dropping out of the start up applications program list. It was working fine for many months and all of the sudden it stopped and when I check the list it isn't there. I add it back to the list and perform a restart and it works but when I shut down the pc and turn it on later it's not there again. Is anyone else having an issue like this?

---

### Post by tredegar on 2011-03-12
> Is anyone else having an issue like this? 
Yes.

I run a number of scripts at startup. One disables the CapsLock and makes it just "Shift".

95% of the time it runs OK. Then it does not.

Putting a **sleep 10** in my script helps:```
#!/bin/bash
# Make Capslock act as Shift
sleep 10
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "add Shift = Caps_Lock"
touch ~/capslock_ran
```

In trying to speed up the boot sequence, ubuntu seem to have lost some stability.

I am running 10.04LTS

---

### Post by UKBB on 2011-03-13
Thanks for the reply and I can understand how it might be skipped if the have lost some stability by speeding up the boot process. But how does it get removed from my start up applications list?

---

### Post by tredegar on 2011-03-13
> But how does it get removed from my start up applications list?
Looks like I mis-read your post. Sorry. 

If it is no longer in the list, obviously you'll have to add it again. I have no idea how it got removed, but once you have re-added it, it should certainly stay there.

If you logout & back in rather than reboot, is it still there?
The scripts are kept in [B]~/.config/autostart
[/B]
Is there something strange about your install (wubi, virtual machine, installed to a USB stick, etc)?

---

### Post by UKBB on 2011-03-13
If I add it back and restart it is ok. When I power down and power back up it is gone. Nothing odd about the set up.

---

### Post by WlaadDyaab on 2011-03-13
> **UKBB said:**
> Google Chrome keeps dropping out of the start up applications program list. It was working fine for many months and all of the sudden it stopped and when I check the list it isn't there. I add it back to the list and perform a restart and it works but when I shut down the pc and turn it on later it's not there again. Is anyone else having an issue like this?

I have a problem with Google Chrome (on Ubuntu it's called Chromium) but not the same as yours

As you said, Chromium was also working fine for me for quite a long time until just about 2 or 3 days ago (I can't view YouTube properly)

Before 2 or 3 days ago was the time where a new plugin of Flash player had to be installed/updated. And problems started to happen to me...etc

So I downloaded another Internet browser

Applications > Ubuntu Software Centre > Internet (on Ubuntu Software Centre's box) > Web Browser > Seamonkey Navigator > Install

Where to find it?:-

Applications > Internet > Seamonkey

(My detailed explanation is not to offend anyone, but for people who are completely new to Linux, so they can also learn as we speak :) )

And after I've installed Flash player from [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)

I managed to play YouTube videos on Seamonkey but not on my favourite Internet browser Chromium :(

---

### Post by keesp on 2011-03-16
I have exactly the same problem that chromium keeps being removed from the startup applications. I renamed the corresponding file in /home/<username>/.config/autostart, and that seemed to do the trick. Another option could be to make a script that starts chromium browser and autostart this script instead.

---

### Post by UKBB on 2011-03-18
So far so good. It took me a minute to figure out how to find that directory since I didn't have hidden files showing but I got it. I sure wish I knew what was causing it to be removed in the first place.

Thanks!

---

### Post by crashme on 2011-03-19
Thanks for that, I had the same problem on a computer here starting a week or two ago. I can only assume that Chrome itself is deleting the autostart file after a recent update. I have no idea why it would do that. 

The fix was simple from a terminal:

mv ~/.config/autostart/google-chrome.desktop ~/.config/autostart/chrome-browser.desktop

---

