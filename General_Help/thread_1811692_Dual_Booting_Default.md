---
title: "Dual Booting Default"
date: 2011-07-25
forum: General Help
---

### Post by Urie on 2011-07-25
OK im new to linux and Ubuntu, I have windows 7 and Ubuntu dual bootin but ubuntu is the default. I would prefer windows 7 to be the default.

Dont get me wrong i love ubuntu now. great for what i need (a software for linux not windows)

I have followed these instructions

> You won't be able to change it from Windows. To change it from inside Ubuntu, edit the file /boot/grub/menu.lst. There will be a line that says
Code:
default 0
Simply change '0' to the number of your Windows install. For example, if your grub has three entries and Windows is the third, change default to 2 (0 is the first entry, not 1).

But in the file it opens there is no text whats so ever so i dont know what to change.

---

### Post by seawolf167 on 2011-07-25
Edit the config file

```
gedit /etc/default/grub
```Change the line that says

```
GRUB_DEFAULT=0
```to

```
GRUB_DEFAULT=**X**
```where you replace the X with the menu  item number (starting with 0 for the first entry) of Windows you see in  grub upon boot.

Then run 

```
sudo update-grub
```

---

### Post by Urie on 2011-07-25
Thanks for quick reply 

The file is empty do i just imput that code to the empty file?

---

### Post by drs305 on 2011-07-25
Urie,

Welcome to the Ubuntu Forums.  :-)

Please download/extract/run the boot info script from the following site and post the contents of RESULTS.txt.  It will show us the status of your boot files and allow us to help you.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Alternatively, you can install Grub Customizer, a GUI app which allows you to modify a great number of Grub settings. Click the 'Customizer' link in my signature line for more information on using GC.

---

### Post by seawolf167 on 2011-07-25
Please post the output from

```
grub-install -v
```

to ensure you are using Grub2, else the commands will be different (I just assumed you were using Grub2)

---

### Post by Urie on 2011-07-25
Hi thanks for all the replies im going to try Grub Customizer 

for a few reasons i liked

But thanks for all your help as i said new to linux and ubuntu all my PC's have run windows but it was free and you can dual boot it so i thught i would give it a go

---

### Post by seawolf167 on 2011-07-25
If you have everything solved, please mark this thread as such under Thread Tools

---

