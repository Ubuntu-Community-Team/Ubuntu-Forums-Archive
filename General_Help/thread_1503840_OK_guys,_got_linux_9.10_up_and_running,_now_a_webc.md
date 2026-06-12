---
title: "OK guys, got linux 9.10 up and running, now a webcam issue"
date: 2010-06-07
forum: General Help
---

### Post by Manuwash on 2010-06-07
So yeah, I just downloaded ubuntu 9.10 and forgot about the whole ati card conflict with 10.4. Now it&#347; working mostly flawlessly, thanks god after so many attempts and hours trying.:popcorn:

Now I got only a small issue that I am sure must be easy to work around. Ive been trying to do some video conference with my girlfriend, so far I tried empathy, pidgin and skype. On the first 2 apps I cant get any of the video/audio options, they are greyed out ( I did configure the plugins on pidgin to no avail). On skype i've been able to see my GF and to have audio chat, but my video is not working. 

I can get my cam working on cheese, so the cam is detected and functional ( nevermind I did the audio chat with the cam's mic). But for some reason I can't get it to work with the messenger apps. 

Any ideas?

---

### Post by LowSky on 2010-06-07
Take a look at this tutorial, it may help
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by Manuwash on 2010-06-07
thanks a lot, found something that gets me the cam working on the test option in the preferences, hopefully it will work when my gf logs in, btw do I always have to open skype from the terminal for this to work?

---

### Post by Manuwash on 2010-06-08
Hey so far it&#347; been going well with skype and the webcam as long as i start skype from the terminal with this command "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype". Which is not so much of a problem but it would be nice that I could just add that command somewhere so I could just open skype directly from my cairo dock.

Also for some reason it seems when I open skype from the terminal my conky shuts down. I start conky with the command "conky & disown" so that when I close the terminal it doesn't shut down. Im a noob with these things so, is there another way to open conky to make sure it stays open?

And finally, I wanted to bump this thread to see if anyone knows how to ungrey the pidgin video option, because if my cam is working with skype and cheese it should work with pidgin too, i prefer to chat by msn or yahoo than skype tbh.

Thanks a lot.

---

