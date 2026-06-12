---
title: "instal ubuntu on virtualbox"
date: 2011-04-04
forum: General Help
---

### Post by michaelkhan3 on 2011-04-04
I installed ubuntu on my virtualbox but every time i start the virtualbox ubuntu starts from the iso file and asks me to install again. When i went to install again it says its already installed. 

It seems as if ubuntu is starting from the iso file instead of the installed copy. does any one know why this is and if there is a way of changing this?

---

### Post by wolfen69 on 2011-04-04
When you open vbox, highlight the ubuntu install and then select **settings** at the top. Then you need to go to storage and remove the iso as the first boot device.

---

### Post by michaelkhan3 on 2011-04-04
What do I put into it instead of the iso file and how do I do that

---

### Post by CharlesA on 2011-04-04
Just set it to empty.

---

### Post by wolfen69 on 2011-04-04
Set host drive instead of iso.

---

### Post by michaelkhan3 on 2011-04-04
I tried that and it wont start ubuntu. I get a message "[0.971213] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

I also tried in system part of settings to move the hard drive ahead of cd/DVD on the boot order and i got the same message

---

### Post by CharlesA on 2011-04-04
It sounds like the install didn't take. Reinstall it and see if it does the same thing.

---

### Post by michaelkhan3 on 2011-04-04
Thanks I'll try that now and see what happens.

---

