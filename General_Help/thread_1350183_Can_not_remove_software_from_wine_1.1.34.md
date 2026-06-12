---
title: "Can not remove software from wine 1.1.34"
date: 2009-12-09
forum: General Help
---

### Post by sokam on 2009-12-09
Today, I updated my wine through update manager after adding the Repository described in here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I am trying to uninstall / remove software that has been installed in wine by Application-> Wine-> Uninstall Wine Software.  When I selected an application and then click REMOVE. Nothing happened.  Since I am trying to test an older version of a window application that required the newer version to be uninstall first, (I am troubleshooting another problem) I am stuck.

Tried typing "uninstaller" in terminal but uninstaller is not install and it asks me to install wine to get uninstaller!

Also, removing the application folder in c:/program file/ did absolutely nothing as well.

Questions:
1) How can I cleanly uninstall any software in Wine at this point?
2) If it is an issue with Wine update that I did, how can I roll back to earlier working version of it?

--------------------------------------
Unbuntu 9.10 dual-boot with Window Vista
AMD Athlon 64x2
4GB DDR2

---

### Post by sokam on 2009-12-09
No one have any idea?

---

### Post by elgandoz on 2009-12-11
I confirm it...I have same version and same problem...
I erased the Wine Menu, and I don't know the command line for the "Uninstall wine software" dialog.
Also typing "Unistaller" return an error in console (It suggest to run sudo apt-get install wine, XD)
Does someone can check wich command line appears in his "Unistall wine softw" menu?

---

### Post by elgandoz on 2009-12-11
Solution Found:
Simply run "wine uninstaller" in term or command line (without quotes). The wine uninstall dialog will appear

---

### Post by 3rdalbum on 2009-12-11
If you need to use the older program version in an emergency, you could create a new user account on your system and install the program in Wine on there.

---

### Post by claracc on 2009-12-24
> Solution Found:
Simply run "wine uninstaller" in term or command line (without quotes). The wine uninstall dialog will appear

It doesn't work, apparently the program i want uninstall "crocodile 605" is uninstalled but it is not true. I can run the program after uninstallation.

What i obtain is the following:

 wine uninstaller
fixme:advapi:LookupAccountNameW (null) L"clara" (nil) 0x33f3e4 (nil) 0x33f3e8 0x33f3dc - stub
fixme:advapi:LookupAccountNameW (null) L"clara" 0x135398 0x33f3e4 0x135dd0 0x33f3e8 0x33f3dc - stub
err:msi:msi_dialog_set_font No font entry for L"VerdanaBold14"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 11 ignored L"CreateFolder" table values

Is there a solution to truly uninstall software in wine?

Thanks in advance

---

