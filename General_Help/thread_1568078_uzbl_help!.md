---
title: "uzbl help!"
date: 2010-09-04
forum: General Help
---

### Post by thebrian on 2010-09-04
I recently discoverd the uzbl web browser, and I really like it because of it's speed and efficiency. However, I have a couple issues:

1. When I try to view/open bookmarks I've made, all that's listed in dmenu is "-e," and selecting any of them doesn't open a page.

2. When using uzbl-tabbed, then only way I can open a link in a new tab is by copying the link and then typing "gY." Is there anyway to put a "open link in new tab" option in the right-click menu? Or a way to achieve this via middle click?

Thanks!

---

### Post by VCoolio on 2010-09-04
I have this from an old uzbl config (haven't used it in months). It could be helpful; first line binds eg key combo 'to google.com <enter>' to open google in new tab; second binds tp to open clipboard url in new tab:
```

@cbind to<uri:>_ = event NEW_TAB %s
@cbind tp = sh 'echo "event NEW_TAB `xclip -selection primary -o`" > $4'

```

---

