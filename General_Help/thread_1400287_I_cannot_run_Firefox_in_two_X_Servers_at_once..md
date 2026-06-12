---
title: "I cannot run Firefox in two X Servers at once."
date: 2010-02-06
forum: General Help
---

### Post by JamesPKing on 2010-02-06
I have two Nvidia 250 GTS cards, each with their own monitor and X Server. 

When I open Firefox for the first time in one of the X Servers it works fine, but as soon as I move over to the other screen/X Server to open another instance of Firefox I get the "Firefox is already running, but is not responding..." error. 

So, I can have as many Firefox windows as I like in X Server 0, but when I try to open one, at the same time, in X Server 1 I get that error.

Does anyone know how to fix this?

I am running in 64 bit if that helps.

---

### Post by n0dix on 2010-02-06
Try with other browser to discard a problem with xorg or video cards.

---

### Post by lovinglinux on 2010-02-06
Try this command:

```
firefox -P -no-remote
```

---

### Post by n0dix on 2010-02-06
> **lovinglinux said:**
> Try this command:

```
firefox -P -no-remote
```

I look for google but i won't imagine it were so simple.

---

### Post by JamesPKing on 2010-02-07
> **n0dix said:**
> Try with other browser to discard a problem with xorg or video cards.

Thanks, I will try this when I boot back into Ubuntu, are there any browsers you would recommend?

The problem is that when I try to open Firefox in another X Server, it can see the Firefox process that is all ready there, but as that one belongs to X Server 0, X Server 1 cannot interact with it, thus Firefox thinks it is unresponsive.

---

### Post by n0dix on 2010-02-07
You could try first the suggestion of @lovinglinux, and if isn't work try with google-chrome or opera.

---

### Post by JamesPKing on 2010-02-09
Thanks for your help, I have got it working by using that command, it allowed me to make a new profile, so one X Server uses default and the other uses a different profile.

---

