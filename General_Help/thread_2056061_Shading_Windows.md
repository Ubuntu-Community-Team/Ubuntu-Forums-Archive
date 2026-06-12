---
title: "Shading Windows"
date: 2012-09-10
forum: General Help
---

### Post by rickm1945 on 2012-09-10
I tried out Lubuntu 12.04 and a feature it had was to roll-up a window and when you were ready to use that window again you could click on a minus sign in the upper right and it would open the window again I found this to be very useful. Is this available in Ubuntu 12.04 Unity? Just this one feature is almost worth the switch to Lubuntu.

---

### Post by cortman on 2012-09-10
[This thread]("http://ubuntuforums.org/archive/index.php/t-1908696.html") should help, especially effenberg0x0's responses.

---

### Post by rickm1945 on 2012-09-11
> **cortman said:**
> [This thread]("http://ubuntuforums.org/archive/index.php/t-1908696.html") should help, especially effenberg0x0's responses.
Thanks Cortman, I decided to install Ubuntu Tweak, and it worked very well. The new conf editor, was confusing as I didn't see GWD file under apps to edit. This was gconf-2. Ubuntu Tweak, work flaulessly.

---

### Post by cortman on 2012-09-11
Glad it's working.

> **rickm1945 said:**
>  This was gconf-2.

This is your problem- you need dconf. But you also need to install it-

```
sudo apt-get install dconf-tools
```

and open with

```
dconf-editor
```

But if you already have it working, great!

---

