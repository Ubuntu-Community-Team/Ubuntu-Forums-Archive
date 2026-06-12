---
title: "Do I have Grub2? Also, blank menu.lst"
date: 2010-08-22
forum: General Help
---

### Post by burgerearl on 2010-08-22
I am trying to edit grub so that it doesn't timeout the menu. I've found a lot of solutions to this where I edit menu.lst. However, this file is blank when I open it.

I just upgraded to Lucid and kept a lot of my old grub settings (I had customized it somewhat).

Also, I am not sure if I have grub or grub2. How can I figure this out?

Thanks!

---

### Post by guitarhero183 on 2010-08-22
I am pretty sure that grub2 doesn't use menu.lst anymore.
The files that it uses has changed.
Maybe you could try looking under /etc/defaults/grub

---

### Post by BrockStrongo on 2010-08-22
make sure that you update grub2 after making any changes to /etc/default/grub 
sudo update-grub2

---

### Post by dougalkerr on 2010-08-22
Yes in Terminal you 'sudo gedit /etc/default/grub' and then when finished with changing the timeout and save the change to the file you must open Terminal again and type 'sudo update-grub'.
I have never had to end the command with a 2.

If you don't update grub this way then the next time you boot Grub will overwrite any change you initially made.

---

### Post by oldfred on 2010-08-22
If you want to see versions:

Grub version
grub-install -v

lsb_release -a
dpkg -l 'grub*'


sudo update-grub2 works but all it does is link to update-grub which also then links to another command.

---

