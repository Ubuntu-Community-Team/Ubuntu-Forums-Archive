---
title: "ubuntu software center crash"
date: 2011-11-08
forum: General Help
---

### Post by Lilykos on 2011-11-08
hello everyone, i am new to the linx community, i have just installed for the first time ubuntu 11.10, and although i love the environment i have an issue. When i open the software center everything runs smoothly until i go to the tab "system". when i try to open it the software center stops working, it just shows the load screen(you know, the one that looks like a star) and the only way out is force close.do you have any dea what the problem might be? i have reinstalled the software center and the problem remains. Thanks a lot in advance!!!

---

### Post by TeoBigusGeekus on 2011-11-08
Try opening it from terminal
```
software-center
```
and post us any error messages you get when it crashes.

---

### Post by Lilykos on 2011-11-08
i opened it from terminal but i dont know how to open from terminal the "system" tab so that i can get the error message!(greek by the way, but i think its not polite to write in greeklish here, so that everyone should understand)

---

### Post by Lilykos on 2011-11-08
sorry i found it....it just says indexError: could not find tree path "number", hich number just goes on and on getting bigger and the software center is still stuck...any ideas?


//well i found it, so it may help others it a was a fault of dconf editor, na dthe process is this:
dconf-editor > org.gnome.desktop.interface > toolkit- accessibility

thanks!

---

### Post by TeoBigusGeekus on 2011-11-08
Good to know patrioti; glad you've made it!!!
Don't forget to mark the thread as solved.

---

### Post by Lilykos on 2011-11-08
sorry, no idea how to do that :S

//found it, thanks again!

---

### Post by TeoBigusGeekus on 2011-11-08
Thread tools>Mark this thread as solved.

---

