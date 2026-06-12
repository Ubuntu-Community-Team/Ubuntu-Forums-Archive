---
title: "shebang lines for desktop shortcut [ask]"
date: 2012-07-27
forum: General Help
---

### Post by geeko_one on 2012-07-27
I've a trouble while creating desktop shortcut using shebang lines, for the first line that I'v create before is :

```
#!/bin/bash
sudo /opt/lampp/bin/mysql
```

this lines was successful to run **MySQL**


, but when I create another line for running **firefox**, the script cannot execute the file, but it runs as text in gEdit

```
#!/bin/bash
sudo /usr/lib/firefox/firefox
```

:-k

---

### Post by SlugSlug on 2012-07-27
chmod +x your_script

you shouldn't launch firefox as root by the way

---

### Post by geeko_one on 2012-07-30
> **SlugSlug said:**
> chmod +x your_script

you shouldn't launch firefox as root by the way

 well thanks, it works..

but I think it should be launch as root, because there's some trouble with firefox if I'm logging it first without "sudo" command, I've no idea why?

---

### Post by SlugSlug on 2012-07-30
if you have ran it as sudo then you have prob screwed your permissions up


```
sudo chown USERNAME.USERNAME ~/ -R
```


try that and don't use sudo for firefox :)

you should launch any GUI apps with gksudo as it sets the right environment up, but still you shouldn't use firefox this way

---

