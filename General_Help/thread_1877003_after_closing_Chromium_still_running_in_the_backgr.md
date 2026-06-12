---
title: "after closing Chromium still running in the background"
date: 2011-11-07
forum: General Help
---

### Post by langmarp on 2011-11-07
after I close Chromium it has still several applications running in the background and I can not get rid of them, only individually, killing in the system monitor

any solution?

thanks!

---

### Post by TeoBigusGeekus on 2011-11-07
Open chromium from a terminal and post us any error messages you get after closing it.

---

### Post by ajgreeny on 2011-11-07
And while the terminal is open use command ```
ps aux | grep chromium
```which will show what is still running.

---

### Post by Rubykuby on 2011-11-07
Open chromium, go to preferences, go to "under the hood", look for "background apps" at the bottom of the page and unselect "Continue running background apps when Chromium is closed"

Sometimes, the terminal just isn't the answer ;)

---

### Post by langmarp on 2011-11-07
thanks for all of you, problem solved!

there were no error messages, but [Rubykuby]("http://ubuntuforums.org/member.php?u=1419069")'s solution has worked, which means it was not a major issue just my level of expertise :)

---

### Post by Hylas de Niall on 2011-11-07
I noticed that setting just last night, and wondered why it would default to keeping them running anyway?
Faster re-lauch in the same session maybe?

I'd love to know.

---

