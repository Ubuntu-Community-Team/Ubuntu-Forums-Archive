---
title: "Only one character on screen after upgrade"
date: 2011-02-03
forum: General Help
---

### Post by memstick on 2011-02-03
Hello,

Today I did an upgrade to xxx.25 kernel with the update tool in ubuntu; this completely messed up my computer. It shows login page and all, but all characters are substituted with a square (something like []).

---

### Post by blueridgedog on 2011-02-03
When you boot, do you have options for other kernels?  Have you tried them?

---

### Post by memstick on 2011-02-03
Tried them all..

---

### Post by memstick on 2011-02-05
[FONT=Arial]Please help me _avoid_ having to reinstall ubuntu again. It is _really_ frustrating and it doesn't help me when I'm working on my master thesis....
[/FONT]

---

### Post by Krytarik on 2011-02-05
Are you able to login, and get to the terminal? If not, press Alt+Ctrl+F1 at the login screen, and login at the console.

Then enter the following command, it configures all downloaded but unconfigured packages:
```
sudo dpkg --configure -a
```
Post back what it shows.

---

