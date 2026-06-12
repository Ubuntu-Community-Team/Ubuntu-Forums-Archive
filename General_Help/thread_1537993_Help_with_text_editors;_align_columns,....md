---
title: "Help with text editors; align columns,..."
date: 2010-07-24
forum: General Help
---

### Post by phillyj on 2010-07-24
Hi all,
I'm really new to using linux. I had a list of words and their definitions but they weren't aligned nicely. Here is a sample:
```

abash   embarrass   
abate   subside or moderate
abbreviate      shorten
```I want it so that it looks like this:
```

abash           embarrass   
abate           subside or moderate
abbreviate      shorten

```I tried emacs and vim search and replace but it thinks the space is equal to 1 so that is not useful to replace. It won't say that the space between, e.g. abash and embarrass is 2 rather only 1. I don't get this stuff and the guides were of no use to me. Please help this noob.

Thanks

---

### Post by jpkotta on 2010-07-24
[http://www.emacswiki.org/emacs/AlignCommands](http://www.emacswiki.org/emacs/AlignCommands)

What I usually do is select the text and do M-x align-regexp RET SPACE RET.

---

### Post by phillyj on 2010-07-28
Ok, that did it for me. Seems I didn't understand how to mark the text properly in the first place.

However, there is another problem that occurred when I made the 2 columns. The 2nd column now has more words than the line can hold so it wraps around to the next line (theres are arrows on the terminal sides where this occurs). How can I move the text to properly align with the 2nd column?

---

### Post by jpkotta on 2010-07-30
> **phillyj said:**
> Ok, that did it for me. Seems I didn't understand how to mark the text properly in the first place.

However, there is another problem that occurred when I made the 2 columns. The 2nd column now has more words than the line can hold so it wraps around to the next line (theres are arrows on the terminal sides where this occurs). How can I move the text to properly align with the 2nd column?

The arrows mean that there isn't really a line break there; Emacs is just wrapping the line so it's all visible.  You can make it truncate the line instead with ```
(setq-default truncate-lines t)
``` This also only affects the display, and will not actually truncate the text of the file.

---

### Post by KeyserSoze93 on 2010-07-30
Run:

```

column -t words.txt

```

If it looks alright, direct the output to a new file.

If you can use vim, run:

```

:%!column -t

```

---

