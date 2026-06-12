---
title: "How to disable showing mounted devices on the Desktop."
date: 2009-07-02
forum: General Help
---

### Post by Hangwire on 2009-07-02
Well, the title explains it all. Now it shows my NTFS partitions and USB stick that is attached to the computer - so how can I make them not show on the desktop, but still be available through the "Places" menu. 

Any suggestions?

---

### Post by credobyte on 2009-07-02
Terminal :
```
gconf-editor
```

Browse to Nautilus/Desktop and uncheck "show media drives" ( something like that :p ).

---

### Post by TeoBigusGeekus on 2009-07-02
```
gconf-editor
```
Go to apps->nautilus->desktop
Make the necessary alterations and exit.

---

### Post by rob1408 on 2009-07-02
Press 'Alt' and 'F2'.  Type 'gconf-editor' in the box, Choose Apps, then Nautilus then desktop.  There is options to remove icons such as mounted drives and such.

---

### Post by Hangwire on 2009-07-02
Worked perfectly :) Thank you all for the fast replies.

---

