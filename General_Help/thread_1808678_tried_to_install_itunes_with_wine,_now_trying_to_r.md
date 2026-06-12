---
title: "tried to install itunes with wine, now trying to remove it."
date: 2011-07-20
forum: General Help
---

### Post by steven_191 on 2011-07-20
i wanted to install itunes for my phone. i had a look online to find a good emulator. i decided to try wine. i went to the software centre and picked one of the many versions. 

I downloaded the itunes.exe file from apple and tried to install it via wine. it said i had to mark it as executable before it would work. i did this and it installed although after it said it needed to be re-installed for whatever reason.

it ran but it froze and generally took forever to do anything. so i thought im bored of waiting now. ill uninstall it. not knowing where to look and not really knowing if i should unistall itunes or unistall via wine or unistall wine altogether, i went online again and found this

[http://blog.ibeentoubuntu.com/2007/11/uninstalling-itunes-and-wine.html](http://blog.ibeentoubuntu.com/2007/11/uninstalling-itunes-and-wine.html)

i opened the synaptics package manager and found the wine package. but when clicking it the only option i got was to install it.

so is it even installed? it must be because it ran itunes? 

so now i may or may not have itunes and wine on the computer and itunes seems to be too much hassle to have working properly. how do i get rid of it now? i thought a system roll back sort of program would be good but dont know if one it already installed. i found 'back in time' in the software centre. obviously not installed yet. annoying.

---

### Post by CatKiller on 2011-07-21
If you've not installed anything else in Wine, you can just delete the .wine directory from your Home folder. That'll get rid of iTunes. You'll probably also want to delete some iTunes menu entries from ~/.config/menus/applications-merged.

---

