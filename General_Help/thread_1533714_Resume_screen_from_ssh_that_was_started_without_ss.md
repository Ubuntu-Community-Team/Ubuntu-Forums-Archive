---
title: "Resume screen from ssh that was started without ssh?"
date: 2010-07-18
forum: General Help
---

### Post by fizgig on 2010-07-18
Like the subject says, I was at my server and logged in directly and started screen.  I then started a command and detached the screen.

I then logged in remotely through ssh thinking I could resume the screen but when I try "screen -r", it says not screens to resume.  I see the screen process still running and when I do go back to the server directly (no ssh) I can resume the screen and things are running just fine.

Anyone know how to resume a screen remotely that wasn't started remotely?

---

### Post by gmargo on 2010-07-18
A plain "screen -r" will not detach someone else's connection, which in this case is your on-site connection.  Use "screen -d -r" to detach the other guy.  The screen(1) man page says that "screen -D -R" is the author's favorite.  The -d/-D and -r/-R variants do things slightly differently.

---

### Post by fizgig on 2010-07-18
That did the trick.  I hadn't done that before since I thought I had detached the screen previously.  Thanks

---

