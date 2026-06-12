---
title: "Cannot load Ubuntu desktop"
date: 2009-11-25
forum: General Help
---

### Post by admcptch on 2009-11-25
Hello all,

Long time lurker, first time poster here. This forum has gotten me through hang-ups in the past, but this current one has myself and a much more experienced Linux friend totally stumped.

I built a box over the summer for my grandparents, had it all set up with Jaunty and it was working great. I told them to bring it home over Thanksgiving and I would update it to Karmic and set it up so I could remote in to them if they had any other problems. So I told them to bring down the box/keyboard/mouse and I would just use one of our monitors here to start the updates. Well here is where the fun starts...

The box would post, get to the graphical login screen, and then it would not load the Ubuntu desktop. The little Ubuntu white loading circle popped up and it would just hang there. So I did some research, tried a few things I saw and nothing. X would not start, so I loaded into the safe kernel and tried to reconfigure it from there, this totally broke it, the graphical login screen would no longer show up. It turned into a bunch of random pixels and 'wingdings style' font across the top. This lovely masterpiece, I assume, is the remnants of the login screen. So I called up my friend and had him come over to see if we could figure anything out.

We used terminal to redo X11, reinstalled X multiple times, etc etc. We even threw in a simple vesa driver and that would not even load graphically. We also used terminal to update to Karmic the old fashioned way, in hopes that it would replace the messed up drivers or whatever was causing it to fail. Karmic updated successfully, but it still won't display video.

Our only guess is that the ATi drivers that I had installed originally for the video card is messing this all up. Any help or ideas at all would be appreciated. I'm really hoping that I can just plug this back in on their monitor and it will work, but I won't be able to test that for another 3 days and there really is no reason for it not to work with other monitors.

Thank you in advance. If you need me to clarify anything I can. I can't reproduce the early errors because we fixed them.

tl;dr -- X won't start for some unexplainable reason. No desktop.

---

### Post by BenAshton24 on 2009-11-25
Hmm, I can't really think of anything that you haven't tried yet, other than further X configuration and maybe trying some different drivers. 

Although I personally would just backup the files and do a fresh install, it's much better than upgrading anyway and hopefully it will fix your problems too :)

good luck
Ben.

---

### Post by admcptch on 2009-11-25
> **BenAshton24 said:**
> Hmm, I can't really think of anything that you haven't tried yet, other than further X configuration and maybe trying some different drivers. 

Although I personally would just backup the files and do a fresh install, it's much better than upgrading anyway and hopefully it will fix your problems too :)

good luck
Ben.

Thanks Ben. Doing a fresh install is what I was hoping I wouldn't have to do, but it my end up being the case.

---

