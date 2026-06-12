---
title: "Windows key as application launcher stops working"
date: 2012-08-08
forum: General Help
---

### Post by Statia on 2012-08-08
I made my windows key start the Kickoff Application Launcher in KDE by putting a little script in ~/.kde/Autostart:

```
#!/bin/bash
xmodmap -e 'keycode 133=F13'

```However, it just stops working after some time and I have to manually run the script again to get it to work again. I noticed it stops working when I have switched to a virtual terminal, but it may have stopped on other occasions as well. Any ideas how to make this little hack more persistent?

---

### Post by Statia on 2012-08-29
And probably related: I have set the NumLock key to on, this will also switch off.

So what happens:

- NumLock switches off
- WinKey stops working

When does this happen:

- After switching to a VT
- After waking up from suspend

Just another bug, or is there a fix for this?

---

