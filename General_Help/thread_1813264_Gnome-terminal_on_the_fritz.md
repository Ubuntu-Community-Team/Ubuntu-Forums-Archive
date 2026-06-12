---
title: "Gnome-terminal on the fritz"
date: 2011-07-27
forum: General Help
---

### Post by chellrose on 2011-07-27
My gnome-terminal is doing weird, random things with its commands.  I'll attempt to explain in more detail...

*Sometimes, when editing a previously entered command, the cursor will jump to a random position and I can't get it to go back to where I want it.  Even if I hit Return and try again, the same thing happens.  However, this doesn't happen _every time_ I try to use an old command.

E.g.: suppose I type
```

 xemacs /home/me/schoolfiles/math/algebra/Chapter8Practice.tex&

```After finishing that, I want to xemacs another file in the same directory, but I've already closed the first one.  So, I hit the up arrow in the shell, then use the back arrow to try to rename "Chapter8" to, e.g. "Test1".  However, the cursor does goofy things, and I might end up with
```

xemacs /home/mTest1oolfiles/math/alg/home/meebra/Chapter8Practice.tex&

```In the above example, my editing has jumped to a completely random place, _and_ a bit of the original text ("home/me") has been copied into a different spot.

Sometimes (especially when using Backspace), the cursor will jump back a bit so that I'm deleting text behind what I actually wanted to delete.  Sometimes the terminal treats this as it appears (usually nonsense), and other times it treats it as though I've actually deleted the text where I intended to - though that isn't what appears on the terminal.  And it doesn't happen with xemacs alone.

One other thing - if I accidentally misspell a command with the "&", that shell tab/window is closed. (example: ```
xemcas&
``` closes the shell)

Finally, I'm not sure how I'd go about filing a bug report on this, because I use the same versions of Ubuntu/GNOME (Ubuntu 10.04) on my home computer and I don't see this erratic behavior.

So... has anyone seen anything like this before, and is there a way to fix it?

Thanks :D

---

