---
title: "Grub menu can't detect my windows OS  wt to do ?"
date: 2010-11-15
forum: General Help
---

### Post by Mashvv on 2010-11-15
Hey guys ! i have a windows xp OS installed on C and on D ubuntu 64bit ! and i disabled from windows to see the booting manager where it shows me weather to choose Windows or ubuntu !

and the GURB menu , when it comes up i cant see windows ! 
Note: i tried the sudo update-gurb this or wtever command was it ! but also failed to show windows

---

### Post by inso_741 on 2010-11-15
boot a windows disk and fix windows using bootfix command(u'll have to select repair windows first)

---

### Post by Hippytaff on 2010-11-15
Or try
```

sudo update-grub

```
> 
i tried the sudo update-gurb 

unless this is just a typo

---

### Post by Quackers on 2010-11-15
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

