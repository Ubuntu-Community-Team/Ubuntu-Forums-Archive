---
title: "Login Display Too Wide"
date: 2012-04-26
forum: General Help
---

### Post by jim_deadlock on 2012-04-26
I've just installed 12.04 and I have a problem that when I log out, the login screen display is set too wide for the screen so I can't see any of the input fields or anything. Is there a way to change the screen resolution for the login screen (or anything else I need to do to fix it)?

---

### Post by jim_deadlock on 2012-04-27
I'm still struggling with this, I tried putting this in xorg.conf

```
Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        SubSection "Display"
             Depth 24
             Virtual 1024 768
        EndSubSection
EndSection
```

... which fixed my login screen, but unfortunately my user desktop was restricted to 1024x768 (normal is 1920x1080). It's my only annoyance with 12.04 so far.

EDIT: I also tried removing lightdm and installing gdm, which resulted in a broken desktop so no joy there either.

---

### Post by techsupport on 2012-04-27
> **jim_deadlock said:**
> I'm still struggling with this, I tried putting this in xorg.conf

```
Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        SubSection "Display"
             Depth 24
             Virtual 1024 768
        EndSubSection
EndSection
```... which fixed my login screen, but unfortunately my user desktop was restricted to 1024x768 (normal is 1920x1080). It's my only annoyance with 12.04 so far.

EDIT: I also tried removing lightdm and installing gdm, which resulted in a broken desktop so no joy there either.

What kind of monitor are you using? How old is it? Maybe time to upgrade to a bigger flat screen maybe?

---

### Post by jim_deadlock on 2012-04-27
It's less than a year old. Please don't reply to any of my threads, if there was an ignore option on this forum I would apply it to you but unfortunately there isn't so I'm just asking you politely instead. Thanks.

---

### Post by jim_deadlock on 2012-04-28
Final bump. Anyone...?

---

### Post by eriklovlie on 2012-04-29
Bump. I see the same thing as the OP. Clearly this is an issue with the upgrade process. My monitor is a fairly new Dell widescreen LCD connected using DVI. The gdm (or whatever the login screen is called) resolution is too high most of the time, but weirdly it is correct sometimes. Same with the desktop resolution.

---

