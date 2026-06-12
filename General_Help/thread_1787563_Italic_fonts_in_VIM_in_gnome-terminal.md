---
title: "Italic fonts in VIM in gnome-terminal?"
date: 2011-06-21
forum: General Help
---

### Post by le_kommie on 2011-06-21
I'm struggling to make VIM to display italic fonts in gnome-terminal. They work when I use urxvt with the TERM set to urxvt-unicode, but no such luck with gnome-terminal.

So far I did the following in my attempts to make this work:

- installed ncurses-term to get tercaps for all terminals
- in .bashr added "export TERM=rxvt-unicode"

I had rxvt-unicode termcap installed in /lib/terminfo/r/ but missing in /usr/share/terminfo/r so I created symlinks there.

And still no italic fonts in VIM.

I searched the forums and google with no luck really.

Does anyone have any idea? I'm not really sure what I'm doing, I'm pretty much a noob in the linux world.[/CODE]

---

