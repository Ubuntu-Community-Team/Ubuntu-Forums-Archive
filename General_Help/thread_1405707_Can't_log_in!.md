---
title: "Can't log in!"
date: 2010-02-13
forum: General Help
---

### Post by Nautilus112 on 2010-02-13
Hello, this is weird, but for some reason I can't log in.  I start the computer and get to the user selection window, I click my name and it says authentication failure, without even letting me type in my password.  

What should I do? Thanks for your help.

---

### Post by ironclaw on 2010-02-13
Can you log in on a virtual terminal? Press <Ctrl>+<Alt>+<F1> to switch to a virtual terminal, and try logging in with your username and password. Press <Ctrl>+<Alt>+<F7> to switch back to the X server display.

---

### Post by Nautilus112 on 2010-02-13
I tried the virtual terminal, and it doesn't ask me for the password.  I type in my name and then it says login incorrect for 5 times.

---

### Post by ironclaw on 2010-02-13
Try booting into recovery mode and changing your user password.

Select recovery mode at the GRUB menu during boot up. Once it boots up, run
```
sudo passwd <username>
```
where <username> is your user name, and type in a new password. Then reboot and try logging in again.

---

### Post by Nautilus112 on 2010-02-13
I tried your suggestion and I get:

passwd: Authentication token manipulation error
passwd: password unchanged

---

