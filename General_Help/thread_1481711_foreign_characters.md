---
title: "foreign characters"
date: 2010-05-12
forum: General Help
---

### Post by 240r on 2010-05-12
Can't rename, move or delete files or folders that have a foreign character.
```

The file or folder /data/down/done/1999 Taraf de Ha&#65533;douks does not exist.
```

Kubuntu Karmic. Fails in konqueror and dolphin. What gives???

---

### Post by LoneWolfJack on 2010-05-13
put double quotes around your folder/file name.

---

### Post by dandnsmith on 2010-05-13
I don't know what the 'best' method is, but a couple of thoughts:

1. that odd character is a place-marker for any unshowable character (so is not unique). Putting quotes round a name with one or more of these in will not get the desired result.

2. I'd be using a terminal, so as to get to the command line. That means you can use any form of evasion you like to think of for the odd names - tab/esc completion, wild characters ...

3. for moves, drag and drop could get what you want, if your graphical browser supports it.

---

### Post by 240r on 2010-05-13
> **dandnsmith said:**
> I don't know what the 'best' method is, but a couple of thoughts:

1. that odd character is a place-marker for any unshowable character (so is not unique). Putting quotes round a name with one or more of these in will not get the desired result.

2. I'd be using a terminal, so as to get to the command line. That means you can use any form of evasion you like to think of for the odd names - tab/esc completion, wild characters ...

3. for moves, drag and drop could get what you want, if your graphical browser supports it.

Not sure what you mean by 2 but 1 and 3 failed.

---

### Post by dandnsmith on 2010-05-14
When you get to a command (terminal) prompt, depending on which 'shell' you're running, and how it has been configured, the tab or esc keys can expand a partial filename as far as is possible within the directory (it stops when there is more than one possible completion, and allows further characters to be typed before another attempt is made to use completion).

The wild cards can be used for name matching:
* will match any string (so you can use fred*smith to match freddavidsmith freddsmith and so on)
? will match any single character.

HTH

---

### Post by 240r on 2010-05-16
Ah. Thank you. The tab completion worked.

---

