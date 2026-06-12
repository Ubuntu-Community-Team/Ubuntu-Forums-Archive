---
title: "please help few questions for a new user"
date: 2009-11-26
forum: General Help
---

### Post by ibrahim.k on 2009-11-26
Hi

When installing skype I get this message 

Error: Dependency is not satisfiable: libqt4-dbus (>= 4.4.3)


I have installed ubuntu 9.10 and i have choosed to install near windows side by side but when i choose the win vista loader option I get the recovery startup for my windows vista !!! though all the files still existed !!


when I press on applications > ubuntu software center I cant download anything all the programs are not available in the current data ??'


I cant choose the extreme option in the appearance tap and when i open the hardware drivers i get nothing ! though my video card driver is not installed because i cant choose the normal or extrmem option

sorry to prolong on you guys,

---

### Post by solar george on 2009-11-26
For the drivers and software centre try bringing up the update manager,
press Alt and F2 then enter update-manager in the run box. Then click on "Check" to reload package lists.
After that you should be able to install from the software centre and use the driver manager.

---

### Post by emachnic on 2009-11-26
Skype is a bit of a pain sometimes. Make sure your computer is up to date first with the update manager. You also might want to enable some of the multiverse and univers repositories. If you need help with that...

```

sudo gedit /etc/apt/sources.list

```

Uncomment the lines with "deb" in front of them and save. Then...

```

sudo apt-get update

```

After that try installing Skype and see what happens.

---

### Post by leandromartinez98 on 2009-11-26
> **ibrahim.k said:**
> Hi

When installing skype I get this message 

Error: Dependency is not satisfiable: libqt4-dbus (>= 4.4.3)


I have installed ubuntu 9.10 and i have choosed to install near windows side by side but when i choose the win vista loader option I get the recovery startup for my windows vista !!! though all the files still existed !!


when I press on applications > ubuntu software center I cant download anything all the programs are not available in the current data ??'


I cant choose the extreme option in the appearance tap and when i open the hardware drivers i get nothing ! though my video card driver is not installed because i cant choose the normal or extrmem option

sorry to prolong on you guys,

Where are you trying to install skype from? The "good" way is to, first, add the mediubuntu repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then go to the software center, search and install skype. Also install ubuntu-restricted-extras if didn't, it is good.

--
Concerning the Windows boot, there are probably two entries for Windows in Grub, there aren't? One is probably on /dev/sda1 and the other on /dev/sda2. Very likely the correct windows is the /dev/sda2 one. There are ways to customise this menu, but I suggest you get used to linux a little bit further before doing this.

--
Which graphic card do you have?

---

