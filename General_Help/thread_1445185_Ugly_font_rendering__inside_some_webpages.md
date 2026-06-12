---
title: "Ugly font rendering  inside some webpages"
date: 2010-04-02
forum: General Help
---

### Post by Alpha UMa on 2010-04-02
This happens to me with any browser (tested: Firefox, Chrome and Opera) and DE (tested; Gnome, KDE, LXDE). While for the most part, the text is OK, some text looks quite messed up (please look at the attachment for an example).

By inspecting the affected pages, I fond that usually (maybe ever?) when the characters are garbled, _the font is Tahoma_.

Then I tested with The Gimp and its text tool: I choosed Tahoma and I tried to type something inside an image. Same issue. It seems to happens when the font size is 14 px or >= 17 px.

That's all I was able to find. Dunno what causes it and how to fix it.

---

### Post by lovinglinux on 2010-04-02
Try [this.]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-display-weird-fonts,-with-greenish-blue-shadows,-after-update--2")

---

### Post by Alpha UMa on 2010-04-03
Thank you. I followed the instructions, but they didn't fix the problem. The fonts were OK, but antialiased. I prefer not-antialiased fonts. 

Once I changed this ```
<edit mode="assign" name="antialias" >
<bool>true</bool>
``` back to false, Tahoma characters are ugly again.

---

### Post by Alpha UMa on 2010-04-03
:idea: I had an idea! I searched for Tahoma in Synaptic and I found this:
```

ttf-tahoma-replacement

```
that package was installed by Wine. Now I uninstalled "ttf-tahoma-replacement" and Firefox (as any other browser) now replaces Tahoma characters with other fonts.
This is not a fix, but at least I can see good rendered text.

---

