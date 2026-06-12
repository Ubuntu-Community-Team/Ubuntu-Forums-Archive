---
title: "screen resolution"
date: 2012-01-12
forum: General Help
---

### Post by aliboy on 2012-01-12
How do you change the resolution if the netbook max resolution is 1024x600 into 1024x768 or better. I tried a live Pinguy OS and was able to set the screen resolution into that size.

---

### Post by aliboy on 2012-01-12
I am using ubuntu 11.10

---

### Post by raja.genupula on 2012-01-12
open your system settings and look for monitors  and open .there will be a lost of resolutions from there you can change your monitor resolutions.

All the best.

---

### Post by xyzzyman on 2012-01-13
In pinguy os, was it scaling 1024x768 down to 1024x600, or were you able to 'push' the end of the screen with the mouse and scroll the additional 168 pixels?

---

### Post by aliboy on 2012-01-13
the whole screen became 1024x768 not the one that you'll move to the edge to see the remaining window. Its called JUPITER. is this possible with ubuntu 11.10? (see the attachment)

the weird thing is when I printscreen, the size of the picture is 1024x600

---

### Post by xyzzyman on 2012-01-13
You can always just install Jupiter:

```

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

```

If it's an Asus eeePC then also add:

```

sudo apt-get install jupiter-support-eee
```

1024x768 wouldn't make sense on a netbook as that's a 4:3 ratio and as far as I know, all netbooks are widescreen aspect-ratio's.

---

### Post by aliboy on 2012-01-13
i was able to install jupiter in ubuntu 11.10 then I set to 1024x768 but the mouse cant move to the bottom edge. (i think that's the edge of 1024x600 and it cant movethe mouse beyond it) any fix for this?

---

### Post by xyzzyman on 2012-01-14
[http://ubuntuforums.org/showthread.php?t=1170167](http://ubuntuforums.org/showthread.php?t=1170167)

---

### Post by aliboy on 2012-01-14
i was able to adjust the screen resolution using the code in that link but still same problem, the mouse pointer cant go in the area in excess of the 1024x600.

---

### Post by aliboy on 2012-01-15
how to resolve this issue??

---

