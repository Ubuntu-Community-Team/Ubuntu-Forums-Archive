---
title: "Raid 1- Best way to do it"
date: 2012-04-13
forum: General Help
---

### Post by blackangelpr on 2012-04-13
Greetings i whish to seek guidance from any expert to learn how could i create a raid1 or any other metod that will duplicate my hard drive information into another one   to savegurad the information.....

I plan to make a computer for my dad to run a LemonPOS where custumers and important database will be store but must secure the information with at least another image of the hard drive...

suggestions and comments will be appreciated

):P

---

### Post by PhantomTurtle on 2012-04-13
I'll tell you before I begin that I know nothing about RAID, but since nobody has answered yet I thought I might post this. I found this tutorial on howtoforge on how to set up Software RAID1 On A Running LVM System. It includes GRUB2 configuration. It's for Ubuntu 11.10. It looks like a pretty long process(4 pages). Again, I have no idea how to set up RAID1, so I cannot help you with any problems you run into. Here is the link: [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10]("http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10").

---

### Post by blackangelpr on 2012-04-14
> **PhantomTurtle said:**
> I'll tell you before I begin that I know nothing about RAID, but since nobody has answered yet I thought I might post this. I found this tutorial on howtoforge on how to set up Software RAID1 On A Running LVM System. It includes GRUB2 configuration. It's for Ubuntu 11.10. It looks like a pretty long process(4 pages). Again, I have no idea how to set up RAID1, so I cannot help you with any problems you run into. Here is the link: [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10).

thanks for the link i had saw it still i hope some one can mention a pci raid card or some other easier way hehehe :) lest cross our fingers :lolflag:

---

### Post by carreira on 2012-04-15
You can try raider utility:
[http://raider.sourceforge.net/](http://raider.sourceforge.net/)
This will convert your single disk to a raid system (1, 4, 5, 6 or 10).

---

### Post by blackangelpr on 2012-04-15
> **carreira said:**
> You can try raider utility:
[http://raider.sourceforge.net/](http://raider.sourceforge.net/)
This will convert your single disk to a raid system (1, 4, 5, 6 or 10).

Great idea but i must ask you 


1) had you ever use it?
2) why the switch between hard drives ?  (o_O) 
3) any thoughts about this if you used it like security risk or lack of performance?

thanks in advance

and by the way Ubuntu 12 rocks, it runs way more smooth :guitar:

---

### Post by carreira on 2012-04-15
> **blackangelpr said:**
> 


1) had you ever use it?

Of course I used it! Actually I am developping it.;)

> **blackangelpr said:**
> 
2) why the switch between hard drives ?  (o_O) 

This could be automated, but it would be necessary to change bootloader config in the original disk. So, manually swapping disks is a way to maintain untouched the original disk in case something went wrong.

> **blackangelpr said:**
> 
3) any thoughts about this if you used it like security risk or lack of performance?

I don't think this could be a problem. Today, linux software raid is a accepted as a solid solution, unless you have enough budget to buy a hardware raid system.

---

### Post by blackangelpr on 2012-04-15
> **carreira said:**
> Of course I used it! Actually I am developping it.;)


This could be automated, but it would be necessary to change bootloader config in the original disk. So, manually swapping disks is a way to maintain untouched the original disk in case something went wrong.


I don't think this could be a problem. Today, linux software raid is a accepted as a solid solution, unless you have enough budget to buy a hardware raid system.

Muchisimas gracias :p   your answer convince i will use it is there is any way to keep contact so i can give you feed back if you need it for your development?  this answer my question and better since there is no need to buy a raid 1 card. 

):P

---

