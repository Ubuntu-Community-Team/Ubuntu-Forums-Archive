---
title: "baffling login problem"
date: 2010-08-12
forum: General Help
---

### Post by ilcavero on 2010-08-12
I stumbled on a login problem that I'm assuming must be consequence of something getting broken on my ubuntu install. I simply can't get my login password recognized anywhere (and I haven't forgotten it), nor in shell, nor in the gnome welcome screen, nor in the unlock window after the screensaver. Thinking that resetting the password would solve this, I restarted, went into recovery console, opened the root shell, ran 'passwd myuser', entered a new simple password and it seems like a success but if I immediately run 'login myuser' or if I restart and go to the welcome screen, then it says incorrect password again. If I do 'sudo -i -u myuser' on the root shell I can do 'passwd myuser' and then when it asks me my previous password is the only time I've found where my pass gets recognized (I can set a new password then but like before I never get a login to recognize it).

The only way I found to make the machine useful again was starting gnome from the root shell and configuring in users and groups that myuser should not be asked for passwords at start. Still I cannot run anything that requires me to do sudo because I get password incorrect.

What can I do to make authentication work again?

---

