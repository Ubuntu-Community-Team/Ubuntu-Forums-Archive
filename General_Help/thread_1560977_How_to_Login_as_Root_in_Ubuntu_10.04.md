---
title: "How to Login as Root in Ubuntu 10.04?"
date: 2010-08-25
forum: General Help
---

### Post by muaaz007 on 2010-08-25
How to Login as Root in Ubuntu 10.04 and my problem is when i used Code Block and run my C program it said not sufficient rights(Some thing like that) , I know the terminal way to execute program but still need to know, any illustrations and help is most welcomed.....

---

### Post by dabl on 2010-08-25
```
sudo su
```

Be careful -- if you don't know what you're doing, you can wreck your system that way.

---

### Post by Rubi1200 on 2010-08-25
The root account is disabled by default in Ubuntu. For normal usage you can elevate privileges by using the sudo command.

---

### Post by Smart Viking on 2010-08-25
The root account is not activated in ubuntu, if you want to activate it you should do a google search since it is not cool to discuss it on these forums. But fear not, there is no reason to activate it! You could launch the filebrowser with the following command and do tons of stuff with root privileges:

```
gksudo nautilus
```Or you can change the permissions from the terminal so you can execute the thing or whatever(is it an .exe file you wanna execute?). This is how you do it:

```
sudo chmod +x /location/to/file.exe
```I hope this helps. :)

---

