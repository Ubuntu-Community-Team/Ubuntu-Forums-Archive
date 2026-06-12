---
title: "password asked in loop (12.04)"
date: 2012-08-16
forum: General Help
---

### Post by Ed55 on 2012-08-16
Hello there,

I just upgraded Ubuntu 12.04 and that changed the resolution of my Nvidia geforce 315m graphics card. I tried many drivers and finally fixed it using the "jockey" command.

Now i have another problem. When I log in as "root" Ubuntu asks me my password (as usual) and a few seconds later goes back to the welcome screen and asks me my password again and again, entering in a loop...

Any solution(s)?

Thanks
Ed

---

### Post by cbanakis on 2012-08-16
Is it asking for your root password, or your keychain password?

It may be asking for your keychain password, and if its different from your login password, that would explain it.

I'm pretty sure if you enter the wrong keychain password, it just asks again, instead of saying its the wrong password.

---

### Post by Ed55 on 2012-09-17
Hi there,

found solution.
If you go (command line) via
ls -Shla | grep "Xauthority"
you will see that "root" takes control over the system (not you...).
Just type

rm .Xauthority*
Reboot

That's all. 
Thanks for reading.

---

