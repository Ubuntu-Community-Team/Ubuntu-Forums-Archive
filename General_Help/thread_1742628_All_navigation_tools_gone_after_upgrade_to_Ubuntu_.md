---
title: "All navigation tools gone after upgrade to Ubuntu 11.04"
date: 2011-04-29
forum: General Help
---

### Post by yangjiangnan on 2011-04-29
I have just upgraded from 10.10 to 11.04. The installation process seems to be perfect. However, after I reboot, I can only see my previous desktop. But all the side bars are gone. The so-called Unity tools (sounds like Mac Dock) are not present at all. Now the only thing I can do is click my mouse on the desktop, open a terminal by right click, play things that have link on my desktop... I even cannot find the option to reboot or start Firefox.

What should I do now? Return to 10.10???

---

### Post by xczxc on 2011-04-29
I had that same problem. Solved it by typing ```
unity --reset
```  in the terminal

---

### Post by mchristian on 2011-04-29
Reboot. When you get to the log in screen, select Ubuntu Classic. Once that is up and running with your usual task bars, open Ubuntu Software Center. Once there do a search for Unity and install all 2D packages. Once this is done reboot again. This time at the log in screen select Ubuntu. This time you should have your Unity desktop operational.

---

### Post by dzsobacsi on 2011-04-29
In my case Unity just did not start at startup.
I have spent some time with this but anyway in my case the problem was arisen because I tried to upgrade from 10.11 netbook edition.
At the bottom of the login screen just choose Ubuntu and that's do the trick.

---

