---
title: "Ubuntu forgot my login and password?"
date: 2009-10-03
forum: General Help
---

### Post by t0pcat on 2009-10-03
I have ubuntu installed on a desktop and I havent logged into to it in a long time. Even though I have the user name and password written down. Ubuntu rejects it and will not let me login. What the heck can I do?

---

### Post by credobyte on 2009-10-03
Ubuntu doesn't forget users/passwords! Here's a tutorial on how to recover/reset this info: [http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

---

### Post by DFlame on 2009-10-03
After exhausting any obvious caps/num lock issue that might be the case, you can change your password as follows:

-Turn on computer, hit Esc to get the GRUB boot menu
-Boot a Recovery Mode kernel
-When booting, you'll get a blue screen with various options
-Pick "Drop to root shell" or something similar

You'll now be in a root environment, so do be careful what you type. Here's how we reset your password:

```
passwd username
```

Just replace username with yours, and note the spelling of 'passwd'. Enter a new password twice to confirm, then restart the computer with:

```
shutdown -r now
```

You should be able to log in.

---

### Post by jward3010 on 2009-10-03
I love this one and the above!

---

### Post by t0pcat on 2009-10-03
Thanks, I figured it was me and not Ubuntu just like politicians I had to shift the blame from me!!:P

---

### Post by t0pcat on 2009-10-03
can I get a list of users also?

---

### Post by credobyte on 2009-10-03
> **t0pcat said:**
> can I get a list of users also?

```
ls /home
```

---

### Post by DFlame on 2009-10-03
[s]Yes, this can be shown by:

nano /etc/passwd

Again, be incredibly careful here. Changes to this file can easily break the system. You can exit the nano editor without changing anything by Ctrl-x[/s]

Far less dangerous solution above haha

---

