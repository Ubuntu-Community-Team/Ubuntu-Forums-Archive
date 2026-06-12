---
title: "Kbuntu over ubuntu?"
date: 2012-06-02
forum: General Help
---

### Post by PizzaLover101 on 2012-06-02
I recently reinstalled ubuntu 12.04, and I wanted KDE instead of unity. So as I installed and did a restart, the login screen, instead of the newer ubuntu one, its another one. This doesn't bother me as much as makes me curious, are there other login screens I can use? And how could I change back if I wanted to?

---

### Post by whatthefunk on 2012-06-02
So you are using KDE??  If you want to change the login screen, go to System Settings and on the bottom you'll find Login Screen.  From there you can download and install new themes.

---

### Post by bdarb on 2012-06-02
When you installed kde it more than likely installed the kde login manager KDM and set it to default, ubuntu by default in 12.04 uses lightDM, where it used to use GDM the gnome login manager. There are lots of different options out there with different goals.

If you'd like to change your DM back to the ubuntu default enter the following into a terminal.

```
sudo dpkg-reconfigure lightdm
```

---

### Post by PizzaLover101 on 2012-06-03
> **bdarb said:**
> When you installed kde it more than likely installed the kde login manager KDM and set it to default, ubuntu by default in 12.04 uses lightDM, where it used to use GDM the gnome login manager. There are lots of different options out there with different goals.

If you'd like to change your DM back to the ubuntu default enter the following into a terminal.

```
sudo dpkg-reconfigure lightdm
```

Thank you, this did help! I was just confused on what I did, but I think I get it now.

---

