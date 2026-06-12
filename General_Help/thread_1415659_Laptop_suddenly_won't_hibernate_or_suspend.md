---
title: "Laptop suddenly won't hibernate or suspend"
date: 2010-02-25
forum: General Help
---

### Post by paranoid_humanoid on 2010-02-25
I think it might have to do with an app I installed called Jupiter ([http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)) that missed with my power configs, I removed it but I still can't hibernate or suspend. Whenever I try to do either, my screen fades to black and nothing happens. If I move the mouse or touch the keyboard, it comes back.

My laptop is a Dell inspiron 1525.

---

### Post by paranoid_humanoid on 2010-02-25
Any help?
pm-suspend doesn't do anything.

---

### Post by mysteriousjinny on 2010-02-25
is there any way for you to retrieve your old settings? sorry am new to ubuntu myself, but what i mean was like system restore to get the copy of your system before the jupiter software installation

---

### Post by paranoid_humanoid on 2010-02-25
Maybe if I could know which settings and where are they located. Gnome Power Manager seems to be configured correctly. I poked around in its gconf values and it should be working. I don't have any clue about what's going on.

---

### Post by paranoid_humanoid on 2010-02-25
I hate the fact that I'm about to reinstall ubuntu to fix this :(

---

### Post by Amozzz on 2010-02-26
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?p=8877026]("http://ubuntuforums.org/showthread.php?p=8877026")

It recommends

```
sudo rm /etc/pm/sleep.d/00-jupiter-wifi
```

I had a similar problem to you when I tried to install Jupiter on an MSI-Wind but this solution fixed it. Maybe Jupiter was designed only for the EeePC!

---

