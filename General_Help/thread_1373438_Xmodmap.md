---
title: "Xmodmap"
date: 2010-01-05
forum: General Help
---

### Post by VitaminCPP on 2010-01-05
I have 3 layouts: USA, Russian and Hebrew. In Hebrew the W key is mapped to apostrophe, so Ctrl+W in Hebrew layout doesn't close tabs in Firefox. There is no workaround for it as I see by now, so I am trying to get it work this way:

I want to map Ctrl+W in Hebrew layout(which is actually a Ctrl+') to be a Ctrl+w. Here is what I got from xmodmap:
```

$ xmodmap -pke | grep 25

keycode  25 = w W Cyrillic_tse Cyrillic_TSE apostrophe W

```

As you can see, there are pairs for each layout, each pair tells what happens without and with the Shift key pressed.

So what I want to know is, can I control keyboard behaviour with Ctrl modifier pressed or it is just about Shift?

Thanks.

---

### Post by VitaminCPP on 2010-01-06
bump...

---

### Post by VitaminCPP on 2010-01-06
nobody knows the answer?..

---

