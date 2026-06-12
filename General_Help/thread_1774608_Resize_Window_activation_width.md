---
title: "Resize Window activation width?"
date: 2011-06-03
forum: General Help
---

### Post by windyweather on 2011-06-03
ubuntu 10.04
ubuntu 11.04

When resizing a window, the activation width is very narrow.
The mouse jitter makes it hard to put the cursor in the right place. It's ok in the corner, but along the edges it's too narrow.

I've looked around in ubuntu-tweak to find the setting and I don't see anything.

Anybody know the setting to change so that I can resize my windows without cramping my hand?

Thanks,
ww

---

### Post by belltown on 2011-06-09
> **windyweather said:**
> ubuntu 10.04
ubuntu 11.04

When resizing a window, the activation width is very narrow.
The mouse jitter makes it hard to put the cursor in the right place. It's ok in the corner, but along the edges it's too narrow.

I've looked around in ubuntu-tweak to find the setting and I don't see anything.

Anybody know the setting to change so that I can resize my windows without cramping my hand?

Thanks,
ww

```
gksudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
``````

<distance name="left_width" value="3"/>
<distance name="right_width" value="3"/>
<distance name="bottom_height" value="3"/>

```

---

