---
title: "My firefox not running"
date: 2009-10-20
forum: General Help
---

### Post by mlinuxuser on 2009-10-20
I am using ubuntu 9.04. I have created a two profiles for firefox. It worked for past few days. But Now when I start it, it shows a small firefox window with the dialogbox displaying that," could not create files at /home/myhome/ directory,And Filepermissions related errors shown. What Should I do now to fix this?:(:(

---

### Post by mlinuxuser on 2009-10-20
changing title of thread is not allowed here?

---

### Post by lovinglinux on 2009-10-20
Try running the following command in the terminal ("Applications >> Accessories >> Terminal"), without replacing any word ($USER is a variable that should be detected automatically):

```
sudo chown -R $USER:$USER $HOME/.mozilla
```

If you have started Firefox with sudo, then that's the cause of the problem. NEVER use sudo with Firefox.

---

