---
title: "Ubuntu install windows, cannot access windows partition"
date: 2012-03-14
forum: General Help
---

### Post by josiahrulez on 2012-03-14
So ive got ubuntu installed inside windows, but i want to access the windows partion because it has all my music etc. How can i do this?

---

### Post by raja.genupula on 2012-03-14
WUBI installation means first you have to get Windows boot loader then it will redirect you to Ubuntu Grub menu . so what you're missing here .

---

### Post by josiahrulez on 2012-03-14
> **raja.genupula said:**
> WUBI installation means first you have to get Windows boot loader then it will redirect you to Ubuntu Grub menu . so what you're missing here .

Im new to ubuntu and have no idea what that means? could you explain it a bit more please?

EDIT* i found it, its in /host/

---

### Post by raja.genupula on 2012-03-14
I mean ..actually you have to explain how you're system behaving when you start it . 

look at my signature for bootinfoscript and post the output of it here .

---

### Post by Mark Phelps on 2012-03-14
When you install Ubuntu using Windows (i.e., using Wubi), then when you run Ubuntu, it automatically mounts the Windows filesystem under /host.  Look for that in Nautilus and you will find your Windows files there.  Just do NOT make changes to those files.  That runs the risk of corrupting the Windows filesystem.

---

