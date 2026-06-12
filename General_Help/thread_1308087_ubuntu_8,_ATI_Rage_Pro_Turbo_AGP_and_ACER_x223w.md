---
title: "ubuntu 8, ATI Rage Pro Turbo AGP and ACER x223w"
date: 2009-10-31
forum: General Help
---

### Post by kowalsky on 2009-10-31
hi all,
i just intalled linux ubuntu ver 8.04-3 and i noticed that the display looks awfull; it's not like i need top shape graphics from a 433 MHz machine with an old video card, nevertheless is there anything i can do to improve the situation?
The card is an ATI Rage Pro Turbo, the monitor is an LCD ACER x223w, the images have their edges doubled, tripled and currently i see one mouse cursor and 4 of it's ghosts fading to its right side.

thanks,
kowalsky

---

### Post by P4man on 2009-10-31
first of all disable all visual effects in preferences > appearance.
Then tell us what resolution you are using. Your monitor should be run at 1680x1050, and Im not sure your venerable videocard can even handle that?

---

### Post by kowalsky on 2009-10-31
thanks P4man,
i am quite surprised to say that my Rage video card seems to know about 1680x1050 (it is the last resolution a the top of the list), however it handles this very poorly.
The refresh rate is set at 60 Hz and rotation is set to normal.
What should happen when I click Detect Displays?

thanks, 
kowalsky

---

### Post by P4man on 2009-10-31
> **kowalsky said:**
> thanks P4man,
i am quite surprised to say that my Rage video card seems to know about 1680x1050 (it is the last resolution a the top of the list), however it handles this very poorly.

I wouldnt expect a decent image quality from that card at that resolution. Even for a modern videocard that resolution is too much to pass over an analogue VGA cable without visible quality loss (ghosting, blurriness,... ) Perhaps you got other driver related issues as well, but Id look on ebay for a dirt cheap replacement card with DVI.

> What should happen when I click Detect Displays?

Nothing I guess, if its already detected.

---

### Post by kowalsky on 2009-10-31
thanks a bunch P4man,
my last question - how do i drop to a shell outside the X window, from my distant memories I still recall one was able to shutdown the X window and work with the shell - that wouldn't have any ghosting, blurring ...

Thanks,
kowalsky

---

### Post by P4man on 2009-10-31
> **kowalsky said:**
> thanks a bunch P4man,
my last question - how do i drop to a shell outside the X window, from my distant memories I still recall one was able to shutdown the X window and work with the shell - that wouldn't have any ghosting, blurring ...

Thanks,
kowalsky

control+alt+f1 (or F2, F3,.. F6). To return to the gui control alt F7 (sometimes F8 or F9)

To stop X, you can type:
```
sudo /etc/init.d/gdm stop
```

replace stop with start to start it again.

---

