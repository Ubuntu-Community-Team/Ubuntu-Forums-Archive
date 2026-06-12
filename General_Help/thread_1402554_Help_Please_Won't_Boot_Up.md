---
title: "Help Please Won't Boot Up"
date: 2010-02-09
forum: General Help
---

### Post by frodriguez96 on 2010-02-09
Help my Xubuntu wont load up cause of search --no-floppy --fs-uuid --set 123456-7890-abcd-efghijklmnop  error in grub 2 menu

i tried changig it by inserting CD and pressing "e" and removing line but i always have to insert cd and edit it to load Xubuntu up....

is there anyway to change it permanently ? and if so how ?

i dont care how aslong as i dont have to insert cd and change the temporary grub.cfg file in Grub 2

-thanks

---

### Post by frodriguez96 on 2010-02-09
> **frodriguez96 said:**
> Help my Xubuntu wont load up cause of search --no-floppy --fs-uuid --set 123456-7890-abcd-efghijklmnop  error in grub 2 menu

i tried changig it by inserting CD and pressing "e" and removing line but i always have to insert cd and edit it to load Xubuntu up....

is there anyway to change it permanently ? and if so how ?

i dont care how aslong as i dont have to insert cd and change the temporary grub.cfg file in Grub 2

-thanksanyone?:confused:

---

### Post by frodriguez96 on 2010-02-09
please help me

---

### Post by john newbuntu on 2010-02-09
After logging in, does
sudo update-grub2
solve your problem?

---

### Post by Leppie on 2010-02-09
you don't have to insert the cd to edit the menu entry. hold shift at boot, the menu should come up. go to the entry you want to boot, then press "e".

try installing the system updates once booted into the system.

---

### Post by frodriguez96 on 2010-02-09
well i updated and it still doesnt work

---

### Post by frodriguez96 on 2010-02-09
i updated in terminal but no luck.....

is there anyway to remove the search line in grub.cfg permanenty ?

is there any other way to fix my boot problem ?

-thanx

---

### Post by Joe Ker1086 on 2010-02-09
when you boot into xubuntu navigate pull up a terminal and enter this

```
sudo nano /boot/grub/menu.lst
```

you can edit the boot lines in there

---

### Post by frodriguez96 on 2010-02-09
> **Joe Ker1086 said:**
> when you boot into xubuntu navigate pull up a terminal and enter this

```
sudo nano /boot/grub/menu.lst
```you can edit the boot lines in there i tried it and im confused...
 i dont get how to use it.....
can u tell me how to use it? i just want to delete the seach floppy line in /boot/grub/grub.cfg

---

### Post by Joe Ker1086 on 2010-02-09
post everything in there here and let me take a look

---

### Post by frodriguez96 on 2010-02-09
> **Joe Ker1086 said:**
> post everything in there here and let me take a look
i entered the code in terminal and the edit thing has nothing in it...... its blank

---

### Post by Joe Ker1086 on 2010-02-09
ok....sorry i dont have a lot of exp with grub2....might be labled diff..... ctrl x will exit.... try the same thing but tab it out....it might be something like /boot/grub2/menu.lst

---

### Post by frodriguez96 on 2010-02-09
> **Joe Ker1086 said:**
> ok....sorry i dont have a lot of exp with grub2....might be labled diff..... ctrl x will exit.... try the same thing but tab it out....it might be something like /boot/grub2/menu.lst  no luck

---

### Post by Joe Ker1086 on 2010-02-09
check these out [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by Leppie on 2010-02-10
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

