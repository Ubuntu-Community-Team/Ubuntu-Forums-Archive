---
title: "cant make work nvidia drivers, i need help"
date: 2010-11-13
forum: General Help
---

### Post by amorallelo on 2010-11-13
Hi,
i cant install my nvidia drivers its an geforce 8400gs ive downloaded the driver but i cant install it the system wont let me, every time i open the terminal and try it give me an error whit "X" something, ive tried to restart it but it donts, i need some advise on how to make work the drivers, in advance thank you very much.

aditional info:
card: nvidia geforce 8400gs.
driver: NVIDIA-Linux-x86-260.19.21.run
and im new to linux so if you please explain me dummy version, thanks ;)

---

### Post by Finalfantasykid on 2010-11-13
Using the program jockey, will make things much easier (Hardware Drivers in the System menu).  But if you want the most bleeding edge drivers, then they way you are doing it is fine, but you have to do it from the terminal, without any GUI running to install the binary which you downloaded.

Read all instructions before doing it, and maybe write them down if you are not familiar with this as you will be without a gui for a few minutes.

I havn't had to do this in a while, so I hope this works.

Go to a TTY (CTRL + ALT + F1), login and enter this command:

```

sudo /etc/init.d/gdm stop

```I think this will disable the X server(if it doesnt, then you will get the same error as before, and in such case you should run the command below).  From here you can run the nvidia binary which you were before.

Once that is done installing, you can run this:

```
sudo /etc/init.d/gdm start
```Assuming this worked, you should have your desktop back, although you will probably have to restart your computer before the nvidia drivers are enabled.

---

### Post by Lifeless Planet on 2010-12-08
I needed to just go to the System and find the component to control drivers. I found the newest NVidia driver, installed it and just enjoyed. You don't need to learn command line commands to do that, but it is valuable information to know.

---

