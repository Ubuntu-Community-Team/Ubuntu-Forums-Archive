---
title: "Nautilus - Default Sort in Reverse Order?"
date: 2012-06-16
forum: General Help
---

### Post by Saibashi on 2012-06-16
Hi all, I've been using Ubuntu since 8.04 and I've noticed one big change when I updated to 12.04.

I prefer to view my default view in nautilus to be:

[LIST]
[*]list view (zoom 33%/smallest)
[*]arranged by Modification Date
[*]and reverse order (so that the newest things added in a folder are displayed on top instead of on bottom)
[/LIST]
In the past, I used gconf-editor, went to apps->nautilus->list view and I could do all three of these.  In particular there was a checkbox to "default sort in reverse order."  In 12.04 gconf-editor does not have any of these options.  

In the nautilus file menu edit->preferences I can set the default view to list, arrange by modification date, but there is no option to view by reverse order.  

I've spent an hour trying to solve this, but haven't found an answer anywhere.  Any idea how I can sort by reverse order by default?

---

### Post by brainwash on 2012-06-16
You will have to use *dconf-editor* to change settings related to GNOME 3 applications. The editor is part of the package *dconf-tools* package. Open the editor and navigate to org.gnome.nautilus to change any option you want.

It should be also possible to change the sorting order directly in Nautilus (View > Arrange Items > Reversed Order) or by running this command in a terminal:
```
gsettings set org.gnome.nautilus.preference default-sort-in-reverse-order true
```

---

### Post by dtmbmw325i on 2012-10-07
I thought this would fix my problem but it did not. My reverse order sorting is only in the "open" and "Save as" dialog boxes. Where can I change the setting for just that?

---

### Post by HunterDX77M on 2012-10-28
I have dconf-editor, but where is the directory that I would go in to change it to display in reverse order? Thanks for any help!

---

