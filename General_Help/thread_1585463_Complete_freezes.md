---
title: "Complete freezes"
date: 2010-09-30
forum: General Help
---

### Post by Cephi on 2010-09-30
10.04.  It seems to happen only when I'm listening to Pandora -- but I'm listening to Pandora for most of the work day, so I can't be sure.  There'll be a sudden complete freeze, no response from mouse or keyboard whatsoever.  I have to do a hard shutdown.  I know it's a long shot to post such a vague problem, but I have no idea how to proceed.  I've had to switch to Windoze in the meantime, which is humiliating and depressing.

I tried using Firefox instead of Chrome, but the same problem occurred.  The freezes happen about once every three hours, but the frequency is inconstant.

Please help!

---

### Post by sikander3786 on 2010-09-30
Windows doesn't freeze on the same computer?

So far the only commonality is Pandora I think. You said it happens every 3 hours at least, so try to survive without Pandora for 4-5 hours and see if it really happens then.

Chrome/Firefox issue is ruled out but another commonality, Flash... What about that?

---

### Post by Cephi on 2010-09-30
> **sikander3786 said:**
> Windows doesn't freeze on the same computer?

So far the only commonality is Pandora I think. You said it happens every 3 hours at least, so try to survive without Pandora for 4-5 hours and see if it really happens then.

Chrome/Firefox issue is ruled out but another commonality, Flash... What about that?

Even though I usually am using Pandora, I have spent many hours on the machine without it, and it has never happened under those conditions.  I suspect it is something to do with Flash, but I don't know what to do about that suspicion.

And no, it doesn't happen under Windows, on the same machine :(

---

### Post by sikander3786 on 2010-09-30
Some very common flash issues/solutions are listed here. (courtesy of forum member lovinglinux)

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Too difficult to say what is causing that. Check the xorg and message logs from System > Administraton > Log File Viewer for something strange. Also try killing X by using Ctrl + Alt + Backspace when it hangs up and see if the hardware is freezing or it is only the X server.

If you don't have the Ctrl + Alt + Backspace combination enabled, you can enable it from System > Preferences > Keyboard > Layouts > Options > Key sequence to kill the X Server and tick the corresponding box.

---

### Post by Cephi on 2010-09-30
That website doesn't seem to list a relevantly similar problem, but I might try installing an older version of flash, or maybe replace it with gnash.

I'll try killing X next time it happens, thanks.

---

