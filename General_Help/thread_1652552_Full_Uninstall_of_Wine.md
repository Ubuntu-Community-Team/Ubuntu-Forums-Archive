---
title: "Full Uninstall of Wine"
date: 2010-12-25
forum: General Help
---

### Post by Mthatcher2100 on 2010-12-25
I'm fairly new to Ubuntu and have tried to get rid of Wine completely for quite some time now. I could use some help. I will post any information you request to help me along this path.

Thanks for the help :)

---

### Post by TeoBigusGeekus on 2010-12-25
What have you tried?

---

### Post by dino99 on 2010-12-25
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

the easiest/fastest way is to delete the hidden .wine folder (ctrl+h to unhide it)

---

### Post by WorMzy on 2010-12-25
[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa")

---

### Post by Mthatcher2100 on 2010-12-26
I figured the problem out, thanks for your quick responses and help. :)

---

### Post by karthick87 on 2010-12-26
```
sudo apt-get remove --purge wine
```

And then goto your home folder and Press **CTRL+H** then delete .wine directory..Or from terminal run
```
rm -R ~/.wine 
```

---

