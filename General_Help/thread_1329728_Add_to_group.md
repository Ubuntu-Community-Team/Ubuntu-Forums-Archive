---
title: "Add to group"
date: 2009-11-17
forum: General Help
---

### Post by RedSingularity on 2009-11-17
How can i add myself to the group that manages synaptic?  I want to add myself so i dont have to enter a password every time i use synaptic package manager.  Thanks.

---

### Post by Aubergines on 2009-11-17
The only way I can think of is to make a script that runs /usr/sbin/synaptic using sudo and put the script onto the gnome menu.

You'll need to add the permissions to your /etc/sudoers files so that it won't prompt you for a password like

```
steve ALL = NOPASSWD: ALL
```

Where steve is your username

---

### Post by sisco311 on 2009-11-17
> **RedSingularity said:**
> How can i add myself to the group that manages synaptic?  I want to add myself so i dont have to enter a password every time i use synaptic package manager.  Thanks.

First reas this:
[thread=1132821]HowTO: Sudoers Configuration[/thread]

Then edit the sudoers file:
```
sudo visudo
```

and append it with:
```
**username** ALL=(root)NOPASSWD: /usr/sbin/synaptic
```

replace **username** with your login name.

---

### Post by RedSingularity on 2009-11-17
Great.  Thanks. :)

---

