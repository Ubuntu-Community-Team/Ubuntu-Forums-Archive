---
title: "How to Log in to Ubuntu without a GUI and remove software!"
date: 2010-07-12
forum: General Help
---

### Post by Rytron on 2010-07-12
Hi.
I do not have this problem but I'd like to know the solution for future reference.

Case senario:
John needs to log in to Ubuntu via the command line and then run this command:
```
sudo apt-get remove irqbalance
```

What would be the exact procedure? Should John use recovery mode or is it best to get to the log in screen first?

---

### Post by cj.surrusco on 2010-07-12
The best procedure would be to choose Recovery Mode from the grub menu and then from the Recovery Mode menu, choose to drop to a root terminal. You can then execute the command from there.

---

### Post by WorMzy on 2010-07-12
Adding "text" to the kernel boot options should boot Ubuntu into a virtual terminal without loading (or at least without displaying) the GUI. But booting normally and pressing Ctrl+Alt+F1 will switch you to a virtual terminal anyway.

---

### Post by Rytron on 2010-07-12
> **cj.surrusco said:**
> The best procedure would be to choose Recovery Mode from the grub menu and then from the Recovery Mode menu, choose to drop to a root terminal. You can then execute the command from there.

In a Virtual Machine it says **netroot** (Drop to root shell prompt with networking) and **root** (Drop to root shell prompt). If I wanted to also install a program, would I have to choose '**netroot** (Drop to root shell prompt with networking)'?

---

### Post by cj.surrusco on 2010-07-12
Yes, if you want to install a program, you would need to use netroot, so that you can access the repositories.

---

### Post by Rytron on 2010-07-12
Thank you cj.surrusco. & WorMzy. ;)

By the way, I opted for netroot and was able to install Arora. :o

---

### Post by cj.surrusco on 2010-07-12
You're welcome, and don't forget to mark your thread as **[solved]**.

---

### Post by Rytron on 2010-07-13
> **cj.surrusco said:**
> You're welcome, and don't forget to mark your thread as **[solved]**.

Just one more thing. Should I be as root or normal user to install and/or remove software? You see when I go to the recovery console I am as root. However I can also log in as normal user.

---

### Post by Lampi on 2010-07-13
you can use aptitude from terminal - nice and small "gui" for package selection/deselection

---

### Post by WorMzy on 2010-07-13
> **Rytron said:**
> Just one more thing. Should I be as root or normal user to install and/or remove software? You see when I go to the recovery console I am as root. However I can also log in as normal user.

Either is fine, but as a normal user you should append 'sudo' to the start of your administrative tasks; like in your first post for example: 'sudo apt-get remove irqbalance'.

If you're root, then you don't need to include sudo, so 'apt-get remove irqbalance' would do the same thing.

---

### Post by Rytron on 2010-07-13
Cheers WorMzy.

---

