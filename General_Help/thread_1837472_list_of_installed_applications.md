---
title: "list of installed applications"
date: 2011-09-01
forum: General Help
---

### Post by Robbyx on 2011-09-01
I do not know why this does not work when it is put in the startup application preferences. I put it in the command box for a startup script:

[SIZE="2"]dpkg --get-selections  > /home/robin package.selections.txt[/SIZE]

Can someone suggest how I change it so that it runs on startup?

---

### Post by linuxman94 on 2011-09-01
> **Robbyx said:**
> I do not know why this does not work when it is put in the startup application preferences. I put it in the command box for a startup script:

[SIZE="2"]dpkg --get-selections  > /home/robin package.selections.txt[/SIZE]

Can someone suggest how I change it so that it runs on startup?

You've just got a small typo.  It should be like this:

```

dpkg --get-selections > /home/robin**/**package.selections.txt
```

---

### Post by Robbyx on 2011-09-01
> **linuxman94 said:**
> You've just got a small typo.  It should be like this:

```

dpkg --get-selections > /home/robin**/**package.selections.txt
```

I tried your version via a copy and paste and it does not work when in the startup applications. Have you tried it there?

---

