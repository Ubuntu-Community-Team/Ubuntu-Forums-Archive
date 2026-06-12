---
title: "Incessant Beeping!"
date: 2009-08-22
forum: General Help
---

### Post by mbuehl on 2009-08-22
When I hold backspace too long, my computer beeps. Yes, I could just yank out my little system speaker, but I don't mind it beeping when it boots/something actually is wrong, however ubuntu seems content to beep at me every time i backspace a bit too much.

Can I turn it off?

---

### Post by Nburnes on 2009-08-22
Then don't backspace to much? It takes a long time of holding it down for it to beep at you.

---

### Post by mbuehl on 2009-08-22
> **Nburnes said:**
> Then don't backspace to much? It takes a long time of holding it down for it to beep at you.

Not for me.. and it only seems to happen in some places. If I move one space too far back in a terminal, it beeps.

---

### Post by Whiffle on 2009-08-22
Yep,  its normal, and common, and annoying as can be.  I usually solve it by blacklisting the "pcspkr" module.  by making a file containing the following in /etc/modprobe.d

```

blacklist pcspkr

```

The next time you reboot, it should be gone.

---

### Post by dhughes on 2009-08-22
Try this:

System > Preferences > Sound > Sounds (tab) 

Uncheck the option "Play alert sound"

---

