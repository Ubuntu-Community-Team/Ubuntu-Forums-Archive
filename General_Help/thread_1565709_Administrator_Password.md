---
title: "Administrator Password"
date: 2010-09-01
forum: General Help
---

### Post by gdonwallace on 2010-09-01
OK, this is a little odd.  There where some updates for 10.04.1 yesterday, after I installed them, a few hours later I restarted my machine as new headers and kernel files where downloaded.

So this morning, when I come in, I wanted to check my software sources as I saw something a little odd yesterday.  When I try to start that program; I am asked for my administrator password.  Not the password I use for administrative tasks; which is what I am generally asked for.

Anyone else seeing this?  And if so, what happened.  The admin account I have setup is My account, I am the only person on the machine.  In the past I have entered my password and carried on; not this morning.  Not sure what is happening; but I have not setup an actual admin account / password.

---

### Post by hhh on 2010-09-01
See if this link helps...
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gdonwallace on 2010-09-01
Thanks for the info, looked it over and looks like it will help.

However; I just rebooted again, and everything seems back to normal.  When I run software sources it is asking for my password for admin tasks and not the admin password.

pretty odd....

thanks for the help though.

---

### Post by hhh on 2010-09-01
No problem, glad it's sorted.

---

### Post by sikander3786 on 2010-09-01
That seems like you were not on the sudoers list and then eventually you did get on that list on reboot. Pretty odd. That might sound silly, but, were you typing your correct password?

---

