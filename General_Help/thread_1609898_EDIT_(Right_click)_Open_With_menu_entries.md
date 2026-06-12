---
title: "EDIT (Right click) Open With menu entries"
date: 2010-10-31
forum: General Help
---

### Post by Robert R on 2010-10-31
Hi everyone, i recently uninstalled wine and also the MS office application however a bunch of entries was left in my open with dialog box , 
(the one when you choose to specify what application you would like to use to open a file see image attached),
 i would like to have these entries removed as it is alot of entries left behind, and made my list quite long
Please hep if you can thanks, Rob.

---

### Post by papibe on 2010-10-31
wine it's a little dirty on the uninstall side. Check this tutorial on the wine's wiki page: [Uninstalling Wine]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa").

Good Luck!

---

### Post by Robert R on 2010-10-31
The page states the following 
> To remove **all programs installed under Wine**, remove the wineprefix (usually the ~/.wine directory) by pasting the following command into a terminal: 

rm -rf $HOME/.wine
But  that doesn't remove them from the system menu; to clean out the menus,  carefully paste the following commands into a terminal: 

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}
However it didnt work, the commands gave no error but just didn't work
any other suggestions.

---

### Post by Verbeck on 2010-10-31
go to System>preferences>main menu
from there, go to the *other* tab. delete the entries you don't want

---

### Post by Robert R on 2010-10-31
Hey i figured it out after looking at the settings file in .config/menu u would notice
it references[COLOR=Blue] /home/rob/.local/share/applications [COLOR=Black]in this directory just delete all the [COLOR=Red].desktop[/COLOR] files related to wine ... 

Yay Yay I wanna go to Hawaii YAY\\:D/
[/COLOR][/COLOR]

---

### Post by Robert R on 2010-10-31
OOH Thanks going to prefences does work as well and is much easier lol. Didnt know that was there

---

### Post by Mr Stoozer on 2011-05-13
> **Verbeck said:**
> go to System>preferences>main menu
from there, go to the *other* tab. delete the entries you don't want

Nice one. Worked perfectly! I did see that and wonder if they were the culprits but didn't want to remove them just in case.

---

