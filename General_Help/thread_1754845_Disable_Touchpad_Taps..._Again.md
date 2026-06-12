---
title: "Disable Touchpad Taps... Again"
date: 2011-05-10
forum: General Help
---

### Post by Chrissd on 2011-05-10
Hi all,

Since Natty, new annoying features have been added to my touch pad. Somehow I can now scroll up and down the page using my palms as I type and can sometimes click as well. Playing about, if I use two fingers on the touch pad, I can scroll up and down the pages. 

I have already disabled the taps off my touch pad. I just want it to move the mouse, nothing else, no tapping, no scrolling, nothing but move the mouse. How can I please disable the new features added please? 

I used the following on startup to fix the taps last time.

```
synclient TapButton1=0
```

Thanks in advance.

---

### Post by Chrissd on 2011-05-13
Ok, now I've added the following to startup, which has stopped some of the random clicking:
```
synclient TapButton2=0
synclient TapButton3=0

```

But if I use two fingers on the touchpad then it still scrolls. Annoying side effects are if I use control and accidentally scroll, then it zooms in and out of pages.

Anyone tell me how to disable two finger touching of the touchpad please?

---

### Post by Chrissd on 2011-05-13
This is what I was after
```
synclient VertTwoFingerScroll=0
```

---

