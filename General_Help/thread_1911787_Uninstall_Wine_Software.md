---
title: "Uninstall Wine Software"
date: 2012-01-19
forum: General Help
---

### Post by TYPELiFE on 2012-01-19
I'm trying to uninstall VC++ 2005 because I have two different versions installed and I read that they conflict with eachother causing problems with some emulated programs. When I go to "Uninstall Wine Software" and click the "Remove" button on either of these two installations of the VC++ redistributable, it just sits and thinks then the uninstall interface returns to ready mode without doing anything. Same thing if I click modify.

Any ideas?

---

### Post by BC59 on 2012-01-19
Open the Wine Configuration (winecfg) and check in the first tab-Applications, if the application to remove is there. Then select it and press remove application.
The last solution is to remove it, physically. Go to home and press CTRL+H to see the hidden files. Then open the folder .wine and search in the c:\Program Files to find the program. Then delete it. If you like to make a backup before, copy the whole folder .wine to another place. If you are not satisfied with the result of the removal, you can delete the damaged folder and replace it with the original .wine you have copied.

---

