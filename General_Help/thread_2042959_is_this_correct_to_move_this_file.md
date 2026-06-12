---
title: "is this correct to move this file?"
date: 2012-08-15
forum: General Help
---

### Post by LLCoolJeff on 2012-08-15
Sorry if this is noobish but I have completely messed this up before and had to go looking for the files...

I am trying to move something from:

1.    "/home/computer/Pictures/Icons/icon.png"

--move to--

2. /usr/share/icons/hicolor/64x64/apps/icon.png

would this be the proper code:

```
$ sudo mv /home/computer/Pictures/Icons/icon.png /usr/share/icons/hicolor/64x64/apps/
```

if I am not mistaken, this will move it to the specified directory and keep the name icon.png correct? or have I gotten something wrong?

---

### Post by ajgreeny on 2012-08-15
Yes, that's correct.

Why do you have to do it?

---

### Post by ads52 on 2012-08-15
Perhaps for safety:

```

sudo mv **[COLOR="Red"]-i[/COLOR]** /home/computer/Pictures/Icons/icon.png \
        /usr/share/icons/hicolor/64x64/apps/

```

as *icon.png* is a pretty generic filename.

---

### Post by LLCoolJeff on 2012-08-15
> **ajgreeny said:**
> Yes, that's correct.

Why do you have to do it?

to make the icon appear on the launcher, having trouble with a direct filename for some reason... I have another thread that deals directly with the problem which I just solved.. But I am unsure why it finally worked lol

read here (after I make a post in a minute): [http://ubuntuforums.org/showthread.php?t=2042640](http://ubuntuforums.org/showthread.php?t=2042640)

---

### Post by LLCoolJeff on 2012-08-15
> **ads52 said:**
> Perhaps for safety:

```

sudo mv **[COLOR=Red]-i[/COLOR]** /home/computer/Pictures/Icons/icon.png \
        /usr/share/icons/hicolor/64x64/apps/

```as *icon.png* is a pretty generic filename.

thanks, my icon wasnt actually names icon.png I just said that so people wouldn't be confused. Thanks though

---

