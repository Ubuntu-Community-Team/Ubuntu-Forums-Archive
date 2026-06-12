---
title: "Is there a way to lock virtual terminal without quitting the current program?"
date: 2011-05-26
forum: General Help
---

### Post by l07 on 2011-05-26
vlock works, however it requires that I return to the shell to run it. Is there a way to assign a key combination to run vlock, so the current program doesn't have to be ended?

---

### Post by lmarmisa on 2011-05-26
> **l07 said:**
> vlock works, however it requires that I return to the shell to run it. Is there a way to assign a key combination to run vlock, so the current program doesn't have to be ended?

Try to launch your program in the background ending the command with an ampersand character (&). For example:

```

firefox &
vlock

```

---

### Post by l07 on 2011-05-26
I tried 'htop & vlock' but that didn't produce the desired result. Also firefox wouldn't run in a virtual terminal in case you're thinking of emulated terminal.

---

### Post by l07 on 2011-05-28
Other suggestions?

---

