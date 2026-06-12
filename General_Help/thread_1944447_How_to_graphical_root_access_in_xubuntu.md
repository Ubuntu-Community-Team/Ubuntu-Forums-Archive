---
title: "How to graphical root access in xubuntu?"
date: 2012-03-21
forum: General Help
---

### Post by &amp;hiu)(@% on 2012-03-21
Hello!

I am used to KDE and Kubuntu Linux, where the "kdesu" and "kdesudo" commands are available.
Now I have Xubuntu Linux installed, and need equivalent commands for starting applications with root access via shortcuts on the menu and the desktop. This is for some bugfixing and workaround purposes.

How do one do this in Ubuntu and Xubuntu?

---

### Post by wojox on 2012-03-21
Install gksu is one option.

---

### Post by philinux on 2012-03-21
> **seagulfish said:**
> Hello!

I am used to KDE and Kubuntu Linux, where the "kdesu" and "kdesudo" commands are available.
Now I have Xubuntu Linux installed, and need equivalent commands for starting applications with root access via shortcuts on the menu and the desktop. This is for some bugfixing and workaround purposes.

How do one do this in Ubuntu and Xubuntu?

For Xubuntu
```
gksu thunar
```

[http://askubuntu.com/questions/71585/what-are-the-equivalents-of-gksu-nautilus-in-other-ubuntu-derivatives](http://askubuntu.com/questions/71585/what-are-the-equivalents-of-gksu-nautilus-in-other-ubuntu-derivatives)

---

### Post by Marzata on 2012-03-21
```
sudo thunar
```

---

### Post by philinux on 2012-03-21
> **Marzata said:**
> ```
sudo thunar
```

Sorry that can be unsafe. Better custom and practice to use gksu for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Marzata on 2012-03-21
Why unsafe? 

> **philinux said:**
> Sorry that can be unsafe. Better custom and practice to use gksu for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by philinux on 2012-03-21
From psychocats.

> Why not make exceptions?
Bottom line: most of the time when you use sudo for graphical applications, it's fine. Some of the time, though, it is not fine, and is, in fact, extremely bad.

If you made exceptions, you would have to give people a list of all the graphical applications that are okay to run as sudo and a list of all the graphical applications that must be run as gksudo or kdesudo.

Why make a list that needs to be compiled and updated, that most people won't refer to, and that is completely unnecessary? Just be consistent in suggesting good practice: gksudo and kdesudo for graphical applications. sudo for command-line applications.

  ..

---

### Post by Marzata on 2012-03-21
Thank you! 

> **philinux said:**
> From psychocats.

  ..

---

