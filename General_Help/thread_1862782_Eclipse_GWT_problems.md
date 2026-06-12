---
title: "Eclipse GWT problems"
date: 2011-10-17
forum: General Help
---

### Post by rasmus91 on 2011-10-17
Hi there.

Im currently in need of Eclipse with GWT. so i installed Eclipse, no problem. But then i tried installing the GWT plugin, and i just get:

```
Cannot complete the install because one or more required items could not be found.
  Software being installed: GWT Designer Editor 2.4.2.r37x201109270347 (com.google.gdt.eclipse.designer.editor.feature.feature.group 2.4.2.r37x201109270347)
  Missing requirement: WindowBuilder Core for XML GUI's 1.2.0.r37x201109270326 (org.eclipse.wb.core.xml 1.2.0.r37x201109270326) requires 'bundle org.eclipse.wst.sse.core 0.0.0' but it could not be found
  Cannot satisfy dependency:
    From: GWT Designer Editor 2.4.2.r37x201109270347 (com.google.gdt.eclipse.designer.editor.feature.feature.group 2.4.2.r37x201109270347)
    To: org.eclipse.wb.core.xml.feature.feature.group 1.2.0.r37x201109270326
  Cannot satisfy dependency:
    From: WindowBuilder XML Core 1.2.0.r37x201109270326 (org.eclipse.wb.core.xml.feature.feature.group 1.2.0.r37x201109270326)
    To: org.eclipse.wb.core.xml [1.2.0.r37x201109270326]
```

I do it the way it should be done: Help->install new software And then adding the link. but it just wont work.

it worked fine in ubuntu 11.04 with Eclipse 3.5. I have googled this, but i dont get what the problem is. Help would be much appreciated.

---

### Post by divestoclimb on 2011-10-20
On the Install New Software windows, click "Available Software Sites" and add [http://download.eclipse.org/releases/indigo](http://download.eclipse.org/releases/indigo) as a site.

---

### Post by rebuldeiro on 2011-10-21
Same problem solved with this solution. Thanks!

---

### Post by rasmus91 on 2011-10-23
Thanks!

---

### Post by iakko on 2011-11-16
Same here, SOLVED! Thanks!

---

### Post by Chozabu on 2013-03-02
Thanks from me too! I though having the 3.8 and 4.2 URIs listed should do fine - but it seems not!

---

