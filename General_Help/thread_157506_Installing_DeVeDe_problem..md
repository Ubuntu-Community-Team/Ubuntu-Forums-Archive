---
title: "Installing DeVeDe problem."
date: 2006-04-09
forum: General Help
---

### Post by NeghVar on 2006-04-09
Ok it should be simple but something isn't right. I downloaded the file from there webpage and extracted it to a folder. I checked out there install instructions and all they say is that I just have to run install.sh as root. So I fired up a terminal and got:

> kuvahmagh@ubuntu:~/Desktop/1/devede$ sudo install.sh
sudo: install.sh: command not found

The file is there because I have the file browser open oin the other side and I'm looking right at it, is there something I'm missing?

Thanks in advance for any assistance.

---

### Post by fatdaddy on 2006-04-09
try

sudo ./install.sh

that will make it use current folder

---

### Post by NeghVar on 2006-04-09
> try

sudo ./install.sh

that will make it use current folder

Ok... im an idiot... Thank you for the help, worked perfectly.

---

