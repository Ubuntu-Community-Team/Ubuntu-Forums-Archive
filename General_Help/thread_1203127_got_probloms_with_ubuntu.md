---
title: "got probloms with ubuntu"
date: 2009-07-03
forum: General Help
---

### Post by starcraftmaster on 2009-07-03
hello guys

i just installed ubuntu 9.04
but i got problems.
and i cant fix them because this the first time ever used ubuntu
so am gonna need steps as i hardly know any thing yet

first of all:star craft.
it runs so damn slow in WINE
i saw some stuff on the wine website on how to fix it , but i don't understand any of the fixes.
so i need some steps or some thing.

2nd is that i cant run the chess game in 3d mode. 
this what it says when i tell it to go into 3d mode::

unable to enable 3d mode
you are unable to play in 3d mode due to the following problems
no python opengl support 
no python gtkglext support
please contact your system administrator to resolve these probloms, until then you will be able to play chess in 2d mode. 


3rd and last problem is when i try to put visual effects on normal or extra this happens
searching for available drivers. after that this happens
desktop effects could no be enabled

when i first tried putting visual effects on normal it searched for drivers and install nvidia drivers
my graphics card is a geforce 4 mx 440 se pci 64mb
nvidia drivers ubuntu installed:::96.43.10


4th problem
cant boot windows me in grub
i have to tell the bios to boot drive 0 to boot windows me (drive 1 is where grub and ubuntu is)
this is the error messege:
Error 13
Invalid or unsupported executable format

press any key to continue...

5th problems
got no clue how to install a webcam
model:logitech web cam

hope you guys can fix this.

---

### Post by makinglife on 2009-07-03
with the webcam i think theirs something called cheesecam or something google around im sure you'll get something.

ok windows ME is crap for one. it crashed because you might of messed with some system files while installing ubuntu ( did you use wubi? )

For the hardware do this.

GO TO
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS
then make sure your graphics card is enabled or even on their.


For the chess im guessing you dont have that software installed use these line's of code and put them in your Terminal

```
sudo apt-get install python-opengl
```Hope it helped

```
sudo apt-get install libgtkglext1
```

Let them both install then your all good you can play 3d chess..I hope:lolflag:

---

### Post by starcraftmaster on 2009-07-03
> **makinglife said:**
> with the webcam i think theirs something called cheesecam or something google around im sure you'll get something.

[COLOR=Red]ok thanks i look into that[/COLOR]

ok windows ME is crap for one. it crashed because you might of messed with some system files while installing ubuntu ( did you use wubi? )

[COLOR=Red]No i did'it use wubi
am using GRUB
and windows me is fine as i can boot it by doing the boot from drive 0 thing in the bios
so theres some thing wrong with GRUB[/COLOR]


For the hardware do this.

GO TO
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS
then make sure your graphics card is enabled or even on their.
[COLOR=Red]
done that[/COLOR]

For the chess im guessing you dont have that software installed use these line's of code and put them in your Terminal

```
sudo apt-get install python-opengl
```Hope it helped

```
sudo apt-get install libgtkglext1
```Let them both install then your all good you can play 3d chess..I hope:lolflag:
[COLOR=Red]lol am noob
i got no clue what sudo apt-get install python-openg means and where to type it
EDIT
i know how to do it now
though terminal 
i did what you said and i still get the error
BUT i only get [/COLOR]
no python gtkglext support
so half a problem fixed

---

### Post by starcraftmaster on 2009-07-03
now i restarted
and i went to chess and clicked 3d
the error did not come up
but when i went to OK , it exit out on it self
now every time i go to chess it just exits out

But now visual effects works fine:p
they look nice:guitar:

so all i gotta fix now is :
windows me wont boot
chess wont work
and fix the starcraft slowness in WINE

---

### Post by starcraftmaster on 2009-07-03
ok i now have fixed the windows me not starting thing
so just chess and starcraft giving probloms

---

