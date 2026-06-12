---
title: "sources.list editing"
date: 2009-10-22
forum: General Help
---

### Post by michal.knapp on 2009-10-22
Hi 

well i have a little problem with permissions on sources.list, I tried to add application and somehow :D i remade sources.list file concrete i added two more labels which cause disfunction of this file ... can you help me to solve it a don't know how to edit this file cause only root can change this file. i have ubuntu for 2 days so i'm just little lagged on this.

THX

---

### Post by sgosnell on 2009-10-22
gksudo gedit /etc/apt/sources.list

---

### Post by michal.knapp on 2009-10-22
thanks a lot :)

---

### Post by sgosnell on 2009-10-23
Por nada.

---

### Post by andrew.46 on 2009-10-24
Hi sgosnell,

> **sgosnell said:**
> gksudo gedit /etc/apt/sources.list

And perhaps for insurance the following *before* opening the file:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

@michal.knapp: This will simply create a backup file that can be restored if your editing actually only makes things worse :).

All the best,

Andrew

---

### Post by sgosnell on 2009-10-24
It won't hurt, but gedit automatically makes a backup whenever you do an edit.  But if you do too many edits, you can lose the original, so it's always a good idea to have a backup somewhere.

---

