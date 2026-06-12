---
title: "Mint Menu Doesn't Work On 11.04"
date: 2011-03-31
forum: General Help
---

### Post by ozone702 on 2011-03-31
Any word on Mint Menu working on Ubuntu 11?  I couldn't get it to load.  I don't have the exact error, but I did allow the error report to be sent up to Conical.

---

### Post by Frogs Hair on 2011-03-31
Hi,
 
I could not find a ppa or .deb package for the mint menu that is compatible with Ubuntu 11.04 . You may have to wait until 11.04 is released.
 
If have have found something that is supposed to work on Natty it could just be the that natty is currently unstable.

---

### Post by ozone702 on 2011-03-31
> **Frogs Hair said:**
> Hi,
 
I could not find a ppa or .deb package for the mint menu that is compatible with Ubuntu 11.04 . You may have to wait until 11.04 is released.
 


Thanks.  I've found that I really can't live without it.  Cononical should really consider making it, rather than Unity, as default... oh well.

---

### Post by idontkn0w123 on 2011-05-02
1) sudo gedit /usr/lib/linuxmint/mintMenu/mintMenu.py
2) line 40 replace 
```
libc = dl.open('/lib/libc.so.6')
``` with
```
libc = dl.open('/lib/i386-linux-gnu/libc.so.6')
```
(still produces some errors if you open in terminal, but at least mintmenu works..)

hm, seems that changing for example favorites icon size does not work, it does not save settings when changed.. if someone knows what to do.. pls help :)

---

### Post by Freelance Physicist on 2011-06-19
The [Webupd8 team](http://www.webupd8.org/) has ported the Mint Menu to Ubuntu.  From [http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html](http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html) :

> Open a terminal (Start -> Accessories -> Terminal) and copy the following:
```
sudo add-apt-repository ppa:webupd8team/mintmenu && sudo apt-get update
```

And then install MintMenu in Ubuntu using the following command:

```
sudo apt-get install mintmenu
```

Once you install it, right click on a Gnome panel, select "Add to panel" and then search for and add "MintMenu".

Despite what the page says, the team has updated the ppa for Natty.

---

