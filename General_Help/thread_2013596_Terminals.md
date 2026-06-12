---
title: "Terminals"
date: 2012-07-01
forum: General Help
---

### Post by rickm1945 on 2012-07-01
What is the difference between the different terminals listed in the Applications section of  the Dash? I see the regular Terminal, UXTerm, and XTerm. What are their functions?

---

### Post by Shadius on 2012-07-01
I don't know if I'm right but Terminal is used for the GNOME desktop environment. XTerm is the emulator for the X Window System. UXTerm is XTerm with Unicode support. Perhaps, someone else can provide a better explanation.

---

### Post by itcotbtoemik on 2012-07-01
> **Shadius said:**
> I don't know if I'm right but Terminal is used for the GNOME desktop environment. XTerm is the emulator for the X Window System. UXTerm is XTerm with Unicode support. Perhaps, someone else can provide a better explanation.

XTerm always "has" UTF-8 (Unicode) support, because it is compiled-in.
But by default, XTerm is compatible with DEC VT102/VT220/etc, which
do not provide that feature (long technical explanation).

Typically, XTerm is configured to use a locale resource setting that makes
it usable in UTF-8 encodings, while the uxterm script ensures that those
resources are set.

---

### Post by andrew.46 on 2012-07-01
> **rickm1945 said:**
> What is the difference between the different terminals listed in the Applications section of  the Dash? I see the regular Terminal, UXTerm, and XTerm. What are their functions?

The function is the same: to open a window where you can type commands. But there are many different flavours of terminal emulator, just  try a few and see which one suits you the best. Don't forget to try my personal favourite:

```
sudo apt-get install sakura
```

Just open a terminal and copy and paste the above :).

---

### Post by rickm1945 on 2012-07-01
Thanks to all who answered this post. I now know the difference:D.

---

