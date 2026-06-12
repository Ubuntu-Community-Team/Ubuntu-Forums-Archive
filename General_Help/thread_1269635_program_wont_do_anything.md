---
title: "program wont do anything"
date: 2009-09-18
forum: General Help
---

### Post by Anonymity on 2009-09-18
Im using vuze and after I clicked "x" on the screen I can no longer bring up the menu at all and when I right click on the icon nothing happens no menu comes up. how can I end this task in terminal?

---

### Post by prem1er on 2009-09-18
```
ps ax
```

This will bring up a list of processes running along with their IDs.  Find the ID associated with vuze and run...

```
sudo kill xx
```  

where 'xx' is the process ID.

---

### Post by Vaphell on 2009-09-18
**ps ux** will list only processes owned by you
besides you can use **killall <app_name>**

if kill command doesn't work you can add -9 parameter - it's to be used on processes really resistant to closing (kill asks process to close, -9 bitchslaps it without asking)
**kill -9 <proc_id>**

---

### Post by Anonymity on 2009-09-18
ok ty got it to shut down

---

