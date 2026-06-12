---
title: "vim: overwrite existing file with :w &lt;file&gt;"
date: 2011-11-06
forum: General Help
---

### Post by CryptKeeper777 on 2011-11-06
I've recently started using a temporary file to copy text between files in vim because copying to the system clipboard doesn't work:

- write lines 5 to 10 to a temporary file: ":5,12w /tmp/vimcp"
- insert copied lines in the other file: ":r /tmp/vimcp"

This works perfectly fine. The problem is that the second time I want to do this, the temporary file already exists, so I can't copy to it. Is there a way to modify the first command so that the temporary file is overwritten?

---

### Post by gmargo on 2011-11-06
If you follow the :write command with a !, then the file will be overwritten.
```

:5,12w! /tmp/vimcp

```See vim's internal help on the subject by typing ":help :write" (or simply ":h :w").

---

### Post by gmargo on 2011-11-06
There is a way to copy lines from a file into the system's clipboard.  You can yank text into the special register * (asterick).

To yank a range of lines in the clipboard (see ":help :yank" and ":help clipboard"):
```

:5,12y *

```And then paste them into a different window's vim:
```

"*p

```

---

### Post by CryptKeeper777 on 2011-11-06
:w! works. Actually I've tried this out before opening the thread, but I wrote ":w /tmp/vimcp!" instead of ":w! /tmp/vimpc"... I just found this out because there's a file vimcp! in /tmp... Stupid mistake.

> **gmargo said:**
> There is a way to copy lines from a file into the system's clipboard.  You can yank text into the special register * (asterick).

To yank a range of lines in the clipboard (see ":help :yank" and ":help clipboard"):
```

:5,12y *

```
That doesn't work. I get the following error: "E488: Trailing characters."

---

### Post by gmargo on 2011-11-06
> **CryptKeeper777 said:**
>  "E488: Trailing characters."

I believe you have only the **vim-tiny** package installed.  Ubuntu installs this version by default.

Drop everything and immediately install the **vim-gtk** package.  This is a full featured vim (including clipboard support). You'll be much happier.

---

### Post by CryptKeeper777 on 2011-11-06
Thanks for the tip. I removed vim-tiny and install vim-gtk, and now :5,7y* and "*p work. 

But with this command, I can't copy to the standard system clipboard, only between vim files. But I found the command "+y with which I can copy a selection to the standard system clipboard. 

How can I copy a range of lines, e.g. :5,7 to the standard system clipboard? I've tried out stuff like :5,7y+ and :5,7"+y but that doesn't work...

---

### Post by gmargo on 2011-11-06
> **CryptKeeper777 said:**
> :5,7y+ 

":5,7y +" needs a space between the y (short for yank) and the plus, assuming that's not just a typo.

You can also select text with the mouse.  And paste it with a middle-click.   ":help x11-selection" talks about the different buffers and methods.  Which method you use sort of depends on your destination.

---

### Post by CryptKeeper777 on 2011-11-06
> **gmargo said:**
> ":5,7y +" needs a space between the y (short for yank) and the plus, assuming that's not just a typo. 
I tried it out once again, with and without space between y and +. Actually, both methods work, the difference is that with space, there's no message displayed confirming the yanking (without space, a message like "3 lines yanked" is shown).

I thought it doesn't work because there was no confirmation message, so I didn't even try pasting the yanked line in another program.
> 
You can also select text with the mouse.  And paste it with a middle-click.   ":help x11-selection" talks about the different buffers and methods.  Which method you use sort of depends on your destination.
I usually don't use a mouse but the trackpad, so I don't have a middle button. But I found xclip with google. Using xclip would be another solution to the vim/clipboard problem, explained e.g. here [http://vim.wikia.com/wiki/GNU/Linux_clipboard_copy/paste_with_xclip](http://vim.wikia.com/wiki/GNU/Linux_clipboard_copy/paste_with_xclip). I haven't tried it out but I'll keep the link in case I'm not satisfied with the other solutions...

Thanks for all the answers! Problem solved.

---

