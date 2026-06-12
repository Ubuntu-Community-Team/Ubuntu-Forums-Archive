---
title: "uninstalling .debs"
date: 2011-06-08
forum: General Help
---

### Post by flipper T on 2011-06-08
i installed rainlendar2 using a .deb package, decided i did not want it, and tried to uninstall it

i deleted the package (i assumed) and used the **find iname** command to find any lingering remnants & deleted these too

and yet it still appears as an app in 11.04's dash

how do i get it out of dash ? i assume i have missed some bits of the install

ps i rebooted & it's still there

more of an irritant than anything

---

### Post by seawolf167 on 2011-06-08
You can it using one of the below methods

CLI:
```
sudo dpkg -r packagename
```GUI:
Open synaptic package manager, find the package and uninstall (since it is a .deb file)

---

### Post by astrobob.tk on 2011-06-08
> **flipper T said:**
> i installed rainlendar2 using a .deb package, decided i did not want it, and tried to uninstall it

i deleted the package (i assumed) and used the **find iname** command to find any lingering remnants & deleted these too

and yet it still appears as an app in 11.04's dash

how do i get it out of dash ? i assume i have missed some bits of the install

ps i rebooted & it's still there

more of an irritant than anything

I am using 10.04 instead, but did check out a live 11.04; there should't be a difference.

Am very astonished that you tried deleting the files; why would you do that manually ?

Anyways; i didn't do that often but I think you can just remove it from the terminal or synaptic.

Just launch the synaptic package manager & search for the package & select it for complete removal. It should automatically remove all unnecessary files associated with the package. Moreover, the launcher is just a connection to the files, so when the files are removed, it should not be functional anymore; just an icon; not exactly sure about unity & the dash, but if you follow the instructions above, it should be removed.

Another way is running in a terminal

```
sudo apt-get remove <packagename>
```

where <packagename> is the package name, in your case rainlendar2

More details: check this thread [http://ubuntuforums.org/showthread.php?t=1100334](http://ubuntuforums.org/showthread.php?t=1100334)

---

### Post by flipper T on 2011-06-08
doh !

quick google search gave answer (dont jump on me)

for anyone interested, find name of deb package you installed

then in terminal run sudo dpkg -r "package name"

without the quotes

actually i had to edit package name as original was something like "rainlendar2.install.amd64.deb" but terminal could not find this so i took a chance on

"sudo dpkg -r rainle*"

and it found and uninstalled it

now gone from dash...yippee

---

### Post by jerrrys on 2011-06-08
I will have to try that seawolf.  i have used deborphan in the past.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=deborphan&sa=Search&cof=FORID:9#881](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=deborphan&sa=Search&cof=FORID:9#881)

---

### Post by flipper T on 2011-06-08
thx both of you

i realized my dumbness as you were writing your responses :(

will mark as solved


ps package was not in synaptic so couldn't use that approach

---

### Post by seawolf167 on 2011-06-08
> **flipper T said:**
> thx both of you

i realized my dumbness as you were writing your responses :(

will mark as solved


ps package was not in synaptic so couldn't use that approach


Hehe, no problem, glad it worked!

---

