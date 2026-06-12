---
title: "Cannot see Applications dropdown"
date: 2010-10-13
forum: General Help
---

### Post by Proxin on 2010-10-13
Hi guys,
I upgraded to Ubuntu 10.10 yesterday from 10.04, and now I am unable to see the dropdown under Applications.

I have CompizConfig-Settings-Manager installed. I have tried disabling Animations, but that did not fix it.

I have attached two screenshots, the first is Before I click on Applications, the second is After I click on it.

Can someone please help me fix this problem?


Best wishes,
Proxin

---

### Post by mc4man on 2010-10-13
Open up your home folder -> View - 'Show Hidden Files'
Scroll down and open .config -> menus

Inside will be a couple of files, delete applications.menu and the dropdown should return

---

### Post by Proxin on 2010-10-14
> **mc4man said:**
> Open up your home folder -> View - 'Show Hidden Files'
Scroll down and open .config -> menus

Inside will be a couple of files, delete applications.menu and the dropdown should return

That fixed it! Thanks so much :)

---

