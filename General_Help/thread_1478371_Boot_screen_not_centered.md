---
title: "Boot screen not centered"
date: 2010-05-09
forum: General Help
---

### Post by cguy on 2010-05-09
Kubuntu Lucid
Using the proprietary graphics driver
low-res Playmouth screen fixed with Startup Manager

The problem is that now the boot screen is not centered on the screen, but slightly shifted to the left.

How can I center it?
Thanks

---

### Post by Zorael on 2010-05-10
Is it only very slightly shifted to the left? It seems to me that the center of the logo image isn't at the middle of the kubuntu text, but rather in the middle when you include the *kubuntu gears*. So when the logo image gets centered, it looks off unless you factor in the gears. To illustrate, and imagine that © represents the kubuntu gears;
```
     |
     |
kubu | ntu©
     |
     |
```

If this is indeed the case then it's an error on the part of the logo image creator. I don't find it terribly unlikely that he just took the finished ubuntu image, which is probably padded to have ubuntu in the center, and prepended a k to it (removing the padding).

edit: While it seems unrelated to your issue, I filed [a bug](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/580571) for this.

---

### Post by cguy on 2010-05-11
It looks like this:
```

------------------------------
|                           /|
|                           /|
|                           /|
|          Kubuntu          /|
|                           /|
|                           /|
|                           /|
------------------------------

```
Where the slash is, there is a black line, as if the image was shifted using the monitor controls.

I have a button on the monitor, [Auto], which automatically adjusts the display properties, including the position of the image.
Well, I can't center the plymouth screen using that button.

---

### Post by cguy on 2010-05-27
bump!

---

### Post by cguy on 2010-05-28
The problem is deeper than the graphical boot.

The boot screen (plymouth disabled now) AND all my ttys are shifted to the left.

---

