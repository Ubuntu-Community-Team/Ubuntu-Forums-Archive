---
title: "wine uninstallation and lost documents"
date: 2011-01-19
forum: General Help
---

### Post by laysforme on 2011-01-19
I was trying to completely uninstall wine from ubuntu 10.04. I searched how to do it on web and used following code:

sudo apt-get remove wine
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

Now I got wine completely uninstalled but at the same time I lost all data from the computer. Music, pictures, documents, and download folder seems to be completely new and empty. Expert, please help me how can I relocate my files.

---

### Post by 3Miro on 2011-01-19
The code looks OK to me. It should not have deleted anything from your Documents or Downloads. Lets try to find out exactly what got broken.

Try listing the folders in the terminal:
```
ls -al Downloads/
```
if this returns a list of your downloaded files, this is good news. You can try going to System -> Prefs -> Appearance and select "Clearlooks".

If not, then shutdown your computer and boot from a liveCD. You will probably have to make a HDD data recovery (which is tricky business and doesn't always work).

---

