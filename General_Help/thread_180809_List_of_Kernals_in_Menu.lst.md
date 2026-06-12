---
title: "List of Kernals in Menu.lst"
date: 2006-05-23
forum: General Help
---

### Post by dengar on 2006-05-23
Is there a way to prevent a a kernel from being added to menu.lst after a new kernel is installed. I want to winnow the list of kernels appearing when I boot down to say 4, but don't want the kernels to be added again to menu.lst whenever I upgrade to a new kernel. Can I delete the kernels from somewhere to prevent them from reappearing after I update?

---

### Post by K.Mandla on 2006-05-23
You can edit /boot/grub/menu.lst to show only the kernels you want. Will that help?

---

### Post by adamkane on 2006-05-23
```

sudo gedit /boot/grub/menu.lst

```

Look at the end of the file for the list of kernels, and look for the word "savedefault" next to the kernel you want to boot, and delete any unnecessary entries.

Also try:
```

update-grub

```

---

### Post by aysiu on 2006-05-23
This is probably less than ideal, but when you get a new kernel, you can reboot, select the new kernel before the timeout is up, then uninstall the old kernel using Synaptic Package Manager (search for the word *linux-image*).

---

### Post by djsroknrol on 2006-05-23
Someone mentioned that the Saturday or Sunday's update did what you were looking for.. to not write them to the Menu.lst file... but it was in a discussion of 6.06, which is Dapper Drake. So maybe what you want can be had on the 1st, hopefully. 

In the past, I've done like Aysiu has suggested....It's alot safer as you can fall back to a previous image if you run into problems. I run a K7 image, so I keep the latest one in there, as well as the latest 386 one as well...besides memtest and my dual boot, I edit them down after upgrades...

---

