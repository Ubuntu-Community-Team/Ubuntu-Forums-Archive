---
title: "How does one change terminal colors after a change root?"
date: 2011-01-31
forum: General Help
---

### Post by Rodayo on 2011-01-31
Now I know that in order to change the colors in your terminal you have to play around with ~/.bashrc

But the effects don't stay in place after a change-root is taken affect. It just reverts to black.

Is there any way I can change that too in .bashrc?

---

### Post by nathan726 on 2011-01-31
Hint: You need to edit root's .bashrc file

The Arch Linux wiki has a few examples:
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)

---

### Post by rob1101 on 2011-01-31
Yes there is. The .bashrc file you edited is *your* .bashrc file for that account (its in your home folder after all, thats where most account specific configurations go). To change the root colors you simply configure the .bashrc for the root account in the root home folder.

EDIT: Forgot to mention that the root home folder is /root, and *your *home folder is /home/*username* if your root user does not have a .bashrc file you can create your own or copy the one from your user account.

---

### Post by Rodayo on 2011-01-31
Thank you both, worked like a charm =]

---

