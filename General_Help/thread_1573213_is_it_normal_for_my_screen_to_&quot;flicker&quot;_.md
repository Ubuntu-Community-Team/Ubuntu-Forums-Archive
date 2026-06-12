---
title: "is it normal* for my screen to &quot;flicker&quot; once in a while?"
date: 2010-09-12
forum: General Help
---

### Post by lue42x on 2010-09-12
Like .. part of the screen (in a horizontal lines way) goes fuzzy for a split second and then everything is noramal again for a while.  I have an Intel 4500 video card.  It seems to happen in the lower half of my screen more than the upper half.  I'm wondering if this is a hardware problem (weak monitor to computer connection in my laptop) or if its just normal with some laptops/computers using Ubuntu.  I just bought this laptop and it was a lot of money and I started school a week ago and so I'm quite worried if this ends up being a hardware thing.

---

### Post by Lukas666 on 2010-09-12
That is not normal. If it's not a laptop try to replace the video cable.

---

### Post by lue42x on 2010-09-12
Its a laptop. This is depressing ... I bought it from an online Ubuntu computer vendor so sending it back for a fix may be a hassle given that I am in school.  I will send them an email and see what they say.

---

### Post by Lukas666 on 2010-09-12
> **lue42x said:**
> Its a laptop. This is depressing ... I bought it from an online Ubuntu computer vendor so sending it back for a fix may be a hassle given that I am in school.  I will send them an email and see what they say.

Before you do that, try a Live-CD Ubuntu, use it for a while, if it runs fine your hardware is OK.

---

### Post by linuxusr50 on 2010-09-12
You might try setting your visual effects to none.  I have seen flickering caused by compiz demanding too much of the graphics card.

---

### Post by Sub101 on 2010-09-12
> **linuxusr50 said:**
> You might try setting your visual effects to none.  I have seen flickering caused by compiz demanding too much of the graphics card.

+1

Is it tending to flicker under a high load?

---

### Post by lue42x on 2010-09-12
oh snap I am using Compiz!  Just the coverflow app switcher ("shift switcher" is the official name i think).  I'll try turning that off and see how things are.  Hopefully that ends this madness!

Also I can try the live CD if I am still unsure.  Thanks for the suggestions, I will report back.


EDIT: I wonder if the computer taking screens captures of the open programs for shift switcher was making the screen flicker.

---

### Post by lue42x on 2010-09-12
Flickers are less frequent now (before it was getting to be like once every few minutes).  It happened once since turning off Shift Switcher in Compize Config.  It was a different kind of flicker this time though, it was the whole lower half of the screen.  I'm going to keep watching ... hopefully it was a fluke and never happens again

EDIT: turned off Expo as well.  Just flickered at bottom.  Sigh.  Gonna restart and see if that helps

---

### Post by lue42x on 2010-09-12
turned off all visual effects.  Flickering persists.  Guess I will have to contact the vendor.

---

### Post by Whisp3r on 2010-10-05
It's not a vendor issue, it's a Ubuntu issue.

This problem appeared in 10.04 and affects Intel graphics cards. I don't know if 10.10 will fix the issue; however, if you use 9.10 or earlier, the problem goes away. There is a launchpad bug thread for it.

---

