---
title: "Mouse scroll wheel stalls"
date: 2010-03-17
forum: General Help
---

### Post by zippyut on 2010-03-17
Hello,

Can someone help me with my scroll wheel?  I've been able to get it installed and it does cause the window to move up and down, but it seems that it will only scroll about 3-4 times before getting stuck (the window doesn't scroll anymore).  If I stop scrolling and wait for a few seconds, the window will scroll again when I scroll the mouse.  I've tried running xev and viewing the output from the scroll wheel, and the window says it's receiving valid scroll commands as long as I scroll the wheel.  

It seems to me that the window gets a ton of scroll commands, but starts ignoring them after 3-4 go into the buffer.  It continues to ignore them until the buffer is flushed with no new commands.

Can anyone help me figure out why the window scroll bars only move a few times before getting stuck?  

Thanks!

---

