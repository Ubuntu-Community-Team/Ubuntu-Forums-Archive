---
title: "Natty Bugs I Can't Find a Fix For"
date: 2011-05-17
forum: General Help
---

### Post by Hawk__0 on 2011-05-17
I ran the beta's of Natty, and then I wiped my HD and installed the official release.  I run 2 monitors as a giant desktop.  In the below screenshot are my 2 super annoying cosmetic bugs that I can't seem to find a fix for:

1. On my right panel, the clock/login name/volume etc widget is shifted over to the right of the screen, beyond view.

2. On the bottom corner of windows with a scale icon, it appears as an annoying block, covering whatever is there.  I get this on all applications, and in Empathy it covers part of the input box.

Are these bugs known? Is there a fix?  I can't stand them anymore!

---

### Post by Hawk__0 on 2011-05-17
bump

---

### Post by Hawk__0 on 2011-05-18
bump

---

### Post by uRock on 2011-05-18
Please wait until 24 hours of dormancy before bumping you thread.

Thanks,
uRock

---

### Post by mcduck on 2011-05-18
I can't say anything about the panel indicators being shifted to the right, but what comes to the block at the bottom right of the windows, that's not a bug, but instead a feature requested again and again by people who had troubles resizing windows. It's possible to disable it if you want to, just follow these instructions: [http://linuxo.com/content/how-disable-%E2%80%98resize-grip%E2%80%99-ubuntu-1104]("http://linuxo.com/content/how-disable-%E2%80%98resize-grip%E2%80%99-ubuntu-1104")

---

### Post by Hawk__0 on 2011-05-18
Thanks for the reply!

This is a feature? In chrome it covers the down arrow (not that I use it, it just seems odd to cover it up).  The link you posted unfortunately does not work :(

The panel widget thing is definitely shifted over.  Look again.  I'm missing my power button, my messaging widget thing, and part of my time/calendar are cut off.  I can attach another screenshot with both my panels if you like.  I have dual monitors, so the panel on the left is correct, but the panel on the right is pushed over.

---

### Post by mcduck on 2011-05-18
Sorry about the link, try this one: [http://m-l1nux.blogspot.com/2011/05/how-to-disable-resize-grip-in-ubuntu.html]("http://m-l1nux.blogspot.com/2011/05/how-to-disable-resize-grip-in-ubuntu.html")

Yes, it is a feature. Not a perfect implementation, I agree, but often requested and probably done as well as possible until Ubuntu moves to GTK3. The problem is just that GTK2 doesn't come with a resize grip area (unless the window also has a statusbar) so adding one to GTK2 applications doesn't always work that well, the program's user interfaces weren't designed to have such thing. 

(and yes, I did see that your panel widgets are shifted to the right. What I meant is that I don't know what could cause such thing so I can't help you with that one.)

---

### Post by Hawk__0 on 2011-05-18
I've made the changes, I assume I need to log out/in for them to take effect.

One thing I notice about my other problem with the panel is that it seems to shift a bit every time I lock and unlock my screen.

---

### Post by Larkspur on 2011-05-18
This is just a shot in the dark, but check Monitors to see if Ubuntu has wrongly detected the size of your screen by a small amount.

---

### Post by Hawk__0 on 2011-05-19
No, it's correct.  Nvidia settings and monitors both show 3840x1080 (2x 1080p monitors [1920x1080])

---

