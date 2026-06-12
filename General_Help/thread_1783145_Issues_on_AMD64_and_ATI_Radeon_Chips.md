---
title: "Issues on AMD64 and ATI Radeon Chips"
date: 2011-06-15
forum: General Help
---

### Post by blender3dartist on 2011-06-15
Lo, it's been a while. Just got a new computer, and the first thing I did was install ubuntu on it. Now I've been having a few problems.

The first would be the painfully slow frame-rate that the entire user interface seems to be running at. I checked my graphics drivers and have installed the CCC for ATI Radeon chipsets. It would appear that everything seems to be running at the proper speed (60 Hz), but the interface is just laggy. Imagine you're running a new Android phone, and you switch screens, and everything is nice and smooth. Now image that, but not as smooth (kind of like a video game running slowly). That's more or less what it looks like. (This behaviour appears when using the switch windows button in unity, or just moving around the windows in general.)
Any suggestions?

Also, this annoying window pops up every time I auto login, asking me to unlock my keychain. Is there any way to get it to stop asking me this?

Thanks in advance.

(Fun fact, I'm a long time lurker and apparently this is my first post ever. Yay.)

---

### Post by pqwoerituytrueiwoq on 2011-06-15
@ keyring
you can try making your wifi setting available to all users
or you can set the keyring password to null (blank/empty)
@video issue
```
lspci | grep VGA
```be nice to know the card/chip in question

---

### Post by blender3dartist on 2011-06-15
Right, mah bad.
This was the printout:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Barts PRO [ATI Radeon HD 6800 Series]

```

My card is specifically an ATI Radeon 6850.

---

