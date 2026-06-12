---
title: "Running &quot;Back in Time&quot; as root"
date: 2010-02-21
forum: General Help
---

### Post by jesseAnger on 2010-02-21
I would like "Back in time" to run as root when Ubuntu boots. The reason I want to run it this way is after I read the documentation it would seem that although you can take snapshots of folders which are root you can't restore them. That being said, it goes on to say that if run as root it would be able to. 

First question: Is this safe for a home computer with one user?

Second Question: How do I make it run as root at startup?

---

### Post by Pollox on 2010-02-22
I believe you only need to be running as root when you actually go to restore root folders, not when you're backing them up.

---

### Post by jesseAnger on 2010-02-23
This is what I'm reading in the help text, I'm taking it as I cannot backup root folders well running Back In Time in 'user' mode. What does everyone think?

---Back In Time acts as a "user mode" backup tool. This means that you can backup/restore only folders you have write access to (actually you can backup read-only folders, but you can't restore them).

It also goes on to say the following which is why I'm curious how to have it launch as root when I log in.

---If you want to run it as root you need to use "su" (command line), "gksu" (Gnome) or "kdesudo" (KDE).

---

