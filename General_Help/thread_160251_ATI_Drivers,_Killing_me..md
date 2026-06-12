---
title: "ATI Drivers, Killing me."
date: 2006-04-14
forum: General Help
---

### Post by Dakaru on 2006-04-14
Ok, I got it to recognize my card and all but I can't get 3D accel.. and The last command in this guide. ([https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI))

Will not work. 


I input the command 
sudo module-assistant build,install fglrx-kernel


and it gives me an error saying incorrect headers.. How can I fix this?

---

### Post by rabidphage on 2006-04-14
r u on hoary??

---

### Post by Dakaru on 2006-04-14
[QUOTE=rabidphage]r u on hoary??[/QUOTE]
Nope Breezy Badger.

---

### Post by rabidphage on 2006-04-14
I think you looked up the wrong guide..
Check this guide. be careful next time. Don't know how much damage you did
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

### Post by zubrug on 2006-04-14
[http://www.ubuntuforums.org/showthread.php?t=64629](http://www.ubuntuforums.org/showthread.php?t=64629)

check this out.

---

### Post by Dakaru on 2006-04-14
[QUOTE=zubrug][http://www.ubuntuforums.org/showthread.php?t=64629](http://www.ubuntuforums.org/showthread.php?t=64629)

check this out.[/QUOTE]

Has this been proven to work? because if so I will try this first. On a fresh install.

---

### Post by zubrug on 2006-04-14
Yes it works great, Brought a big smile to this noobs face.

---

### Post by Dakaru on 2006-04-14
[QUOTE=zubrug]Yes it works great, Brought a big smile to this noobs face.[/QUOTE]
Do I need to select the Kernal Frame Buffer in the Xorg Config part?

---

### Post by zubrug on 2006-04-14
either should work, I selected no

---

### Post by Dakaru on 2006-04-14
[QUOTE=zubrug]Yes it works great, Brought a big smile to this noobs face.[/QUOTE]
Worked Great. ATI Drivers up and running withen a few seconds. Time to install KDE.

---

