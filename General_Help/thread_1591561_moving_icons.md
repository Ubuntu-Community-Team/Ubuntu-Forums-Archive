---
title: "moving icons"
date: 2010-10-09
forum: General Help
---

### Post by agkq62 on 2010-10-09
Couple of weeks back I found a thread about moving the windows icons from the left to the right. Now I can't find it anywhere, brain fade.

Help please.

---

### Post by TeoBigusGeekus on 2010-10-09
If you mean the desktop icons, I think it can't be done.

---

### Post by Quackers on 2010-10-09
I'm not certain, but I think it may have been in the Sticky written by Philinux, which seems to have disappeared from the top of the page.
It's not a problem I've had so am unable to assist other than to say you could try the search function. Maybe use the maximize/minimize buttons as terms.

---

### Post by theanalyst on 2010-10-09
Try [this]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/"). Type
```
sudo gconf-editor
```
in terminal. It brings up the gconf-editor window, under apps>metacity>general scroll down to see button_layout. Change the value of the field to 
```
menu:maximize,minimize,close
```
Hope this was what you were looking for.

---

### Post by agkq62 on 2010-10-09
I have done this previously, something in Appearance/Themes. I think the sticky was what I was looking at, there was a warning about only doing it this way to avoid problems with future updates. Tried searching for the last 1/2 hour but found nothing hence the post.

Where has the sticky gone?

---

### Post by agkq62 on 2010-10-09
> **theanalyst said:**
> Try [this]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/"). Type
```
sudo gconf-editor
```in terminal. It brings up the gconf-editor window, under apps>metacity>general scroll down to see button_layout. Change the value of the field to 
```
menu:maximize,minimize,close
```Hope this was what you were looking for.

Thanks for that but I'm sure there was a warning in the thread, that I now can't find, about not doing it this way.

Am I right.

---

### Post by theanalyst on 2010-10-09
Well I personally use ubuntu tweak to tweak these settings, sorry if what I posted was wrong...

---

### Post by Quackers on 2010-10-09
> **theanalyst said:**
> Well I personally use ubuntu tweak to tweak these settings, sorry if what I posted was wrong...

That's where else I saw it. Ubuntu-tweak > Window Manager Settings. Well remembered sir :-)

---

### Post by agkq62 on 2010-10-09
Thanks all, I'll give Tweaks a try.

---

