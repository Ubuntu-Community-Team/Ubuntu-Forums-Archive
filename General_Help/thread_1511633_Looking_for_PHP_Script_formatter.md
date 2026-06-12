---
title: "Looking for PHP Script formatter"
date: 2010-06-17
forum: General Help
---

### Post by Gordonisnz on 2010-06-17
Hi,

For those who are programmers - I have a utility in Windows XP, that can format (indent) PHP scripts, so that they look nice, & easily read.

I'm wondering, has Ubuntu / Linux got any utilities / processes that will also do this ?


I don't want to copy the files back to Windows, & format, & then copy them back to my Ubuntu Machine.

---

### Post by wojox on 2010-06-17
I use Gedit and the plugins and set it to View > Highlight Mode > Scripts > PHP

---

### Post by Gordonisnz on 2010-06-17
I've got the view part already - & its telling me the different meanings of text / PHP code.

& i've found the plugins area - But can see no "php format" option. (to auto-indent the lines)

Is there a way to "find" a new / not-yet-loaded plugin ?

Thank you...

---

### Post by wojox on 2010-06-17
Try:

```
sudo apt-get update; sudo apt-get install gedit-plugins
```

---

### Post by Barrucadu on 2010-06-17
I believe `indent` is the program you're looking for, though I've never used it.

---

### Post by indytim on 2010-06-17
For GEdit:

Preferences -> Editor -> Enable Automatic Indentation

I use gedit exclusively for all of my php editing.

:p

IndyTim / DataMan

---

