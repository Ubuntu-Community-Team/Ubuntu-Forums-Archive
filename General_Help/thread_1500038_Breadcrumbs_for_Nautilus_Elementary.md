---
title: "Breadcrumbs for Nautilus Elementary"
date: 2010-06-02
forum: General Help
---

### Post by Daniel_le_Rouge on 2010-06-02
Hello!

I have installed Nautilus Elementary and I would like to use breadcrumbs. So I followed the following instructions: [http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html]("http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html")

I activated breadcrumbs in the Nautilus preferences, but still there are no breadcrumbs. What can I do to activate them?

I have attached a screenshot of my current situation.

Thanks for your help!

Daniel

---

### Post by ammonkey on 2010-06-03
You are in the 'always use location entry' mode , so no breadcrumb in this mode which seems pretty obvious.

gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false

---

### Post by Daniel_le_Rouge on 2010-06-08
Works perfectly!

Thanks a lot!

---

### Post by Subban on 2010-07-05
> **ammonkey said:**
> You are in the 'always use location entry' mode , so no breadcrumb in this mode which seems pretty obvious.

gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false

Thanks for the solution as this tripped me up also, I did the original gconf tweak when first installing Lucid and had forgotten about it. Just installed Nautilus Elementary now and had no idea what was wrong, not particularly obvious at all.

Whether its worth having Elementary check that though is another matter.

---

