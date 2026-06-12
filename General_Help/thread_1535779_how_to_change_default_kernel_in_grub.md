---
title: "how to change default kernel in grub"
date: 2010-07-21
forum: General Help
---

### Post by Simplicius on 2010-07-21
I hope the following is clear enough, I'm not very technical.

I have Lucid on my laptop. Unfortunately, with the various 2.6.32 kernels neither hibernate nor suspend work, so I've installed and use the last 2.6.31 kernel that came with Karmic.

Now, I'd like to set it as default, so that I don't need to actively choose it when I boot. The problem is that I can't find a way to set Grub (version 2.0, or 1.96rc, can't remember) to pick the 2.6.31 kernel and if I try to uninstall the 2.6.32-23 kernel synaptic says that linux-generic and linux-headers will also be uninstalled (not just the parts specific to 2.6.32-23). This doesn't sound like a good idea.

Any thoughts?

---

### Post by Vaphell on 2010-07-21
to set some specific menu entry as default
- sudo gedit /etc/default/grub
- change GRUB_DEFAULT to a number that is the position of your selected entry (counting from 0)
- sudo update-grub

---

### Post by Simplicius on 2010-07-21
Thanks! Just what I needed.

---

### Post by vak on 2011-10-08
> **Vaphell said:**
> to set some specific menu entry as default
- sudo gedit /etc/default/grub
- change GRUB_DEFAULT to a number that is the position of your selected entry (counting from 0)
- sudo update-grub

btw, how to be sure about the number of entry if the server is remote and no plesk available?

---

### Post by SirKingChase on 2012-02-13
> **vak said:**
> btw, how to be sure about the number of entry if the server is remote and no plesk available?

I would not recommend doing it remotely I just tried and now I cant log in.  Im pretty much screwed until I get home and press the restart button.  I miss counted and started with 1 so its probably in the memory test :(

---

