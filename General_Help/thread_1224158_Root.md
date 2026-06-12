---
title: "Root?"
date: 2009-07-27
forum: General Help
---

### Post by Da CalebMan on 2009-07-27
Hello,

 I'm wondering if anyone could tell me how to import extra maps into Wormux.

I spent 1h looking for someway to login as root, but when I logged in, the: 

'usr/share/games/wormux/maps'

 directory no longer exists! When I log in as my default user, 100's more files are visible, but I must have root permission to edit the 'wormux maps' folder.

What do I do?:confused:

---

### Post by magh-87 on 2009-07-27
> **Da CalebMan said:**
> Hello,

 I'm wondering if anyone could tell me how to import extra maps into Wormux.

I spent 1h looking for someway to login as root, but when I logged in, the: 

'usr/share/games/wormux/maps'

 directory no longer exists! When I log in as my default user, 100's more files are visible, but I must have root permission to edit the 'wormux maps' folder.

What do I do?:confused:

Lucky for you, you don't need to login as root!

Simply sudo the folder to make all changes. It will ask for your password and you can then proceed with your adjustments

---

### Post by Monotoko on 2009-07-27
run this command
```
sudo nautilus
```

It will open a window, which will then be able to edit/read/write in root

Heavy warning though, do not use it carelessly, sudo is the most powerful command there is

---

### Post by Da CalebMan on 2009-07-27
Woah! Thanks you guys!

I forgot all about *SUDO*, and thabkfully, I won't have to remember any commands!

Thanks a bunch!:popcorn:

~Caleb

---

### Post by Bucky Ball on 2009-07-27
Don't forget the other one mentioned, nautilus from a terminal. This basically opens up your root folder window and you can browse the machine as root. Handy for getting rid of files that a user can't (but as always, be careful when lurking about as root). :)

su = super user; do = do. Super-user do ... the next command. In other words, your root temporarily. 'su' gets you permanently, but unwise as not real safe and to be used only when necessary.

---

### Post by Cheesemill on 2009-07-27
> **Monotoko said:**
> run this command
```
sudo nautilus
```It will open a window, which will then be able to edit/read/write in root

Heavy warning though, do not use it carelessly, sudo is the most powerful command there is

You shouldn't use sudo for GUI apps, you need to do
```
gksudo nautilus
```
instead.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Da CalebMan on 2009-07-27
Thanks for the posts guys, I'll be sure to try them *all *out.

~Caleb

---

