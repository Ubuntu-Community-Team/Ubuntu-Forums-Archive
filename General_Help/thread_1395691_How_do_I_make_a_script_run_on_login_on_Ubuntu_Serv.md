---
title: "How do I make a script run on login on Ubuntu Server 9.10?"
date: 2010-02-01
forum: General Help
---

### Post by intermentals on 2010-02-01
I have the desktop packages installed as well but the system is configured to go to the console on boot.

I would like to make it run a script once the user has logged in...

Thanks

---

### Post by falconindy on 2010-02-01
Add it to the user's ~/.bash_profile (assuming you're running bash). If you want this to be global, add the script to /etc/profile or /etc/profile.d/

---

### Post by cforput on 2010-02-24
I also want to run a script at login and have seen people mention ~/.bash_profile but I have looked and my user doesn't have that file. Would you know why it doesn't?

---

### Post by Muscovy on 2010-02-24
If you want to do it to all users, you can place it in /etc/xdg/autostart.

---

### Post by efflandt on 2010-02-24
**man bash**

You probably have a ~/.profile which does the same thing that ~/.bash_profile would.

---

