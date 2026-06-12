---
title: "Anybody no how to decompress .rar in knoppix?"
date: 2009-08-03
forum: General Help
---

### Post by Greenbean209 on 2009-08-03
Ive recently switched to knoppix on my really old computer. It works pretty dang well. Theres one thing i need help with and that is decompressing a .rar archive. So far ive just tried expiremntall typing just like you would in ubuntu. ```
sudo apt-get install unrar
```  It said it could not find the package. I expected it wouldnt have an unrar package. So my question is does anybody know how to  get unrar or another program in knoppix?

thnx in advanced 4 any help.

---

### Post by llamabr on 2009-08-03
```
brock@hops:~$ apt-cache search unrar
comix - GTK Comic Book Viewer
unp - unpack (almost) everything with one command
unrar-free - Unarchiver for .rar files
unrar - Unarchiver for .rar files (non-free version)
brock@hops:~$ 
```

For some reason, I always have to install both of the last two, since sometimes one works, and sometimes the other works.

---

### Post by Greenbean209 on 2009-08-03
did u do that within knoppix?

---

### Post by Greenbean209 on 2009-08-03
i tried that search command in the terminal and it found nothing. So i ask again does anybody know how to decompress a .rar in knoppix?

---

### Post by juancarlospaco on 2009-08-03
sudo yum unrar

sudo yast unrar

or install PeaZIP.

---

### Post by Greenbean209 on 2009-08-03
im not familliar with yast and yum wat are these commands? Also does peazip work on knoppix?

---

