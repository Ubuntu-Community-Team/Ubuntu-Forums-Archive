---
title: "How can I repair my sources.list"
date: 2010-04-11
forum: General Help
---

### Post by Groszman on 2010-04-11
As I tried to install skype on karmic, I followed the manual given on community ubuntu documentation: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

but I did some mistakes during editinig sources.list which ended in the update not working anymore, saying:

E: Typ »exit« ist unbekannt in Zeile 51 der Quellliste /etc/apt/sources.list
(there is a wrong command in the end of the file)
E: Die Liste der Paketquellen konnte nicht eingelesen werden.
Bitte rufen Sie »Systemverwaltung« => »Software-Quellen« auf, um das Problem zu beheben.
(couldn't read the package list, please enter software sources)
E: _cache->open() failed, please report.

Entering the software sources doesn't solve the problem. I can open the source.list with gedit but I can't remove the wrong command lines since I do not know where to enter my root password.

Sorry, I know this is sort of a "guy who hasn't got any clue what he's doing, destroys his system" problem but it'll be so nice if anyone could give me some hints how to solve that problem or where to find a good manual.

cheers

---

### Post by stilling on 2010-04-11
open terminal 
sudo gedit /etc/apt/sources.list


and modify what is wrong save and close 

sudo apt-get update

your done


Hope this helps

---

### Post by WinterRain on 2010-04-11
> **Groszman said:**
> 

Entering the software sources doesn't solve the problem. I can open the source.list with gedit but I can't remove the wrong command lines since I do not know where to enter my root password.



To edit your sources list, you need superuser rights. Do:
```
gksudo gedit /etc/apt/sources.list
```
Then you will be able to make changes.

---

### Post by Groszman on 2010-04-11
Many thanks! Everything is fine again.

---

### Post by kellemes on 2010-04-11
And if you need to start from scratch..
[Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/")

---

