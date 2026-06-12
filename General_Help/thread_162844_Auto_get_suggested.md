---
title: "Auto get suggested"
date: 2006-04-19
forum: General Help
---

### Post by DiGiTY on 2006-04-19
everytime i download & install something (i.e. sudo apt-get install banshee), it notifies me of recommended and suggest packages. how do I set it up so that it simply gets those packages automatically for me???

TIA

---

### Post by dave9191 on 2006-04-19
I had a brief look through the apt get man page, and I don't think that you can tell it to get those packages automatically. If you use a program like synaptics, then it might have that option. 

The suggested packages are not required, and most of the time you will not need them. But if you know you need or want something, then you could just type "sudo apt-get install " (with the space on the end), highlight all the suggested packaged and then middle click just after the space. That will paste the package names and you can hit enter to install them. 

--
Dave

---

### Post by skymt on 2006-04-19
Installing suggested packages automatically would probably be a very bad idea. Some suggested packages are only for certain setups, and are either not useful or actually harmful (take up disk space, start un-needed servers, or conflict with packages you use). Other times there are redundant suggestions, where packages that do essentially the same thing are suggested, to give the user more choice.

If you use Synaptic, you can right-click the status box next to a package and get sub-menus with suggested and recommended packages that you can install right there. Synaptic is recommended over apt-get anyway, if only because it's easier.

---

