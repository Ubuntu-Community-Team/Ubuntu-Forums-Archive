---
title: "How do I completely removie Wine installed programs?"
date: 2010-03-04
forum: General Help
---

### Post by colobix on 2010-03-04
Hey. I can't remove nor uninstall the wine programs.
I have tried the uninstaller that comes with wine but it doesnt work.
How can I remove them from the start menu and the uninstall list as if they never existed on my pc?
The only thing I can do is to remove the files.

---

### Post by agolasol on 2010-03-04
i use SYNAPTIC PACKAGE MANAGER to remove it. search it then remove completely.
hope can help

---

### Post by zine92 on 2010-03-05
DO you mean the Wine package itself or the windows programs you installed via wine. Anyways, for wine, you can what colobix said, via synaptic or the ubuntu software centre. If you are refering to the windows programs use the in built wine uninstall then manually remove the directory. And if you confirm you removed packages, you can try to do sudo apt-get purge wine[press tab for autocompletion] and you can see if it is still in your workstation. Hope that helps.

---

### Post by colobix on 2010-03-05
> **zine92 said:**
> DO you mean the Wine package itself or the windows programs you installed via wine. Anyways, for wine, you can what colobix said, via synaptic or the ubuntu software centre. If you are refering to the windows programs use the in built wine uninstall then manually remove the directory. And if you confirm you removed packages, you can try to do sudo apt-get purge wine[press tab for autocompletion] and you can see if it is still in your workstation. Hope that helps.
NOt to sound rude but please read my message again.
I said programs and i said i cant uninstall them using the wine uninstaller.
the programs are still on the list and it doesnt even remove the files from the c driver folder.

edit: agolasol didn't read my message either,

---

### Post by zine92 on 2010-03-05
Did you try the options unistall wine software from the wine menu options. If after you try that, they are still stuck menus, use the menu editor to remove them and/or report them the the wine team.

---

### Post by colobix on 2010-03-05
OMFG.
No u can not remove wine installed programs using the menu editor, since the Application folder is a shortcut under Wine itself not a sub-folder,
If I could do it that way it would be easy and I wouldn't have to come here.

---

### Post by lavinog on 2010-03-05
If you delete the /home/user/.wine folder it lets you start with a clean slate...sometimes its better to do that than uninstall a bunch of programs.
If you just want to remove one program, you can just remove the program folder: /home/user/.wine/drive_c/Program\ Files/programfolder

---

### Post by colobix on 2010-03-05
That didnt solve the menu problem but ok I figured it out.

/home/user/.local/share/desktop-directories/
and
/home/user/.local/share/applications/wine

But thank you anyway guys. Problem solved

---

### Post by colobix on 2010-03-05
NO way, I take it back. that didn't remove the start menu shortcuts either, only the installation log and offcorse the files. Where the heck are these these shortcut links?

---

### Post by allynux on 2010-03-05
Remove /home/*<your username>*/.local/share/applications/wine/Programs/*<your uninstalled wine program folder>*

---

