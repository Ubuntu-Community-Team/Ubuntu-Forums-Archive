---
title: "What happened to netbook?"
date: 2011-12-06
forum: General Help
---

### Post by xi109 on 2011-12-06
I installed Lubuntu 11.10-minimal and then installed lubuntu-desktop and it's working great except for the netbook interface. When I select it and log in, it sends me straight back to the login page.

I presume I'm missing a package but which one?

---

### Post by oldtimer7777 on 2011-12-06
> **xi109 said:**
> I installed Lubuntu 11.10-minimal and then installed lubuntu-desktop and it's working great except for the netbook interface. When I select it and log in, it sends me straight back to the login page.

I presume I'm missing a package but which one?

Try:

```

sudo add-apt-repository ppa:lubuntu-desktop/ppa[FONT=monospace]
[/FONT]sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get install lubuntu-desktop

```

---

