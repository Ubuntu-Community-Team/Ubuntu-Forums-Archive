---
title: "Cannot open tax forms with acroread"
date: 2010-01-04
forum: General Help
---

### Post by tak1150 on 2010-01-04
I can open other PDF files (including the instruction files for form 1040), but I cannot open the form 1040 PDF with acroread.
I can open the same file with evince, but I really need to do this with acroread.

Here's the output:
```
t@s:~$ acroread 
/home/tak/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/tak/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/tak/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/tak/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

```

---

### Post by pricetech on 2010-01-04
While not a solution, I'm guessing the reason why is because the tax forms are editable. Apparently accroread doesn't like them.

---

### Post by tak1150 on 2010-01-11
Yes, I'm aware of the difference between the form PDF and instruction PDF: editability. I should've asked the question this way: what causes the Acrobat Reader to crash when the PDF is editable? How can I fix it? Thanks!

---

### Post by lyall on 2010-01-11
I open both the 1040 form and the 1040 instructions with 
***Document Viewer*** with no problems

good luck and have fun learning

---

### Post by Tumpster on 2010-01-28
I have the same trouble except I can't open ANY pdf file with it. Ideas?

---

