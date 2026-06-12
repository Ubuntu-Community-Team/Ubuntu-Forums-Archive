---
title: "upgrade manager do not upgrade anymore"
date: 2011-10-31
forum: General Help
---

### Post by Amgad elsaiegh on 2011-10-31
i am using fresh version of ubuntu 11.10 32-bit version , i can not install any updates anymore due to a weird message appear every time i try to update ubuntu, Here is a screen shot

[IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/29.jpg[/IMG]

what is that thing , lzma and how can i solve this problem ?

---

### Post by drs305 on 2011-10-31
'lzma' is in the *main* repository so it shouldn't pose a problem for normal package installations.

Try running the update command from the terminal and see if you get an invalid key error message. Post whatever errors are displayed and perhaps we can gain some insight.
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Amgad elsaiegh on 2011-11-01
thank you drs305 for replaying ^_^ , after alot of searching i found that many users suffered from the same problem and the solution was in changing the servers of downloading updates in the software sources under ubuntu software tab to : **Main server**

---

