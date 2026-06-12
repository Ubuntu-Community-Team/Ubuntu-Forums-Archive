---
title: "need to access &quot;Root&quot; folder."
date: 2010-11-22
forum: General Help
---

### Post by kree8or on 2010-11-22
Hi peeps,
How can I access the "Root" folder? when I try, it tells me I don't have the right permissions. How can I switch to the right permissions?
TIA
Kree8or

---

### Post by Bradj47 on 2010-11-22
> **kree8or said:**
> Hi peeps,
How can I access the "Root" folder? when I try, it tells me I don't have the right permissions. How can I switch to the right permissions?
TIA
Kree8or

You should be able to ```
cd /
``` if you are a standard user. If you are not an administrator and the administrator disabled read permissions to **/**, there is no way unless you have the admin password. In which case you could just 
```

sudo cd /
ls

```

---

### Post by bonixavier on 2010-11-22
[s]If you're trying to access it through Nautilus, press Alt+F2 and write gksudo nautilus. That will give you permissions to go everywhere.[/s]Oh! It's Kubuntu. Alt+F2 and type kdesu (or kdesudo) dolphin.
If it's trough the terminal, you could type sudo su.

I just don't know what could possibly be so interesting in that folder. It's like your home folder, but for the user root.

---

