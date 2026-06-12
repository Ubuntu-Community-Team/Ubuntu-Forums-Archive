---
title: "Remove Wine"
date: 2006-05-28
forum: General Help
---

### Post by PoisoN2003 on 2006-05-28
I was wondering how do i remove wine coz i messed up and i want to start over

i tried just reinstalling but it wouldnt do it coz it says there is a version already installed

---

### Post by Shay Stephens on 2006-05-28
Have you tried removing it in synaptic?

Go to System - Administration - Synaptic Package Manager

Then search for wine.  It should show up in the list.  Click on the checkbox and select "mark for removal".  That should do it normally.

---

### Post by Harold P on 2006-05-28
If you want to totally remove it, make sure you select "Mark for complete removal". That'll remove all the prefs and extras that could cause problems when you re-install.

---

### Post by PoisoN2003 on 2006-05-28
okey cool thx i completely forgot about that :)


i still get saem error that i got before says i dont have drive c.
When i run wineprefixcreate 
i get 
mkdir: cannot create directory `/home/poison/.wine/dosdevices/c:/windows': No such file or directory

---

### Post by ElijahLofgren on 2006-05-29
[QUOTE=PoisoN2003]I was wondering how do i remove wine coz i messed up and i want to start over

i tried just reinstalling but it wouldnt do it coz it says there is a version already installed[/QUOTE]
You probably just want to remove your wine config options.
Delete or rename your ~/.wine folder:
```
mv ~/.wine ~/.wine-broken
```

Hope this helps. :)

---

### Post by edopizza on 2006-06-16
I installed Total commander to use it with wine. 
With che command "uninstaller" I was able to remove Total commander. 
Now when I try to remove wine with Synaptic or "apt-get remove --purge", there is always a folder ".wine" left that contains 4MB of data and the Total commander link on the desktop doesnt disappear. 

How to completely get rid of the installed windows programs and of wine?

---

### Post by ElijahLofgren on 2006-06-16
[QUOTE=edopizza]I installed Total commander to use it with wine. 
With che command "uninstaller" I was able to remove Total commander. 
Now when I try to remove wine with Synaptic or "apt-get remove --purge", there is always a folder ".wine" left that contains 4MB of data and the Total commander link on the desktop doesnt disappear. 

How to completely get rid of the installed windows programs and of wine?[/QUOTE]
Uninstalling the wine program leaves your config files (the .wine folder). If you don't want them you can just delete them.

I would just remove the .wine folder and the link on the desktop. You can either delete the wine folder with your File Manager or with the following command:
```
rm ~/.wine -Rfv
```

---

