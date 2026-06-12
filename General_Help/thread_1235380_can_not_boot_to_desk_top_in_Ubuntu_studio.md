---
title: "can not boot to desk top in Ubuntu studio"
date: 2009-08-09
forum: General Help
---

### Post by elecmusic on 2009-08-09
installing Ubuntu studio. When it starts to boot for the first time it asks for my logan ...that works ..then my password..that works ..then it goes to a command promp.  that has my computer user name and the name I gave my computer. here is what it looks like...
  phillip@wright:~$   what command do I type there to open to the graphic disk top? so I do not have to stare at this black and white page. I am new to Linux but been using Ubuntu 8.10 no problem as it just starts fine. but with this instalation all I get is this dos. looking page.  I try typing help but the help was no help. I have tried many times to get this Ubuntu studio to open I sure wish I could see what it looks like when it is installed. I am just sitting here looking at this...  Phillip@wright:~$  *what do I type here?* .Please can anyone help! me.:confused:  **I( found out what I did wrong. I did not install the Ubuntu desk top is on the list of programs to install after the hard drive format is done on the installation thanks for the reply I still love linux No more waiting for the files to fly by no more driver disks I will learn this good enough for me to do what I need I just have to keep reading .peace to all** I installed Ubuntu 9.04 then I used the Synaptic package Manager to install the studio packages works great so far

---

### Post by P4man on 2009-08-09
It should boot in to X (the graphical interface) automatically. Something is wrong :)

You can try starting X by hand by typing:

```
sudo /etc/init.d/gdm start
```

It may give us a clue as to what the problem is.

---

