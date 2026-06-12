---
title: "Winscp and Ubunu"
date: 2009-11-09
forum: General Help
---

### Post by elcostis on 2009-11-09
Hi and good day to everyone.
I have just installed Ubuntu 9.10 on my pc and I am trying to use from my windows pc the program Winscp to access some files on my Ubuntu pc but when i try to edit them i get permissions problem. Is there some kind of solution to this?
 
My regards!

---

### Post by sh4d0w808 on 2009-11-09
> **elcostis said:**
> Hi and good day to everyone.
I have just installed Ubuntu 9.10 on my pc and I am trying to use from my windows pc the program Winscp to access some files on my Ubuntu pc but when i try to edit them i get permissions problem. Is there some kind of solution to this?
 
My regards!


I do not recommend to edit files over winscp. I recommend U to ssh to your ubuntu PC and edit the files with 'sudo vi' or 'sudo nano' commands. U can establish ssh connections from Windows with putty.

---

### Post by bchurchill on 2009-11-09
I agree with shadow808.  For either solution, make sure that you've got the ssh server installed:

sudo apt-get install ssh

that it's configured appropriately in /etc/ssh/sshd_config, and that it's running:

/etc/init.d/ssh status

---

