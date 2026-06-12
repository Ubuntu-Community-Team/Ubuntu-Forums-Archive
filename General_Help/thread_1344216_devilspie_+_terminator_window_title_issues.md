---
title: "devilspie + terminator window title issues"
date: 2009-12-02
forum: General Help
---

### Post by treehouse on 2009-12-02
So I'm trying to stick terminator to my desktop with devilspie. I set up gnome-terminal to use the profile name "DesktopConsole" as the window title when I open a terminal with that profile, but terminator just seems to use the current working directory as the title, so Devilspie doesn't catch it.

My devilspie:
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
        )
)

```

then I tried to set it up with the command 
```

terminator --geometry=900x970+5+28 -b -p DesktopConsole

```

I'm not sure how else to catch the window without using (application_name) in devilspie, but I'd like to be able to use Terminator without every instance getting caught.

Any ideas?

---

### Post by sisco311 on 2009-12-02
```
terminator --title "DesktopConsole"
```

---

### Post by treehouse on 2009-12-02
> **sisco311 said:**
> ```
terminator --title "DesktopConsole"
```

terminator: error: no such option: --title

---

