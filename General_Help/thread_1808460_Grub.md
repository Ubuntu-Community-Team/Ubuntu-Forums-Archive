---
title: "Grub"
date: 2011-07-20
forum: General Help
---

### Post by Gwaro on 2011-07-20
I downloaded and installed Grub Customizer which worked fine. I tried to run it again but i got the message 'grub-mkconfig couldn't be executed successfully.You must run this as root.'
How am i supposed to go about this?

---

### Post by alphaamanitin on 2011-07-20
> **Gwaro said:**
> I downloaded and installed Grub Customizer which worked fine. I tried to run it again but i got the message 'grub-mkconfig couldn't be executed successfully.You must run this as root.'
How am i supposed to go about this?

```
sudo grub-mkconfig
```I suggest you read about sudo, root and get yourself more familiar with the basics of linux like operating systems.  

AlphaA

---

### Post by Gwaro on 2011-07-20
i entered the command and i get'command not found'

---

### Post by ddastoor on 2011-07-20
Are you sure you don't mean 

```
sudo grub-customizer
```

?

Please see (the author himself):

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html]("http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html")

---

### Post by Gwaro on 2011-07-20
no change

---

### Post by alphaamanitin on 2011-07-20
Sorry, my mistake was I left out the 'r' in grub.  In hind sight, it looks like you need to run the grub customizer as root, and then when it calls up the grub-mkconfig command it will be ran as root automatically.  

I don't know the command to start the grub customizer in BASH, but in your terminal you should do sudo whatevercommandrunsgrubcustomizer.  I suspect it ran the first time without a problem because you still had root privileges due to installing the program.  I the root privileges lasts for 5 minutes or so.

AlphaA

---

### Post by ddastoor on 2011-07-20
hmmmmm, not sure... 

i'm assuming u installed the following way:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```

I installed grub-customizer and then ran it.. it works fine for me... 
sudo apt-get install grub-customizer
sudo grub-customizer

just on a hunch try the following if u want...reinstall ?

so...
1) apt-get remove grub-customizer
2) and reinstall 

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

---

### Post by John-B on 2011-07-20
Gwaro, it runs fine on my system, I suggest you check the command it uses to load... ex. on my system/menu it uses "su-to-root -X -c grub-customizer" to load.  Is it the same on yours?

---

### Post by Gwaro on 2011-07-21
i am not sure on how to check that

---

### Post by John-B on 2011-07-21
Well first see if it works for you, open up a terminal and copy this (not including the quotes "") "su-to-root -X -c grub-customizer" and see if it runs for you.  If it does then we are 1 step closer :)

---

