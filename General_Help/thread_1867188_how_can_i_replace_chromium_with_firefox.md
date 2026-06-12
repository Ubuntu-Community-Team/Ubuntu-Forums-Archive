---
title: "how can i replace chromium with firefox?"
date: 2011-10-22
forum: General Help
---

### Post by daniel227 on 2011-10-22
hello,

i quite like lubuntu and it really seems to help with my old hardware.

i'm just not so happy with chromium and i would like to use firefox instead.

unfortunately, uninstalling chromium from the synaptic package manager requires me to uninstall most of lubuntus desktop environment too (?????).
i tried that and it really started to get wobbly, i couldn't connect to mobile broadband anymore and after a reboot the synaptic package manager (what a word!) wouldn't start anymore.

reinstalling now.

any suggestions? maybe from the terminal?

ps: i had a look at this [http://ubuntuforums.org/showthread.php?t=1798792&highlight=lubuntu+uninstall+chromium](http://ubuntuforums.org/showthread.php?t=1798792&highlight=lubuntu+uninstall+chromium)
-but it's way beyond me.

greetings,

daniel

pps: please lets not start a discussion about why don't i want to use chromium and it's not chrome, you know. i know.

---

### Post by masgeeks on 2011-10-22
Is there any reason why you cannot just leave chrome installed and then just install firefox and set firefox as your default web browser...???

---

### Post by raja.genupula on 2011-10-22
first install the firefox and then remove chromium 

you can get the firefox by 
```
sudo apt-get install firefox
```

then remove chromium and its not make any type of harm to your system.

---

### Post by ajgreeny on 2011-10-22
If removing chromium also removes **lubuntu-desktop** you need not worry.  The package **lubuntu-desktop** is just a meta-package which ensures everything is present in the original system, but it does not do anything nor take any applications away, and is not used by the system for any needed actions, other than, for example, a distro upgrade from 11.04 to 11.10.  It is not an application in itself and you will not know it is missing.

However, is it really important to remove chromium?  I use lubuntu on two machines and have both browsers on both machines.  I have set firefox, which I also prefer, as the default app for html files, and have had no problems of any kind with that setup.

---

### Post by daniel227 on 2011-10-22
> **raja.genupula said:**
> first install the firefox and then remove chromium 

you can get the firefox by 
```
sudo apt-get install firefox
```then remove chromium and its not make any type of harm to your system.

did you actually try this? does it make a difference if i install firefox First, and then uninstall chromium?

---

### Post by daniel227 on 2011-10-22
> **ajgreeny said:**
> If removing chromium also removes **lubuntu-desktop** you need not worry.  The package **lubuntu-desktop** is just a meta-package which ensures everything is present in the original system, but it does not do anything nor take any applications away, and is not used by the system for any needed actions, other than, for example, a distro upgrade from 11.04 to 11.10.  It is not an application in itself and you will not know it is missing.

However, is it really important to remove chromium?  I use lubuntu on two machines and have both browsers on both machines.  I have set firefox, which I also prefer, as the default app for html files, and have had no problems of any kind with that setup.


-...hm.
bout the first thing, i read that somewhere, but i'm pretty sure it did sth more to my system. but then "pretty sure" is not exact - i guess i have to go on using lubuntu and get the feel of it. also i'm going to upgrade, i guess that will change things, too.

also, is there any kind of help in lubuntu? F1 seems to do nothing, and i haven't seen anything in the menus either.

thanks to all.

---

### Post by hhh on 2011-10-22
> **daniel227 said:**
> does it make a difference if i install firefox First, and then uninstall chromium?
Not critically, but it does in Debian based systems like Ubuntu. Some programs are dependent on a web browser, so if you remove chromium apt will automatically install Iceape to satisfy the dependency. Since you don't want Iceape, just install Firefox first, as that too satisfies the dependency.

You can get help with Lubuntu from the LXDE wiki and Ubuntu forums...
[http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page)

Also Google LXDE and look at the Arch wiki for it.

---

### Post by raja.genupula on 2011-10-22
> **daniel227 said:**
> did you actually try this? does it make a difference if i install firefox First, and then uninstall chromium?
Hi man ,NO  , but i have google chrome,chromium and firefox in my box and Fox and g chrome are good for me .But why i have suggested this means , i have seen a post that making a browser free system really become big problem , in that if user removes chrome then firefox installs and vice-versa.so i keep in mind that and suggested you that first install firefox and then remove chromium,

---

