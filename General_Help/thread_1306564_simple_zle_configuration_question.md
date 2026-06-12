---
title: "simple zle configuration question"
date: 2009-10-30
forum: General Help
---

### Post by cvp on 2009-10-30
To start off, please assume that I am retarded.

I like zsh. zsh is a pretty cool guy. The documentation for zsh is endless and extremely thorough, which can be good or bad. In this case, it's a bad thing.
I've been meaning to fix this minor little issue for a while, and I'm really just looking for a quick fix. I'll read through the entirety of the zsh documentation available when I have more time; now is not the time. So if anyone knows off-hand how I can fix these two minor things, you'll save me hours upon hours of reading through irrelevant documentation. This would be very much appreciated.

So, two things:
1) When I press the up arrow to edit the previous line, the cursor is placed at the beginning. I would like it to be at the end.
2) I edit my lines in vi-mode, and presently it starts in insert mode. I would like it to start in command mode.

Thanks!
-cvp

---

### Post by estragib on 2010-07-21
_**#1**_ works for me.

When I start a clean zsh -df and use *<up-arrow>* in either command or insert mode, the cursor is positioned at the end of the buffer. It could be that you have different ZLE widgets bound to those keys. By default, *up-line-or-history* and *down-line-or-history* should be bound, respectively.

Please check this with:

```
bindkey -M **main** "*<^V><up-arrow>*"
bindkey -M **vicmd** "*<^V><up-arrow>*"
```**Note**: By *<^V><up-arrow>*, I do mean actually hitting Ctrl-V followed by the up-arrow key. This should insert the text representation for that key between the quotation marks.

As for _**#2**_, this is a simple solution:

```
function zle-line-init () { zle -K vicmd; }
zle -N zle-line-init
```See [http://zsh.sourceforge.net/Doc/Release/Zsh-Line-Editor.html](http://zsh.sourceforge.net/Doc/Release/Zsh-Line-Editor.html) (18.5.1 Special Widgets) for more info.

---

