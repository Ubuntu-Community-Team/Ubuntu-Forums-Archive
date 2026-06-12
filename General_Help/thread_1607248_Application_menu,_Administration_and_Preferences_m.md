---
title: "Application menu, Administration and Preferences menu not visible"
date: 2010-10-27
forum: General Help
---

### Post by akythedoc on 2010-10-27
hi guys, i am having a problem on Ubuntu 10.10. In system menu, there is no Administration or Preferences menu.Also, application menu does not show anything. I am using Ubuntu since 2 weeks and still not used to to the terminal commands for running applications and admin tools.

one more thing.
When i booted my PC today it reported an error and process terminated before reaching the login window. So i restarted and chose recovery mode. it also reported some errors and tried to fix the problem. it deleted some files i think. and my system is working again but with above mentioned problem.

reply..
thanks..

---

### Post by AndyCee on 2010-10-28
What happens if you right-click on "Applications" and select "Edit Menus"?

---

### Post by akythedoc on 2010-10-28
sorry for late reply

nothing happens when i right click and select edit menus

places menu is normal and i can run a few apps by alt+f2.. so apps are there..
also when i click on applications, there is a very small white area appears around 1cmx2mm
Administration and preferences is also gone so i cant use them.

---

### Post by plucky on 2010-10-28
From a terminal try ```
alacarte
``` and post back any errors.

Good Luck

---

### Post by akythedoc on 2010-10-28
> **plucky said:**
> From a terminal try ```
alacarte
``` and post back any errors.

Good Luck
on giving alacarte it shows the following output:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 44, in __loadMenus
    self.applications.path = os.path.join(util.getUserMenuPath(), self.applications.tree.get_menu_file())
  File "/usr/lib/python2.6/posixpath.py", line 65, in join
    if b.startswith('/'):
AttributeError: 'NoneType' object has no attribute 'startswith'

---

### Post by plucky on 2010-10-29
There seems to be corruption with alacarte.
You could try re-installing using ```
sudo apt-get install --reinstall alacarte
```

> it also reported some errors and tried to fix the problem. it deleted some files i think.

That is not good and might be the reason for the corruption.It might be worth running a fsck on your / partition ```
sudo touch /forcefsck /dev/sda?
``` where ? specifies the number of your / partition.The command will cause fsck to run on the next reboot.You can find your / partition with the command ```
df -h
```

Good Luck

---

### Post by akythedoc on 2010-10-29
i followed the steps to reinstall alacarte and reinstalled it.
i restarted my PC.
and checked the / for any corruption on startup using fsck. It found none.

but the problem is still there.

thx fr tryin though..

if anyone knws how to fix this pls reply..

---

### Post by valdesas on 2010-11-04
Exact same problem. Happened when the Dell 1012 netbook powered off (low battery) and I was working on adding to the menu (from Systems). I am using the 10.4 Netbook edition.
Anyone... any thoughts, ideas, suggestions or solutions??  Thanks in advance!

---

### Post by valdesas on 2010-11-04
I think I solved it (with bits from other posts and guesswork!)

I'm assuming it's only the Administration and System/Preferences drop-downs.
If not, then:
right-click on panel; add to panel  and add the "Menu Bar"

Otherwise, just to get the dropdowns (and in the Netbook (UNR) it
shows up as missing sub-menus on the left navigation area)

[If you want to be extra safe, then 1st:
cp ~/.config/menu ~/.config/menu.backup]
 
cp /ect/xdg/menus/applications.menu  ~/.config/menu 
cp /ect/xdg/menus/settings.menu  ~/.config/menu 
 (overwrite if necessary) 

Then open a terminal and enter:
 pkill gnome-panel 
 It will start up again with all the drop-downs menus!

Hope that helps.

---

### Post by akythedoc on 2010-11-10
> **valdesas said:**
> I think I solved it (with bits from other posts and guesswork!)

I'm assuming it's only the Administration and System/Preferences drop-downs.
If not, then:
right-click on panel; add to panel  and add the "Menu Bar"

Otherwise, just to get the dropdowns (and in the Netbook (UNR) it
shows up as missing sub-menus on the left navigation area)

[If you want to be extra safe, then 1st:
cp ~/.config/menu ~/.config/menu.backup]
 
cp /ect/xdg/menus/applications.menu  ~/.config/menu 
cp /ect/xdg/menus/settings.menu  ~/.config/menu 
 (overwrite if necessary) 

Then open a terminal and enter:
 pkill gnome-panel 
 It will start up again with all the drop-downs menus!

Hope that helps.
I used those commands you gave but it did nothing. then i checked for the files in that folder.
There was no applications.menu file and no settings.menu file

so after Googleing i got a sample applications.menu and pasted it in the folder /etc/xdg/menu/
but this file had only accessories menu entries.

so now i have accessories menu in the applications.
i still don't have the administration and preferences menu.

now can any one help me restore the proper applications.menu file and settings.menu file??

thanks in advance..

---

### Post by akythedoc on 2010-11-14
can anyone post me a copy of your applications.menu and settings.menu files.
I think that will solve my problem.
come on guys help me.

---

