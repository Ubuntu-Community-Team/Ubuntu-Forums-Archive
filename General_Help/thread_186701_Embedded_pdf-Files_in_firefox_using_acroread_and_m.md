---
title: "Embedded pdf-Files in firefox using acroread and mozplugger not working"
date: 2006-06-02
forum: General Help
---

### Post by Bear Knuckle on 2006-06-02
Hi,

I installed mozplugger to have embedded videos in firefox, but this removed the mozilla-acroread. Mozplugger should also be able to handle pdfs and deligate them to be displayed using acroread in a window, but it's just not working, the pdf is loaded, but the windows stays grey and no acroread is loaded.

I found a bug and changed the line:
```
repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
```
to
```
repeat swallow(acroread) fill: acroread -geometry +9000+9000 +openInNewWindow "$file"

```
like advised here: [https://launchpad.net/distros/ubuntu/+source/mozplugger/+bug/3994](https://launchpad.net/distros/ubuntu/+source/mozplugger/+bug/3994)

But nothing changed, and now I wonder what to do to get acroread working embedded in firefox.

---

### Post by Bear Knuckle on 2006-06-02
Found the problem: I mistyped "+openInNewWindow" instead of "-openInNewWindow", now it's fine.

---

