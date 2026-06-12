---
title: "deleting/ uninstalling  of a  progran in wine"
date: 2011-09-05
forum: General Help
---

### Post by gringo8217 on 2011-09-05
hi 
 i have a issue with a program in wine that doesn't  work and i need to un -install it but it wont with the feature in wine  its a program called solid edge !! has anyone got a tip to locate it and  delete it completely !! i have searched and deleted it s files but it still shows in wine !!

---

### Post by evilsoup on 2011-09-05
If you installed it using wine, then the program files should be located in "~/.wine/drive_c/Program Files". There will be a folder called something like (in your case) solidedge; simply delete this and it'll be gone (though you will have to remove the option from your applications menu manually).

EDIT: If it's not there, just search through "~/.wine/drive_c" and "~/.wine".

EDITEDIT: waitamoment, do you mean that it shows up under the menu (APPLICATIONS>WINE>PROGRAMS)? Then you just need to manually edit your menu (right-click on APPLICATIONS, select "Edit Menu", the rest is pretty self-explanatory).

---

### Post by gringo8217 on 2011-09-05
yes  pal thats the one !!

---

