---
title: "link for opening files/folders as su"
date: 2009-10-26
forum: General Help
---

### Post by dogturd on 2009-10-26
Hi,

Does anyone know of  web link /tutorial to show me how to open files/folders automatically as admin/su?

---

### Post by nexes128 on 2009-10-26
You can just go Alt-F2 then type 
```
gksu nautilus
```

That will open a file browser as root and any files you open from that window will be open as root. As far as opening everything automatically as root, the only way i can think of doing that is to login as root from the gdm but that is very very bad and will no doubt cause more problems then its worth.

---

### Post by t0p on 2009-10-26
If you install the package **nautilus-gksu**, you will then be able to right-click on files and folders and there will be an option to "open as administrator".  Install the package by typing into a terminal the command:

```
sudo apt-get install nautilus-gksu
```

---

### Post by kbielefe on 2009-10-26
What do you mean by opening automatically?  What kind of files for what purpose?  I don't mean to sound preachy, but file permissions are set up how they are based on decades of experience for very good reasons.  While making exceptions is possible, and frequently done even, those exceptions are best kept as narrowly defined as possible and should have good reasons of their own behind them.  For example, if all you need is a way for a certain user to regularly change one root-owned file, there are ways to do that while opening as few security holes as possible.  If you are routinely using root access for tasks after your initial setup, there are safer ways you could be accomplishing it.

That warning out of the way, I'll second t0p's recommendation of nautilus-gksu if you insist on killing a mosquito with a cannon.

---

### Post by dogturd on 2009-10-27
Many thanks for all the help. Nautilus-gksu it is then!

---

