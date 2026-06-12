---
title: "HELP: Problem installing windows versino of ubunto"
date: 2010-07-09
forum: General Help
---

### Post by nvidia123 on 2010-07-09
Hi,

  i am trying to install the windows versino of ubunto using the windows installer on my laptop however, when i try to boot it, i get these BUG messages shown in the screen dump provided. Can somebody why on earth i get this???

Thanks

---

### Post by mike555 on 2010-07-09
I think your saying your trying to install Ubuntu by way of "Wubi" installer .....
   it would be better to restart your computer with the Ubuntu cd in , then start Ubuntu as "try" mode to see if everything works first ........ then I would recommend doing a "real" install by shrinking your Windows partition , making a new partition for Ubuntu and installing it there ...

---

### Post by nvidia123 on 2010-07-09
I just finished downloading from the the ubuntu site the desktop edition onto my laptop, instead of the wubi installer,ie. ubuntu-10.04-desktop-i386, will it give me the option to burn a cd? or are you referring to purchasing the actual ubuntu cd?

Also, if i do install the ubuntu-10.04-desktop-i386 on my laptop, will it give me the option to make the new partition or will i have to download a specail program to do this ?

---

### Post by nvidia123 on 2010-07-09
actaully the burning stuff i can read the [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) link provided but when i partition, i'm not sure how i would do that and hwo much memory i would need to reserve??

---

### Post by mike555 on 2010-07-09
the memory goes with the operating system , unless your thinking of installing to a virtual box ...
  you should read more about installing Ubuntu before doing anything , sounds like your too new to this to hurry into it, because it is easy to make a mistake .. I know :>)

---

### Post by nvidia123 on 2010-07-10
hi,
   i'm having trouble trying to boot from my cd that i burned, i made sure that the cd/dvd drive was at the top of the Boot menu but that didn't work, i also tried these following commands but that did not also work:

noapic nolapic 

acpi=off 

irqpoll 

lapic pci=routeirq 

and i'm still getting this messages:
BUG: soft lockup - CPU\1 stuck for 61s [plymouththd: 1189]
This should be an easy boot/install but it is making it difficult for me, what am i missing here? In addition whil i'm attempting to boot, i get this message on screen:

error: unexpectedly disconnected from boot status daemon

Thanks ubuntu :(

---

### Post by mike555 on 2010-07-10
Make sure you burned it as an .iso file and burn it slowly as you can ...
  some computers you need to hold down a key , like f12 , to boot from cd.

---

### Post by nvidia123 on 2010-07-10
well when i burned it i used the infraRecroder but after looking at what it's speed is set to it is set to Maximum but does also give the option of the following: 24x, 16x and 10x and so i believe i must have done it at 'Maximum' speed. Also on my laptop pressing f12 will give me the option to boot from whch device, i did select dvd/cd but i still have the same issu, i'l burn it again but do u think i should do 10x speed thisi time?
The desktop edition would work on a laptop right? or do i need to download the netbook version?

Also, should i change the write method? what should it be trypically?

UPDATE: I tried to use the CD on my pc and surprisingly it seemed to boot but when i try to boot from my laptop it does not.

---

