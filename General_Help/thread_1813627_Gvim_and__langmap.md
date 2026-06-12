---
title: "Gvim and  langmap"
date: 2011-07-28
forum: General Help
---

### Post by Romain DOUMENC on 2011-07-28
Hello,

I encounter a small problem with the package vim-gnome:
I'm using a bépo keyboard layout (French Dvorak) on an usual computer (AZERTY). In order to use the convenient vim shortcuts, I configured my **langmap** variable as:
```
set langmap=ctsr;hjkl,éz,H/,h:,G.,ouOU;rsRS,yiYI;xdXD,bdlBDL;aioAIO,f],çÇjJ;yYpP,vu,.v,:V,\\,g,TJ
```which basically remaps some keys between the two layouts in the normal mode.

Now arise the problem: when I click on the save button in the GTK interface, the last line under the cursor in the file I'm currently editing disappear, and nothing is saved! I think this button is not aware of the remapping.

Do you think it is a bug, or have I done something wrong? If it is a bug, any hints on where (esp. which option) I should look to write a patch will be appreciated.

Thanks

---

