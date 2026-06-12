---
title: "Ubuntu wont boot up"
date: 2012-02-23
forum: General Help
---

### Post by louisgonick on 2012-02-23
Today I arrived home, I tried to boot Ubuntu up, the fist time I tried I was left on the blank purple screen for hours, the second time I was taken to a black screen with something like this on the top left corner: @>

Is something wrong with the partition, the hardware or ubuntu itself?

Any help is appreciated

---

### Post by Gremlinzzz on 2012-02-23
what kind of install
wubi
dual boot
if just ubuntu which one

---

### Post by louisgonick on 2012-02-23
> **Gremlinzzz said:**
> what kind of install
wubi
dual boot
if just ubuntu which one

I'm not quite sure, I still have windows. To install it I just booted up the live cd, and installed from there. I'm assuming dual boot.

---

### Post by Gremlinzzz on 2012-02-23
Windows still working and its ubuntu 11.10 just guessing

---

### Post by IWantFroyo on 2012-02-23
Has Windows updated?

Anyways, try hitting the "ESC" key right after your computer's manufacturer's screen. Don't hold, tap. It may take several tries, but you should be able to get to GRUB. You'll see a list of something like Ubuntu and then a long number (2.6.35.1.2). Go down several and try one with a non-current number.

If the old kernel lets you in, back up your data and come back here.

---

### Post by louisgonick on 2012-02-23
> **Gremlinzzz said:**
> Windows still working and its ubuntu 11.10 just guessing

Windows took slightly more time to boot up today, but its fine. Yes I have Oneiric

---

### Post by louisgonick on 2012-02-23
> **IWantFroyo said:**
> Has Windows updated?

Anyways, try hitting the "ESC" key right after your computer's manufacturer's screen. Don't hold, tap. It may take several tries, but you should be able to get to GRUB. You'll see a list of something like Ubuntu and then a long number (2.6.35.1.2). Go down several and try one with a non-current number.

If the old kernel lets you in, back up your data and come back here.

I think that by hitting ESC I will be taken to the BIOS. I get a purple screen with all my OSs to chose from, should I select "Previous Linux Verisions"

---

### Post by IWantFroyo on 2012-02-23
Sure. I've never seen that screen before, but it's worth a try.

It's supposed to look like something else, though (and I was referring to GRUB, not BIOS, that's why I said to hit the key after initial screen goes away).

---

### Post by louisgonick on 2012-02-23
> **IWantFroyo said:**
> Sure. I've never seen that screen before, but it's worth a try.

It's supposed to look like something else, though (and I was referring to GRUB, not BIOS, that's why I said to hit the key after initial screen goes away).

I managed to boot ubuntu up by choosing an option that started with 3 and ended with 12, the normal one ends in 15. 

Now that I checked that "purple screen" with all the OSs seems to be GRUB, it says that on the top.

---

### Post by louisgonick on 2012-02-23
Since I managed to get in ubuntu with the older kernel I already started backing up. What should I do next?

---

### Post by IWantFroyo on 2012-02-23
*facepalm* Fail on my part. Yeah, that's GRUB.

Anyways, now you can try updating. That should fix it.

---

### Post by louisgonick on 2012-02-23
> **IWantFroyo said:**
> *facepalm* Fail on my part. Yeah, that's GRUB.

Anyways, now you can try updating. That should fix it.

Just updated ubuntu. Now I have kernel 3.****.16. It booted up just fine.

Thanks

---

