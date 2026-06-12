---
title: "turn Caps Lock into Shift"
date: 2011-10-17
forum: General Help
---

### Post by cesera on 2011-10-17
I am running Lubuntu Oneric on an old eee-pc 701, and though it runs great, I am struggling with keyboard a little. Specifically I keep hitting Caps Lock when trying to use the left shift key. I have been trying to remap the caps_lock to shift, but don't seem to be able to so. Just to make sure: I am trying to turn the caps lock key into shift_L, so that I have two Shift_L keys, and it doesn't matter which one I hit.

Any pointers anyone? I have seen a lot of pointers on the internet but none seem to work. Currently I have done the following:

```
xmodmap -pke > /etc/xmodmaprc
```then add the following to rc.local;

```
xmodmap -e "clear Lock"
xmodmap /etc/xmodmaprc
```but it seems to have no effect.

---

### Post by polki@mac.com on 2012-03-01
I'd love to know the answer to this one as well.

---

### Post by Tiganjero on 2012-03-01
Go to ***System > Preferences > Keyboard***, open the ***Layouts*** tab and click the ***Layout Options*** button. In the ***Caps Lock key behaviour*** sub-menu select the option that suits you the best. Hope this helps!

Cheers,
George

---

### Post by polki@mac.com on 2012-03-02
Thanks for the tip Tiganjero, but this thread is tagged with **Lubuntu**. ;-)

---

