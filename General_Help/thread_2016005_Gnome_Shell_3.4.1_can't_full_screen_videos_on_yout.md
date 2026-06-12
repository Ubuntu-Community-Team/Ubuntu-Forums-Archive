---
title: "Gnome Shell 3.4.1 can't full screen videos on youtube or any other site"
date: 2012-07-03
forum: General Help
---

### Post by coldjeanz on 2012-07-03
Started happening about a week ago I can't pin point what might have done it. When I click on the full screen button for a video on just about any page it will just flicker and then not do anything. I switched over to Unity and it seems to work fine there (although it seems to be a bit glitchy as well) so this looks like a Gnome Shell specific problem. I tried disabling all extensions on Chrome but it still won't work. 

Okay I just tried all these sites with Firefox and there seems to be no issue so I believe this is a Chrome specific issue. What could be the problem then?

---

### Post by msammels on 2012-07-03
Hey!

Check out [this link](http://www.youtube.com/html5)... yeah, don't ask me - YouTube have been forcing it on random people it seems. if this isn't the trouble, let us know! :)

---

### Post by coldjeanz on 2012-07-03
Unfortunately I don't think that's it because it says I'm not enrolled in the HTML5 trial.

---

### Post by msammels on 2012-07-03
OK, so it's a Flash issue... where did you install Chrome from?

---

### Post by coldjeanz on 2012-07-03
Probably just from here

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

And yeah my first instinct is that it's a flash issue but I don't exactly know how to go about fixing it. Even though it doesn't do it on Unity, there still seems to be some issue going on. Whenever I go full screen on Unity it will lag for a second and when I exit full screen the same thing will happen. But on Gnome Shell it's so bad that I can't even get to full screen at all using Chrome. Really strange problem.

---

### Post by msammels on 2012-07-03
Well, that was going to be my suggestion. Have you tried uninstalling Chrome, purging, rebooting and reinstalling from the website? (USC versions of stuff can be dodgy).

---

### Post by coldjeanz on 2012-07-04
I haven't. When I have time I probably will so I guess I'll stick with Unity for the time being.

---

### Post by msammels on 2012-07-04
Wait, what? Are you saying that Chrome's built in Flash works in Unity... but not in GNOME3? If so, then you might want to try removing and purging gnome-shell, then reinstalling it...

---

### Post by Ohzed on 2012-07-04
have you tried it using Chromium or Firefox (and other browsers) from the USC yet?

---

### Post by coldjeanz on 2012-07-04
> **msammels said:**
> Wait, what? Are you saying that Chrome's built in Flash works in Unity... but not in GNOME3? If so, then you might want to try removing and purging gnome-shell, then reinstalling it...

I really think it's a Chrome problem. When I use Firefox everything is really smooth, if I click full screen there is no delay. It just goes straight to it and starts loading the video in HD. If I exit full screen there is no hiccup or anything.

With Chrome it's very jerky when I go into full screen or exit. Even though it's functional in Unity it still has some apparent issues.

---

### Post by msammels on 2012-07-04
Definitely sounds like a Chrome issue. Have you tried Chromium, like Ohzed suggested?

---

### Post by coldjeanz on 2012-07-04
I tried with Chromium and Midori both browsers work just fine. Chrome is the only one giving me fits and that's annoying because it's my favorite browser.

---

### Post by coldjeanz on 2012-07-04
I think I'm just going to switch over to Chromium instead of wasting any more time figuring it out. Browser seems to be nearly identical and all my extensions still work.

---

### Post by TCattitude on 2012-07-04
> **coldjeanz said:**
> Started happening about a week ago I can't pin point what might have done it. When I click on the full screen button for a video on just about any page it will just flicker and then not do anything. I switched over to Unity and it seems to work fine there (although it seems to be a bit glitchy as well) so this looks like a Gnome Shell specific problem. I tried disabling all extensions on Chrome but it still won't work. 

Okay I just tried all these sites with Firefox and there seems to be no issue so I believe this is a Chrome specific issue. What could be the problem then?

Same thing happen to me, Chrome and Gnome Shell too (lastest, via ppa).
Check answer by kovalexal here:
[http://askubuntu.com/questions/157437/videos-wont-go-into-full-screen](http://askubuntu.com/questions/157437/videos-wont-go-into-full-screen)
Disabling flash 11.3 and just let 11.2 enabled actually work for me. Videos can go fullscreen now.

---

### Post by coldjeanz on 2012-07-04
Awesome that was it, thanks a lot!

---

### Post by TCattitude on 2012-07-04
> **coldjeanz said:**
> Awesome that was it, thanks a lot!

You're welcome ;)

---

### Post by nikonian on 2012-07-07
This fix works a treat: thanks!

---

