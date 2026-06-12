---
title: "Problems with Flash intallation"
date: 2009-08-31
forum: General Help
---

### Post by Pharohs on 2009-08-31
I have found way too many sites detailing how to install Flash on my system.  I am running Ubuntu 9.04.  When testing my install on the Adobe website ([http://www.adobe.com/products/flashplayer/action/](http://www.adobe.com/products/flashplayer/action/)).  I get nothing.  When, the site offers to install Flash player 10, the installation fails.  When I type "about: plugins" in Firefox, I get this:

 File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

I would like to uninstall what I have, and start fresh, but I don't know how.  I tried the package installer, but then I get an error later which says that the "flashplugin-installer" is still on the system, which prevents a new installation.

I had hoped that this would have been addressed and fixed over the past year, but, nope.


My head is spinning. Can anyone help?

---

### Post by Lampi on 2009-08-31
libswfdecmozilla is another variant of flash player - it's not the one from adobe you are looking for. If you no longer want to use it, uninstall it like this:

```
sudo aptitude purge swfdec-mozilla
```

Now you install the flash player of adobe:

```
sudo aptitude install adobe-flashplugin
```

make sure you only have one flash player installed at a time - otherwise it might conflict your browser setup

---

### Post by Pharohs on 2009-08-31
It worked.  Thank you so much. :)

---

### Post by igriego on 2009-09-05
i tried this but i get:



isaiah@Fizzlicious:~$ sudo aptitude install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "adobe-flashplugin"
Couldn't find any package whose name or description matched "adobe-flashplugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by BslBryan on 2009-09-06
> **igriego said:**
> i tried this but i get:

Couldn't find any package whose name or description matched "adobe-flashplugin"


What version of Ubuntu are you running?

Try 
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by igriego on 2009-09-13
ubuntu 9.04

---

### Post by BslBryan on 2009-09-14
Did you try the command I gave you?  Also, in Jaunty, this command should take care of everything you need:
```
sudo apt-get install ubuntu-restricted-extras
```
:-)

Moved to general help.

---

### Post by sdunlapa on 2009-10-11
Thanks you
```
sudo apt-get purge swfdec-mozilla
``` worked for me. I now only have *flashplugin-installer* and am running Jaunty 9.04.

---

