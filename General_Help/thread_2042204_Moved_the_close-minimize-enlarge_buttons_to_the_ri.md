---
title: "Moved the close-minimize-enlarge buttons to the right"
date: 2012-08-14
forum: General Help
---

### Post by GJ1234 on 2012-08-14
Hello,

I recently found a guide that explained how to move those buttons to the right, but I'd like to change them back.
Does anybody know how to do this?

---

### Post by Aubergines on 2012-08-14
Try

```
gconftool -s /apps/metacity/general/button_layout -t string close,minimize,maximize
```

---

### Post by vasa1 on 2012-08-14
OP hasn't mentioned the OS version or the desktop environment. Won't the answer depend on that information?

---

### Post by bob-linux-user on 2012-08-14
You might want to google for MWButtons, which is a simple graphical tool to arrnge the buttons how you want.

---

### Post by bob-linux-user on 2012-08-14
Back home now so can give you the link.....

[http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html](http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html)

I used it quite recently when setting up Ubuntu 12.04.

---

### Post by GJ1234 on 2012-08-15
Thnx for the replies everybody!

---

### Post by sienile on 2012-08-15
Remember to mark the thread as solved if the above info helped you get it done. Use the "Thread Tools" button at the top of the thread.

---

