---
title: "debugging applications"
date: 2011-03-16
forum: General Help
---

### Post by parag14 on 2011-03-16
how do i debug an application in ubuntu, for eg, when i run evince document-viewer, i want to know when and how the respective functions are being executed

---

### Post by kellemes on 2011-03-16
[http://live.gnome.org/Evince_2fDebugging]("http://live.gnome.org/Evince_2fDebugging")

---

### Post by parag14 on 2011-03-16
> **kellemes said:**
> [http://live.gnome.org/Evince_2fDebugging](http://live.gnome.org/Evince_2fDebugging)

thanx a ton. this is as far as evince goes, what do i do if i want to do the same for any other software?

---

### Post by kellemes on 2011-03-16
> **parag14 said:**
> thanx a ton. this is as far as evince goes, what do i do if i want to do the same for any other software?

Some apps include commandline options to give debugdata but most don't.. ("man <applicationname>" may explain)
In that case you need the rebuild the sourcecode with some debug-setting.
I guess because released apps don't need to include debug-info in order to keep the app small, including debug-data may make it large and slow.
But I'm no developer so I'm sure my explanation isn't perfect.. :)

---

