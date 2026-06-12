---
title: "extremely slow internet"
date: 2010-09-11
forum: General Help
---

### Post by vitalys on 2010-09-11
I just downloaded Ubuntu 10.04. The FireFox was horribly slow, so I googled the problem and disabled ipv6. It became a bit faster but not that much. I still can't load yahoo page, it just times out.

I am running Vista on the same box and internet is perfectly fine there with any browser whether it's IE, chrome or firefox.

any ideas?

---

### Post by slooksterpsv on 2010-09-11
How are you connecting, wirelessly or wired? 32-bit or 64-bit? can you download google chrome - [http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by andymorton on 2010-09-11
Try Chromium (available in the software centre) It's a lot faster than Firefox.

---

### Post by vitalys on 2010-09-11
I am using 32-bit. I am connecting wirelessly.

---

### Post by wojox on 2010-09-11
Great [Firefox Tutorials]("http://firefox-tutorials.blogspot.com/")

You could also try opening a terminal and

```
gedit ~/.bashrc
```

Add this to the end of the file and restart Firefox

```
export MOZ_DISABLE_PANGO=1
```

---

### Post by vitalys on 2010-09-11
> **andymorton said:**
> Try Chromium (available in the software centre) It's a lot faster than Firefox.

thanks, I'll try.

---

