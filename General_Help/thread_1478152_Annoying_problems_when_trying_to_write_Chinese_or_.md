---
title: "Annoying problems when trying to write Chinese or Japanese (IBUS)"
date: 2010-05-09
forum: General Help
---

### Post by hihihi100 on 2010-05-09
Hi there:

Me, like many others, used to use SCIM to write in Chinese or Japanese. SCIM hasnt been updated for like 5 years, and the standards in use for Ubuntu (including 10.04, the version I use) is IBUS... However, up to today, I havent been able to see or use the menu with all the different Input Methods options (I mean the list with all the languages and the different input methods available, something that makes the change of the language quite easy), like was the  case with SCIM, when I click on the keyboard icon that appears in the upper panel, I always see “No input window”, I can see a blank square that, if passed on with the mouse, will make “Switch input method” appear, but nothing else to confirm which Input method I have changed to, and, I cannot understad why, everytime I go to System – administration – language support, in the inpout method combo box, GCIN (has been uninstalled), UIM (also uninstalled) and SCIM (uninstalled too) keep appearing in the "keyboard input method system" combo box.


Plus, everytime I click on the IBUS icon, I get:


```
IBUS daemon is not started, do you want to start it now?
```


to which I click yes, to get to:



```
IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
```


I have already added those lines to the very end (bottom of the page) of the amentioned file, but I keep receiving those two warnings.



Please help

---

### Post by Irihapeti on 2010-05-09
I have had some problems with both Scim (which I still use) and iBus in Lucid. I suspect that there are a few bugs here. Logging out and in again is usually all that's needed, but I've had to reboot on two occasions to get them to behave properly.

If you are still getting uim and gcin appearing in the keyboard input method system box, I suspect that there are still some configuration files on the system. Open synaptic and check to see if they are listed in the "not installed (residual configuration)" section, and mark them for complete removal if they are.

I don't know why that iBus message refers to .bashrc, because that's not the main file that controls non-latin input methods.

In the directory .xinput.d in your home directory, you should see a file that has the name of your locale. (In my case it is "en_NZ".) It's a link to a file in the /etc directory, so you can't edit it directly. Please post the contents of it here. It may give us a clue as to what's happening.

---

