---
title: "question about wrapping in vim"
date: 2011-08-17
forum: General Help
---

### Post by ninjaaron on 2011-08-17
I know this isn't the vim forum, but I guess there are people here who know vim well.

Anyway, I've started using vim in the tty for creating prose (as opposed to code) without any distractions.  This works fairly well, but there is a problem with wrapping.  Obviously, having lines go all the way across the screen is difficult to read.  I need the text to wrap at somewhere around 70-80 characters.

I've tried doing this with the textwidth (tw) and wrapmargin (wm) options.  This works well within the buffer, but it creates line breaks, which is a pain if I want to move the text into a WYSIWYG editor or post it on my blog.

Is there a way to make the text wrap within the buffer at 72 characters without actually creating a line break?

---

### Post by ninjaaron on 2011-08-27
Asked on the vim boards.

The only way to do this is by creating an additional buffer vertical to the other with the command:```
:vnew
```

This command can also be given a number as an operator to set a specific size.  For example:```
:72vnew
```This command will create the new buffer that is exactly 72 characters across, which I find to be pretty good for reading.

In addition, one will probably want to use this command:```
:set lbr
``` It forces vim to keep words together when wrapping, as the default behaviour is to fill each line with characters.

I'm probably the only person in the world who cares about this, as I guess nobody else will be writing their thesis in vim.

---

