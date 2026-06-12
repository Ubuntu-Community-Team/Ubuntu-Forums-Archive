---
title: "LibreOffice Calc - Format Error Discovered - Need Help!"
date: 2012-04-05
forum: General Help
---

### Post by w201 on 2012-04-05
I can't open one of my Calc documents. This happened to me several times before upgrading to 11.10. Thought it was a bug in calc and had been solved with the new update.

Here's what I get when I try to open my file:

```
Read-Error.
Format error discovered in the file in sub-document content.xml at 2,111584(row,col).
```

Only happens with one specific file. Last time it happened I was able to recover my work from an old backup. Unfortunately this time around I haven't been backing up work. Always back up your work guys! 

Anyway, any ideas on how I can open this file? Even some third party software that can help me pull the data would be awesome!

Much appreciated!

---

### Post by TeoBigusGeekus on 2012-04-06
Rename the .ods file to .zip and unzip it.
Find the content.xml file, open it and try to figure out what's going on with the 2nd row (I can't believe you've filled up to the 111584rth column - something fishy's going on there).

---

### Post by w201 on 2012-04-06
Hi TeoBigusGeekus,

I opened the content.xml file but I can't tell what the problem is from reading the code.

There is indeed something fishy going on because my file stops at row 44. Do you understand xml code? If you'd like to take a stab at it...

---

### Post by TeoBigusGeekus on 2012-04-07
Post the ods file; or even better pm it to me.

---

### Post by w201 on 2012-04-07
PM sent.

---

