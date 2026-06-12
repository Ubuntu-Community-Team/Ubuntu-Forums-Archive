---
title: "Gedit: delete autofill entries in find/replace?"
date: 2011-02-18
forum: General Help
---

### Post by donsy on 2011-02-18
Is there a way to delete one or more (or all) autofill entries in the find/replace window of Gedit?

---

### Post by hillhotel on 2011-10-23
i have the same request of knowing how to clear the drop box file of search terms in the Search/Find dialogue of Gedit.  Usually they are a hidden text file somewhere, but alas not found.

---

### Post by crdlb on 2011-10-23
They are stored in gconf (2.x) or dconf (3.x). In dconf-editor, the path is org.gnome.gedit.state.history-entry. It should be /apps/gedit/... in gconf-editor.

---

### Post by hillhotel on 2011-10-24
I'm running Debian 6.0.3 (squeeze) and found the search history in:

 /Applications/System Tools/Configuration Editor 

for the following key:

 /apps/gnome-settings/gedit/history-gedit2_search_for_entry

Then I could choose to delete the entries or unset the key.

---

