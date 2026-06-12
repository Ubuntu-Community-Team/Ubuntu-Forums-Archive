---
title: "Vim Question"
date: 2012-01-13
forum: General Help
---

### Post by Jabrick on 2012-01-13
How can I transform all lines like

1239884 93
3249894 28
3489248 89

to a result like

1239884
3249894
3489248

in vim for all lines in the text?
Basically delete from a whitespace to the end of a line.
I see :%s/\s\+$//
Deletes all trailing with space.
Says \s searches from empty start and plus finds all occurences until ($) end of line.
But I don't know how to change so that
It finds whitespace and then deletes from the whitespace to end of line.

---

### Post by papibe on 2012-01-13
Try this:
```
:%s/\s\+.*$//
```
Notes:
- you need to escape '+' to give it special meaning.
- '.' means any character.

Hope it helps.
Regards.

---

