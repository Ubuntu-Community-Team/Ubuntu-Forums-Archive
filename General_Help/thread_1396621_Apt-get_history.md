---
title: "Apt-get history?"
date: 2010-02-02
forum: General Help
---

### Post by Kvothe on 2010-02-02
Is there a way to see the packages that I have recently installed? I'm trying to remove a program and I'm not sure what the names of the packages that came with it are.

---

### Post by nothingspecial on 2010-02-02
If you usually install using apt-get 

```
history | grep apt-get
```

There`s probably a better way but it`ll work.

---

### Post by etnlIcarus on 2010-02-02
When you install a package, any dependencies it pulls are marked as, "Automatic", and become easily removable, once no other packages require them. *sudo aptitude autoremove* should do the trick, or you can open synaptic, choose *status* from the sidebar categories, and choose *autoremovable* from he sidebar list.

---

### Post by nothingspecial on 2010-02-02
Having just read your post properly,

```
sudo apt-get autoremove
```

will remove anything you no longer need.

---

### Post by philinux on 2010-02-02
> **nothingspecial said:**
> Having just read your post properly,

```
sudo apt-get autoremove
```

will remove anything you no longer need.

+1

If anyone wants to check the apt log its in /var/log/apt/term.log

You'll also find older logs there packaged up. You need to open as admin or use gksu nautilus to read them. No idea why.

---

### Post by Kvothe on 2010-02-02
Did not get rid of them. They appear to be needed.

---

### Post by Kvothe on 2010-02-02
> **philinux said:**
> +1

If anyone wants to check the apt log its in /var/log/apt/term.log

You'll also find older logs there packaged up. You need to open as admin or use gksu nautilus to read them. No idea why.
Thank you. This should take care of it...

---

### Post by Kvothe on 2010-02-02
The package I was looking for is linux-image-2.6.24-26-generic, and that sounds important. Is it okay to remove it?

Edit: Done, problem solved. Thanks again.

---

