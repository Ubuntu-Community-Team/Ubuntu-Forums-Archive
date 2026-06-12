---
title: "opendict menu missing"
date: 2012-01-08
forum: General Help
---

### Post by lvm on 2012-01-08
When I start opendict it prompts me to install a dictionary via the menu, the problem is that there is no menu. Reinstalling and deleting ~/.opendict didn't help. Any ideas? 11.10-32

[img]http://bestpics.ru/full/opendict-snapshot.png[/img]

---

### Post by toomas on 2012-03-31
I had the same trouble.  After some digging in the Web, I had the luck to stumble upon
<https://bugs.launchpad.net/ubuntu/+source/opendict/+bug/881381>, from which I learned that opendict has discontinued support of python-wxgtk2.6.  Installing python-wxgtk2.8 made opendict work.

Hope this helps,
T.

---

