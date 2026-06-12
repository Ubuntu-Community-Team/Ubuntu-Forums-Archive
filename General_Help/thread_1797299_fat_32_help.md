---
title: "fat 32 help"
date: 2011-07-04
forum: General Help
---

### Post by katmarce on 2011-07-04
Okay I literally know nothing about computers. My step dad switched me to Ubuntu so that I don't have to deal with all of the problems that Windows has. I have a My Passport external hard drive and a PS3. I want to watch my downloaded episodes of Dexter on the PS3. From what I understand I have to format it to Fat32. If there's an easier way to do this I'm open to suggestion. I copied everything off of the hard drive that I want to save so it's not a problem if it gets erased. I also have an Xbox 360 if that is easier, although I'm much more familiar with the PS3. I seriously do not know ANYTHING about Ubuntu. If someone could help me I'd be very grateful. Please be very specific so I can follow what you're saying. Thank you so much.

Kaiti

---

### Post by wolfen69 on 2011-07-04
Gparted will do the trick. Open a terminal and do: (you can copy and paste)
```
sudo apt-get install gparted
```
then open gparted with:
```
gksudo gparted
```
After gparted opens, you will see a pull-down menu at the top. Choose the drive you want. Then just right click it and unmount. Then you will be able to format it.

---

### Post by katmarce on 2011-07-05
Awesome! Thank you so much. I was getting really frustrated before I saw this. :D

---

