---
title: "Resolution problems with Lucid 64"
date: 2010-07-02
forum: General Help
---

### Post by warfacegod on 2010-07-02
I have Lucid 64 connected to my 27" TV with 4:3 aspect ratio via s-video from an nVidia NV4 GeForce 6200SE TurboCache 256 MB card using the 173 driver set at 800X600.

After hours (don't get on my case, this is the first time I've had hardware that would run well on a TV:p) and hours of tinkering I've gotten a feel for how to do this and have some pretty good results.

However, I have two problems.

.01 The display isn't quite filling the entire screen. It's leaving about a .25 inch black bar all the way around the screen. This is negligible and if I can't fix it with only minor adjustments then so be it. I can live with it.

.02 This one isn't so minor. Many of the Windows are opening with portions of themselves cut off of, usually, the bottom of the screen. This makes, among other things, getting to the Close button rather impossible.

I'll post some screenshots in a few minutes.

---

### Post by Chame_Wizard on 2010-07-02
In the terminal,try```
sudo aptitude -S 1440x900
```

---

### Post by warfacegod on 2010-07-02
Screenshots.

---

### Post by Vaphell on 2010-07-02
well, not all apps are well designed and they are taller than the 600px
simply alt-drag to move the pesky window to uncover its important bits

---

### Post by warfacegod on 2010-07-02
> **Chame_Wizard said:**
> In the terminal,try```
sudo aptitude -S 1440x900
```

I got this in the Terminal. I checked the Appearances Window and there was no change.

---

### Post by Leppie on 2010-07-02
have you checked your tv manual to see if 800*600 is a supported resolution?
and what kind of connection are you using? (s-video, hdmi, etc)

---

### Post by warfacegod on 2010-07-02
> **Leppie said:**
> have you checked your tv manual to see if 800*600 is a supported resolution?
and what kind of connection are you using? (s-video, hdmi, etc)

Hey, Leppie. Bumming around in my Threads I see:p.

It's a 4:3 TV capable of up to 1080i so I can only assume that 800X600 is supported. Don't have a manual and I'm not going to try and get it online either. I went through that last year. As far as I can tell there isn't one available online.

s-video (Mentioned that in my first post. Come on ,try and keep up:tongue:)

---

### Post by theozzlives on 2010-07-02
Ubuntu works best at 1024x768 or higher. If you check the system requirements, I think it's there. Windows 7 is the same.

---

### Post by warfacegod on 2010-07-02
It was originally at 1024X768 and the picture quality was horrendous. I tried everything I could think of at that resolution but in the end it just wasn't enough. Setting it to 800X600 gave me a substantial improvement in quality.

---

### Post by Leppie on 2010-07-02
you know i like to trash (and crash) your threads... :lolflag:

i've had similar issues with a wide screen tv... using different cables didn't resolve much.
if the box you've connected to the tv has hdmi, i'd say that's your best bet.

sorry, hadn't seen the connection thingie... must be the time of day... :mrgreen:

---

### Post by warfacegod on 2010-07-02
S-video is the best quality TV output I have on the computer. The TV itself has DVI but at the moment I obviously can't use it.

---

### Post by warfacegod on 2010-07-06
I've made *some* progress. I've switched back to 1024X768 and adjusted the Fonts DPI. The image is better than before but not as good as when I'm at 800X600. It's not a great solution and I'd much prefer getting the windows to display properly in 800X600 unless there's a way to force it to use a higher 4:3 resolution.

---

