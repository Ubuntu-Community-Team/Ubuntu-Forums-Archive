---
title: "Gnome Doesnt Respond"
date: 2006-05-18
forum: General Help
---

### Post by shrithegreat on 2006-05-18
dear helpful people,
i am a not so old user of ubuntu breezy badger. i have no problems with its functioning and the like. but Gnome apparently doesnt respond to my requests. like whenever i try to use something like network administration or gparted from the gnome menu it asks me for my password. wheni enter my root password it says wrong password. so i tried using my user password. it just does nothing after that. it plainly shuts up. so everytime i type in my user password(not the root password) all it does it nothing. i am getting frustruated as several options hereby are closed to me. any help in regard to this would be appreciated.
thank you

---

### Post by Ytrecq on 2006-05-18
It is right to use your user password if gksu(do) is used. 
But aren't there any missing files? And are the commands(wich open the programs) alright.

---

### Post by shrithegreat on 2006-05-18
well i installed gparted using aptitude. network-admin asks for a password too and i face the same problem there as well.if i consider gparted to be wrongly installed network-admin cant be because it is installed by default.i would appreciate further help.

---

### Post by Ytrecq on 2006-05-18
Is gksu or gksudo correctly installed? Is gnome-systools correctly installed? Maybe it will works when you try it again with Add/Remove Software.

---

### Post by sciyoshi on 2006-05-18
Hi,
Maybe try opening a terminal and typing 'sudo network-admin' or 'sudo gparted' and see if that works. If it does, i think its a problem with your gksudo..

---

### Post by shrithegreat on 2006-05-19
dear people,
i did open a terminal and logged in as root. then i typed network-admin and to my surprise it works. so does that mean my gnome is wrongly installed?

---

### Post by Ytrecq on 2006-05-19
Maybe, gksudo is a part of GNOME, isn't it? I think that gksudo isn't correctly installed. Please try to (re)install it with Synaptic, and look for other packages with gksudo in its name.

---

### Post by shrithegreat on 2006-05-19
folks,
i would have happily run synaptic but my problem doesnt allow me to. do you really advise me to go and mess with gksudo? if so i shall remove it ( hopefully it wont mess with the entire Gnome) and reinstall it using apt-get or aptitude. plese post follow up comments on this. i shall be grateful if you help me.

---

### Post by shrithegreat on 2006-05-19
folks i tried to use aptitude to install gksudo but it detected a package called gnome-sudo instead of gksudo. so i went and installed it to no avail. please help me

---

### Post by shrithegreat on 2006-05-19
folks,
this is closing time for this problem. used visudo and it worked!
thanx for all the help you rendered.

---

