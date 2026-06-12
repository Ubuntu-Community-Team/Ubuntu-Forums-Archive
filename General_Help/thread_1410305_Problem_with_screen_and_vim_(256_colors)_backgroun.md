---
title: "Problem with screen and vim (256 colors) background color rendering"
date: 2010-02-18
forum: General Help
---

### Post by Fanck on 2010-02-18
Hi,

Maybe someone can help me on that one. I'm using xterm/screen/vim, and set them up to 256 color mode. Everything went well, except when background color for the theme I choose is not black.

Here's the theme I use in this example:
[http://www.vim.org/scripts/script.php?script_id=2887](http://www.vim.org/scripts/script.php?script_id=2887)

Here's the situation: as long as I only use vim, the background is well rendered, meaning everything is grey in vim background. But when I try this with screen, the background is back to black, and only the text get some kind of highlight with the background color.

Here are the magical lines I added to screenrc:

```
term screen-256color
attrcolor b ".I"
# Tell screen how to set colors. AB = background, AF=foreground
termcapinfo xterm 'Co#256:AB=\E[48;5;%dm:AF=\E[38;5;%dm'
# Erase background with current bg color.  Not needed if TERM=screen-256color
defbce "on"
```Colors are well rendered in 256 color, I only have a problem with this background. Anyone knows how to 'fix' this?

Thanks in advance :)

---

### Post by gertin on 2010-09-22
I know this is an old thread, but I stumbled across it while googling for the exact same issue. Posting solution here as it might help others. :)

If you're attaching to an existing screen (which hasn't read 'defbce on' from ~/.screenrc yet) you have to do the following: C-a and type:
```
:bce on
```

Screen should now set the background color correctly.

---

### Post by naught101 on 2012-08-12
Thanks Gertin! works for me.

---

### Post by wildmanne39 on 2012-08-13
Old thread closed.

---

