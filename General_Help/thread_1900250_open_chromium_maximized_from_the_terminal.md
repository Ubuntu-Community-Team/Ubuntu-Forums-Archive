---
title: "open chromium maximized from the terminal"
date: 2011-12-25
forum: General Help
---

### Post by PGScooter on 2011-12-25
How can I open chromium (using the command chromium-browser) from the commandline already maximized? I think it's the same for all gtk apps but I can't figure it out.

I'm not sure if this helps or not:
[http://developer.gnome.org/gtk/stable/GtkWindow.html#gtk-window-maximize](http://developer.gnome.org/gtk/stable/GtkWindow.html#gtk-window-maximize)

Thank you!

---

### Post by idoitprone on 2011-12-25
brower  are scary pieces of technology

[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

```
chromium --start-maximized
```

---

### Post by PGScooter on 2011-12-26
> **idoitprone said:**
> brower  are scary pieces of technology

[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

```
chromium --start-maximized
```

Thanks idoitprone,

```
chromium-browser --start-maximized
```
worked for me.
I'm guessing you have an alias setup of chromium for chromium-browser?

---

### Post by idoitprone on 2011-12-27
> **PGScooter said:**
> Thanks idoitprone,

```
chromium-browser --start-maximized
```worked for me.
I'm guessing you have an alias setup of chromium for chromium-browser?


tooo lazzzzzzzzzzzzzyyyyy. I found tat in a 2sec google search

---

