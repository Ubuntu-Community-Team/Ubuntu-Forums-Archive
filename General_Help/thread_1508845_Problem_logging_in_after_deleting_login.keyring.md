---
title: "Problem logging in after deleting login.keyring"
date: 2010-06-13
forum: General Help
---

### Post by rsanchez1 on 2010-06-13
I was having a problem with the keyring asking me for a password after I changed my user password. I googled it and found that since the password changed, I will get asked for the keyring password until I delete ~/.gnome2/keyrings/login.keyring. What happened was that I wasn't paying attention that you had to generate a new keyring password before rebooting. Now, whenever I try to login via gdm, I get this message:
 
error initiating conversation with authentication system - general failure
 
How do I get it working again? I can still login from the terminal.

---

### Post by arrange on 2010-06-13
I'm not sure, but on my system I have nothing in the *~/.gnome2/keyrings/* folder and I'm able to login (though I use automatic logging) normally. Try moving (not deleting) all the files from that folder somewhere else.

---

### Post by rsanchez1 on 2010-06-13
The only other file in the directory was user.keyrings, so I moved it to my home folder but I'm still getting the same result.
 
I tried looking for a way to reset the gnome keyrings from the terminal, but all the solutions I found required a GUI, and I can only login from terminal at the moment.
 
:confused:

---

### Post by rsanchez1 on 2010-06-13
I should also note that I'm on 10.04 32-bit.

---

### Post by rsanchez1 on 2010-06-13
Actually I just found the solution to my problem. One of the other solutions to my keyring problem was to install libpam-keyring, then modify /etc/pam.d/gdm by adding the line @include common-pamkeyring. I removed that line and now I can login again. Thanks for the help!

---

