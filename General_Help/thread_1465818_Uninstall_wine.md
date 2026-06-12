---
title: "Uninstall wine"
date: 2010-04-29
forum: General Help
---

### Post by dzwestwindsor on 2010-04-29
I did sudo apt-get remove --purge wine, and im made sure that nothing was left in the packages. 


But if i go to Applications => wine , its still there. but nothing works.. but the menu is still there.

I also removed the .wine folder. 

How do i get rid of that wine menu completely? Thanks

---

### Post by Rasa1111 on 2010-04-29
try 

sudo apt-get autoclean

or

sudo apt-get autoremove

> If you have installed and uninstalled a lot of applications, chances are your system is infected with a lot of dependencies files that you have absolutely no use for. Here are some useful commands to get rid of any partial package and remove any unused dependencies:


 Cleaning up of partial package:
 sudo apt-get autoclean


 Cleaning up of the apt cache:
 sudo apt-get clean


 Cleaning up of any unused dependencies:
 sudo apt-get autoremove


 A good practice to avoid any left behind is to use the *autoremove* command whenever you want to uninstall an application.


 sudo apt-get autoremove application-name

that cleans up all the residual 'junk' leftover from removed packages.

 or, in synaptic, go in and clean up residual config packages..

good link... 
[http://panupongsk.blogspot.com/2010/03/once-in-while-you-may-want-to-do-some.html](http://panupongsk.blogspot.com/2010/03/once-in-while-you-may-want-to-do-some.html)

---

### Post by dzwestwindsor on 2010-04-29
thank you, i ran all those commands, and checked everywhere, but the wine still appears in the menus.

This is driving me nuts, i searched for any file that had "wine" in it, and i removed them all, and still, the menu is there. this is ridiculous. does anyone have ideas?

---

### Post by Rasa1111 on 2010-04-29
darn, sorry...  lol

have you used synaptic package manager to try cleaning it yet? 

this is from link i posted above....

> **Get rid of old residual config package**

 When you upgrade a software to a later version, the package of its previous version will still be left behind in the system. You will be able to free up some space by eliminating the old residual config package
 Open up your Synaptic Package Manager (*System-> Administration-> Synaptic Package Manager*). On the left, click on the *Status* button. You will see a few options appear on the top left pane. If there is a *Not Installed (residual config)* option, click on it. This will reveal all the residual config package in the system.
[IMG]http://maketecheasier.com/wp-content/uploads/2008/10/synaptic1.jpg[/IMG]

Check the box beside the package and select &#8220;Mark for complete removal&#8221;. Click [I]Apply.

[IMG]http://maketecheasier.com/wp-content/uploads/2008/10/synaptic2.jpg[/IMG]

[/I][I]

? 

[/I]also... 
have you to tried a restart/reboot?

 Im not sure what else to do.......
sorry, im kinda n00b myself..

 but i remember i had this problem as well, and got it taken care of..
somehow...  lol* *

---

### Post by mc4man on 2010-04-29
If it continues to show (and you don't want to simply disable in edit menus) then places to look -> home - show hidden files

~/.wine
~/.local/share/desktop-directories/ (wine-<whatever>.directory
~/.local/share/applications/ ( look for .desktops with wine in name

---

