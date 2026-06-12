---
title: "Weird Display Colors on 10.04"
date: 2010-04-29
forum: General Help
---

### Post by drkrffxx on 2010-04-29
Hey, I'm new here and kinda new to Ubuntu.

I just installed Ubuntu 10.04 x64 and I'm just testing it out and I found a very annoying problem.

I have a 24" LG display plugged into a nVvidia 9400GT and I found the colors being too... too... I don't know the exact word to describe them, it's like if the Digital Vibrance was cranked up to the max (those with nVidia cards know what I'm talking about), reds and greens are fugly, I checked the settings under nVidia CP and DV was turned off, I have no problems with this under Win7 where the colors are shown very natural.

I have installed the latest driver and I'm wondering if there is any color profile or something else I could tweak.

Any help will be greatly appreciated as this is spoiling my first Ubuntu experience.

---

### Post by attadaved on 2010-04-30
Facing almost a similar problem on my ASUS M5VM Laptop display with ubuntu 10.04. Seems digital vibrance is cranked up.

Any solutions??

---

### Post by drkrffxx on 2010-04-30
I might as well bump it as I found another display issue.

Whenever I click on the + button in Firefox to open up a new tab the whole display becomes brighter, washed out, to give you an idea of what the problem is, the top black menu bar becomes grayish and so on, that's until I go to any website, the colors come back to the normal brightness setting, I mean, when the new tab is a blank the whole screen becomes grayish.

The same happens on Chrome when I click on the new tab button, but it just last a split second while it loads the new tab then it goes back to normal.

Ah oh, and I can't use the quick reply box, is that normal?

---

### Post by dino99 on 2010-04-30
you should have nvidia-current activated into system --> admin --> hardware driver, and good resolution.

into synaptic: nvidia-settings and nvidia-current-modaliases have to be installed too

into system admin nvidia settings you tweak as you want

---

### Post by drkrffxx on 2010-04-30
I already done that before (Installed the proprietary drivers and played around with the nv panel). I can't tweak anything, nothing corrects the issue, no gamma nor brightness setting correct the color display, and the digital vibrance is set to 0.00, and the resolution is set to the max my display can handle 1920x1080@60hz but I think that's not the issue.

This is how I see the colors on my display (look at the color bars):

[IMG]http://www.w7forums.com/attachments/384d1247162522-digital-vibrance-dv2.jpg[/IMG]


It's disturbing. It's like the DV was turned all the way up like I stated before.

---

### Post by edyeeh on 2010-05-06
I have the same problem ever since I installed the latest video driver. I think it was 195*. Some of the colors look washed out. I can see it in pictures, movies, and in the transparency effects. Don't know what's wrong.

---

### Post by edyeeh on 2010-05-16
*bump*

anyone found a solution to this problem? even with nvidia settings' digital sharpening at 0, the screen still looks to sharp

---

