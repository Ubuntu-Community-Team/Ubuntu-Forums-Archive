---
title: "Nautlus Open Terminal"
date: 2009-06-30
forum: General Help
---

### Post by tad1073 on 2009-06-30
I have nautilus open-terminal installed on my system, but ever since the new version, every time I close the terminal I get this message:

```

 There is still a process still running in this terminal. Closing the terminal will kill it.

```

Does any on know of a way to fix it where the message will not appear?

I still get the message even after I do Ctrl+c

---

### Post by mcduck on 2009-06-30
That shouldn't popup if you have nothing running in the terminal any more.

Anyway, you can disable the warning, just run "gconf-editor", browse to apps/gnome-terminal/global and disable "confirm_window_close".

---

### Post by tad1073 on 2009-06-30
> **mcduck said:**
> That shouldn't popup if you have nothing running in the terminal any more.

Anyway, you can disable the warning, just run "gconf-editor", browse to apps/gnome-terminal/global and disable "confirm_window_close".

Thanks, worked like a charm.

The only thing I do is start conky from the terminal.

---

### Post by mcduck on 2009-06-30
> **tad1073 said:**
> Thanks, worked like a charm.

The only thing I do is start conky from the terminal.

that would be reason for the message as well, programs started from terminal run as child processes for that terminal, so in a way Conky is still running inside that terminal..

I always use the Run dialog (Alt-F2) for starting apps like Conky. :)

---

