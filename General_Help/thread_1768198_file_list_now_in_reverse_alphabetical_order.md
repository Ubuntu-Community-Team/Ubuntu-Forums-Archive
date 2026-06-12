---
title: "file list now in reverse alphabetical order"
date: 2011-05-26
forum: General Help
---

### Post by linuxonbute on 2011-05-26
Hi,

I am running fully updated ubuntu 10.10 and now, since 2 days ago, when I open a file 

in open office, gimp or gedit etc the directories and files now appear in reverse alphabetical order.

Has anyone any idea why this has happened?

Norman

---

### Post by sanderd17 on 2011-05-26
If you go to list view, you can click on the column headers to change the order. Does this help?

---

### Post by linuxonbute on 2011-05-26
> **sanderd17 said:**
> If you go to list view, you can click on the column headers to change the order. Does this help?
Can you point me to this option in any of these programs? I cannot see where it is.

In all these cases there is a view menu but not list.

---

### Post by sanderd17 on 2011-05-26
in the view menu you could choose for list.

If you don't find, could you take a screenshot, than I know we are talking about the same thing.

---

### Post by linuxonbute on 2011-05-26
Attached is the screenshot.

---

### Post by sanderd17 on 2011-05-26
Ok, you are already in list view mode :P

You just need to click the column header with "Name" on it

---

### Post by Vaphell on 2011-05-26
yeah, notice that the arrow on the right side of the name column changes orientation. It indicates ascending/descending order. In fact you can sort by any column, just focus it

---

### Post by matt_symes on 2011-05-26
Hi

Open a terminal and copy and paste
```

gconftool-2 -s -t boolean /apps/nautilus/icon_view/default_sort_in_reverse_order false
gconftool-2 -s -t boolean /apps/nautilus/list_view/default_sort_in_reverse_order false
```

Hopefully that will fix it.

Kind regards

---

### Post by linuxonbute on 2011-05-26
> **sanderd17 said:**
> Ok, you are already in list view mode :P

You just need to click the column header with "Name" on it
Well how dumb can I be:)
Of course that's it. 
Strange thing though, I altered it in open office and then fired up gimp to do the same and it had changed there as well. Thought they would be application specific.

Ah well at least that worked even though I cannot think how it happened in the first place.

Thanks guys.

---

