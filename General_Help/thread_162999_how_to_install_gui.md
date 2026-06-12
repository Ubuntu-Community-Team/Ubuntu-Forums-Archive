---
title: "how to install gui"
date: 2006-04-20
forum: General Help
---

### Post by jeisma on 2006-04-20
hi!

i installed ubuntu using a "server" install.

now i think i need a gui without the accessories, graphics, multimedia apps, just a plain server with gui.

how do i start?


thanks!

---

### Post by codejunkie on 2006-04-20
[QUOTE=jeisma]hi!

i installed ubuntu using a "server" install.

now i think i need a gui without the accessories, graphics, multimedia apps, just a plain server with gui.

how do i start?


thanks![/QUOTE]
if you just wan't a light weight gui enable the universe repos by running 
```
sudo nano /etc/X11/xorg.conf
```uncomment the universe lines and save the file by pressing ctrl+x and then run
```
sudo apt-get install xserver-xorg xfce gdm
```instead of xfce you could also install openbox fluxbox.

---

### Post by Zerocool10482 on 2006-04-20
I think you can try this.

sudo apt-get install ubuntu-desktop

but that might not work. you can also put in the ubuntu cd and type rescue.

good luck.

---

### Post by Zerocool10482 on 2006-04-20
[QUOTE=Zerocool10482]I think you can try this.

sudo apt-get install ubuntu-desktop

but that might not work. you can also put in the ubuntu cd and type rescue.

good luck.[/QUOTE]

Edit: nevermind someone had a better answer. cool

---

### Post by Sef on 2006-04-20
a lightweight desktop:

sudo apt-get update

sudo apt-get install xubuntu-desktop

for a real lightweight one (instead of xubuntu.)  Read this before installing:  [https://wiki.ubuntu.com/Fluxbox?highlight=%28fluxbox%29]("https://wiki.ubuntu.com/Fluxbox?highlight=%28fluxbox%29")

sudo apt-get install fluxbox-desktop

What are your system specs?

---

### Post by jeisma on 2006-04-20
hello!

i have celeron 2GHz, 128MB RAM.

ill try running fluxbox.

thank you very much everyone!


joey

---

### Post by AndyCooll on 2006-04-20
Running "sudo apt-get install ubuntu-desktop" actually installs all the default Ubuntu programs as well (e.g. Firefox, Open Office, Totem etc). Not sure about the Xubuntu or Fluxbox versions.

:cool:

---

