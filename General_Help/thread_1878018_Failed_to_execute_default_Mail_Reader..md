---
title: "Failed to execute default Mail Reader."
date: 2011-11-09
forum: General Help
---

### Post by subehsharma on 2011-11-09
In Chrome/Chromium, when i click on "Send to" link in certain websites, i get this message:

Failed to execute default Mail Reader.
Failed to execute child process "/usr/lib/i386-linux-gnu/xfce4/exo-1/exo-compose-mail-1" (No such file or directory).


While the same page on firefox correctly opens Thunderbird. Any idea?

---

### Post by Toz on 2011-11-09
In Settings Manager -> Preferred Applications, do you have a default mail client specified?

Also, do you have **libexo-1-0** installed?

---

### Post by subehsharma on 2011-11-09
> **Toz said:**
> In Settings Manager -> Preferred Applications, do you have a default mail client specified?

Also, do you have **libexo-1-0** installed?

Yes, both things that you asked are already present.

---

### Post by LewisTM on 2011-11-09
This happens to me too, most likely a bug for 64-bit systems.
XFCE is trying to find a library in the i386 architecture directories and it's not there.

Here's a fix. Run this command in a terminal.
```
sudo ln -s /usr/lib/x86_64-linux-gnu/xfce4 /usr/lib/i386-linux-gnu/xfce4

```
This creates the missing directories by linking to the 64-bit ones.

Tell me if it works for you (and mark as SOLVED if it does).

Cheers!

---

### Post by subehsharma on 2011-11-09
worked like a charm!! Thanks aton!

---

