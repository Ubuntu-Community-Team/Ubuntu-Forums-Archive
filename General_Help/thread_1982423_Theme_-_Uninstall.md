---
title: "Theme - Uninstall?"
date: 2012-05-18
forum: General Help
---

### Post by praveenkumarpon on 2012-05-18
Hi, I am new to Ubuntu and I recently installed a theme for Unity.

Since I didn't like it, I wanted to uninstall and I didn't know how to. So I just changed the Theme to default in the Appearance settings.

I had installed the theme as suggested by upubuntu.com:  
[http://www.upubuntu.com/2012/02/12-new-best-gnome-shell-themes-for.html](http://www.upubuntu.com/2012/02/12-new-best-gnome-shell-themes-for.html)

The commands I used are as follows:
mkdir ~/.themes
sudo apt-get install gnome-tweak-tool
wget -O back_n_black_blue_edition.zip [http://goo.gl/jfbxW](http://goo.gl/jfbxW)
unzip back_n_black_blue_edition.zip -d ~/.themes
gsettings set org.gnome.desktop.interface gtk-theme 'Back n Black-Blue Edition'
gconftool-2 --set --type string /apps/metacity/general/theme 'Back n Black-Blue Edition'

I need to be sure if the theme wouldn't cause any issues to Ubuntu. How to remove it completely?

Thanks.

---

### Post by Frogs Hair on 2012-05-18
If installed in file system usr/share/themes use gksudo nautilus in the terminal move to the directory above and delete the theme folder.

If installed in home .themes open the home folder use Ctrl + h to display hidden folders and delete from the .themes folder.

You can also use the following in the terminal if you know the full theme name```
sudo apt-get remove ******-theme 
``` 

The synaptic package manager will also work if installed.

---

### Post by praveenkumarpon on 2012-05-18
> **Frogs Hair said:**
> 
If installed in home .themes open the home folder use Ctrl + h to display hidden folders and delete from the .themes folder.


Yup, it was in .themes, I deleted it.
Thanks.

---

