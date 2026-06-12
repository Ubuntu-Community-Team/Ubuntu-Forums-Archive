---
title: "Devilspie &amp; gedit"
date: 2009-11-01
forum: General Help
---

### Post by Kruptein on 2009-11-01
Okay I succesfully installed terminal on my desktop with devilspie,
but now I'm trying to add gedit to it too.
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
)
(if
        (matches (window_name) "gedit")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+0+150")
                (geometry "600x400")
        )
)
```

Now everytime 2 terminals appear and my gedit window overrides those.

How can I fix this?

---

