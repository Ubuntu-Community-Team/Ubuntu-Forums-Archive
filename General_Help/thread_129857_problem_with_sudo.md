---
title: "problem with sudo"
date: 2006-02-14
forum: General Help
---

### Post by larsemil on 2006-02-14
i have a problem running my programs that require rootauthorisation.

thats lika update, sudo and so on.


typing sudo command blaha

prompts for my rootpassword and then nothing happends. why is that?

---

### Post by minisori on 2006-02-14
Its not your root password, its your own password.

---

### Post by RAOF on 2006-02-14
It doesn't prompt for you root password, 'cause you probably haven't got one - the root accound is disabled by default in Ubuntu.  It prompts for **your** password.  And it won't display anything as you type it in.

---

### Post by larsemil on 2006-02-14
then something must be wrong because my root is active. i can su to it and use it if i want.... hmmm. strange!

---

### Post by Primary Consult on 2006-02-14
I had this problem earlier today... if you used expert install, most likely you set a root password, and the regular user account you created is not in sudoers.  As root (use su) run visudo and add your user account to the list at the bottom (only one on the list should be root).  ie:
root all=(all) all
me all=(all) all
sudo  (and thus all the admin stuff in the gui) should work now.

---

### Post by larsemil on 2006-02-15
thx man! that solved it!

---

