---
title: "Popup messages"
date: 2006-02-22
forum: General Help
---

### Post by Therrol on 2006-02-22
Is there a command that makes a simple popup message when I execute a command? I have installed a few programs on my parents computer (they are new to linux) and would like some programs to have one of those messages popup. Things like "Not finished yet" and other things. Is this possible?

---

### Post by heimo on 2006-02-22
I'm not sure what you're looking for, but run
```
zenity --info --text "Hello"
```
on command line and you'll get a popup window with text "Hello" and [ok] button.

---

