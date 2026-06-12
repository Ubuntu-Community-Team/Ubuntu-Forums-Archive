---
title: "Double Compression technique shrunk a 700mb file down to 40mb!"
date: 2010-12-31
forum: General Help
---

### Post by Rytron on 2010-12-31
Hi.

I downloaded a file that was 40mb compressed and was almost 700mb when fully extracted. It was inside a [COLOR="Indigo"].rar[/COLOR] file that in turn was inside another [COLOR="Indigo"].rar[/COLOR] file.

How can this be done in Ubuntu? Can this also be done with [COLOR="Blue"].zip[/COLOR] and [COLOR="Blue"].7z[/COLOR] files?

Thanks.

---

### Post by Frogs Hair on 2010-12-31
If you right click a folder with other folders inside and select compress it will compress everything . The compression tool GUI that opens when you select compress has a location and file type menu and you may use the tools , such as  7zip or RAR if installed.

---

### Post by dcstar on 2010-12-31
> **Rytron said:**
> Hi.

I downloaded a file that was 40mb compressed and was almost 700mb when fully extracted. It was inside a [COLOR="Indigo"].rar[/COLOR] file that in turn was inside another [COLOR="Indigo"].rar[/COLOR] file.
...........

Compression depends almost entirely on the structure of the original file, in this case the original file was able to be highly compressed - a lot of other files are already compressed so you are going to be sorely disappointed if you expect this level elsewhere.

An "almost 700MB" file is basically a CD image that was probably padded out to ensure that the whole CD surface was written to.

---

