---
title: "SCIM and pinyin prediction - how do I turn it off?"
date: 2009-09-13
forum: General Help
---

### Post by cfogelberg on 2009-09-13
Hello all,

I have been setting up SCIM for simplified Chinese character input, and I have it mostly working now. However, the pinyin prediction is driving me mad. How do I turn it off?

For example, I want to write the character &#25105;, whose pinyin is "wo" with a third tone mark over the "o". I'd be happy to type "wo" and then any number, but right now I have to type "w" and then 3. If I type "wo" then the &#25105; character disappears from the list of options :/

I have tried turning off "Allow incomplete pinyin", and turning on "Use tone" in SCIM Input Method Setup, but this hasn't helped (see attached image). TIA for any help you can offer!

Christo

---

### Post by Irihapeti on 2009-09-15
I'm not sure what is causing your scim-pinyin to behave like that. On my system, when I type "wo" I still see &#25105; as the first character in the list.

You could check the settings of the buttons on the small panel at the bottom of the screen. There are two buttons between the &#26234;&#33021;&#25340;&#38899; label and the 'moon' symbol. The default settings are &#20840; and &#20013;. If they are set to something else, this could be causing problems. 

If you want a more simple pinyin without prediction, then you could install scim-m17n and use either "zh-py" or "zh-tonepy". The latter requires you to type in the tone number before any characters become visible.

---

### Post by cfogelberg on 2009-09-15
> **Irihapeti said:**
> I'm not sure what is causing your scim-pinyin to behave like that. On my system, when I type "wo" I still see &#25105; as the first character in the list.

You could check the settings of the buttons on the small panel at the bottom of the screen. There are two buttons between the &#26234;&#33021;&#25340;&#38899; label and the 'moon' symbol. The default settings are &#20840; and &#20013;. If they are set to something else, this could be causing problems. 

If you want a more simple pinyin without prediction, then you could install scim-m17n and use either "zh-py" or "zh-tonepy". The latter requires you to type in the tone number before any characters become visible.

Ah, I think you've solved it!

Attached is a screen shot which showed it was set to traditional characters or something, which probably also explains why I didn't recognise so many of them... I didn't have the two buttons (&#20840; and &#20013;) or the &#26234;&#33021;&#25340;&#38899; label you talked about showing, which tipped me off.

Anyway, I still don't know why it was doing funny smart pinyin things but that problem seems to have just disappeared now that I've changed it to &#26234;&#33021;&#25340;&#38899; :)

Thanks heaps,
Christo

---

### Post by Irihapeti on 2009-09-15
Glad to know you've got it working.

Incidentally, cangjie, which you have showing in your latest screenshot, is something quite different from pinyin. I found a reference to it: [http://www.sungwh.freeserve.co.uk/methods/cangjie.htm](http://www.sungwh.freeserve.co.uk/methods/cangjie.htm)

---

