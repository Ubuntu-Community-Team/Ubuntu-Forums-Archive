---
title: "Excel graph axis problem"
date: 2010-08-22
forum: General Help
---

### Post by Tomonomonous on 2010-08-22
bar/column graphs in ms excel (using wine) dont display their axis labels, but they display fine in OOo spreadsheet, wth?

[IMG]http://img826.imageshack.us/img826/9528/screenshote.png[/IMG]

---

### Post by jpaugh64 on 2010-08-22
I can't answer your question specifically, but I can tell you that if you run wine from a terminal window you may find out more about this problem. Sometimes when programs break in Wine, they complain about a missing file on the terminal.

It's under Apps->Accessories->Terminal

Type in:
```
$ cd "~/.wine/drive_c/Program Files/<Location_of_Excel>"
$ wine excel.exe

```I don't have Excel (or Wine, at the moment), so this is out of my head, only.

---

### Post by Tomonomonous on 2010-08-22
i was also having an issue where i was unable to open powerpoint, i found that you have to add riched20.dll as an override. this has also fixed the issue i mentioned :D

---

