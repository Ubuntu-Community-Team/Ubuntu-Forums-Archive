---
title: "How to disable ACPI on bootup?"
date: 2011-09-05
forum: General Help
---

### Post by Pithikos on 2011-09-05
I searched a bit around but there is (still) not a clear answer on how to disable ACPI. I found that you can edit the kernel on startup and add the "pci=noacpi" line but then what? In the grub menu it states that the editing is like in emacs. Thing is I never used emacs. So how can I save once I added the line?

---

### Post by Toz on 2011-09-07
You need to edit the file **/etc/default/grub** and commit the changes.

From the command line:
```
gksudo gedit /etc/default/grub
```

and change the line starting:
> GRUB_CMDLINE_LINUX_DEFAULT=
to include **pci=noacpi**

For example, my current line reads:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
...so I would change it to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"
```

Then to commit it, run:
```
sudo update-grub
```

Reference link: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by Pithikos on 2011-09-10
Thanks a lot! Just a notice. The line 
```
gksudo /etc/default/grub
```should be
```
gksudo gedit /etc/default/grub
```

---

### Post by Toz on 2011-09-10
Thanks for the catch. I've updated my post. If you don't mind, can you mark this thread as solved from the Thread Tools link above?

---

