---
title: "help sharing keyboard and mouse using synergy-foss"
date: 2011-04-27
forum: General Help
---

### Post by markp1989 on 2011-04-27
today i tried to use synergy to share the keyboard and mouse from my imac to my ubuntu 11.04 setup.

the synergy config on my imac looks like this.
```


section: screens
        mark-paynes-imac.local:
        mark-desktop:
end

section: links
        mark-paynes-imac.local:
                right = mark-desktop
        mark-desktop:
                left = mark-paynes-imac.local
end
```

when I run synergy server on my imac, and synergy client on the ubuntu box, the mouse and clipboard get shared fine, but the keyboard doesn't , keyboard is only available to the mac.

any one else had this problem?

Thanks for looking, Mark

---

