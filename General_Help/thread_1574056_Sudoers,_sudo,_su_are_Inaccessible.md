---
title: "Sudoers, sudo, su are Inaccessible"
date: 2010-09-13
forum: General Help
---

### Post by d00rman on 2010-09-13
I did some terrible mistake, basically, I gave a wrong permission to the /etc/sudoers file using chmod and now, I can't access it anymore.

I can't enter any 'sudo' in the terminal either as they say permission denied... and 'su' doesn't work, says 'Authentification failure' after I enter the password...

Tried to connect as root, but since I didn't give it a password already, it won't work.

Feel like I'm pretty out of options
What shall I do ?

---

### Post by WorMzy on 2010-09-13
Boot into recovery mode and drop to a root shell, as outlined in the first part of this tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Then use chmod to fix the permissions of sudoers. I believe it should have 440.

What were you trying to accomplish by changing it's permissions?

su doesn't work because root doesn't have a password by default (su asks you for root's password, sudo asks for yours)

---

### Post by MooPi on 2010-09-13
I'm going to guess that you were trying to edit the sudoers file and couldn't get it to open with your normal editor. Sudoers file is normally edited with ```
sudo visudo
``` command. With this command nano opens my sudoers. I imagine you can change the default editor but I would just stick with nano if I were you.

---

### Post by d00rman on 2010-09-13
Awwww
Thank you kind cat.
Can't believe the solution was that simple :o

---

