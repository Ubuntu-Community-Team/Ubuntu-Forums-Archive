---
title: "Ubuntu 12.04 Removed compiz = no dashboard/dock"
date: 2012-06-17
forum: General Help
---

### Post by deathbycopypaste on 2012-06-17
Edited to make shorter:
Fairly certain i know how i got to this point.  just not sure why my fix isnt working.  Compiz was cool, for a while.  I think i went overboard in the removal process.  This is the third time i have tried to remove this program so that "echos" of it are not present. 
After removing compiz the open windows still dodge.
I have used the command line to purge compiz and any compiz related files.  This includes unity and ubuntu-desktop.  Those were reinstalled after rebooting for the uninstalls. The windows have stopped dodging but there is presently no dock.  I have tried the command to install cairo-dock and rebooted, this did not work either, so i have removed that and purged what would not be removed. 
Any help would be appreciated.

---

### Post by zombifier25 on 2012-06-17
Unity is a part of Compiz. Removing Compiz will DEFINITELY break your desktop. Get in Ubuntu 2D mode, or install another DE.

---

### Post by deathbycopypaste on 2012-06-17
> **zombifier25 said:**
> Unity is a part of Compiz. Removing Compiz will DEFINITELY break your desktop.  
Yes, hence the reinstallation of unity and ubuntu-desktop.  Are you saying Compiz comes default on the 12.04 environment?  I installed compizconfig-settings-manager.  I thought this was something extra.  I saw that when unity and ubuntu-desktop were reinstalled, they included some compiz related packages, but those aren't related to the "extra downloads" Edit: By extra i refer to the settings provided by compizconfig-settings-manager. 
 > **zombifier25 said:**
> Get in Ubuntu 2D mode, or install another DE.
How to get to Ubuntu 2D mode?  I am able to open command line after logging in. I also see there is Unity-2D when i run dpkg -l|grep unity.  
Please clarify what you mean by DE.  do you refer to cairo-dock?  or perhaps the OS itself?

---

### Post by zombifier25 on 2012-06-17
When you reinstall Unity and Compiz, you need to run this command to reset all settings back to default:
```
unity --reset
```

And Unity 2D is a lighter, but not as beautiful version of Unity. It does not use Compiz, instead it uses Metacity for window managing. When you log in, click the tiny Ubuntu logo on your username, select Ubuntu 2D and log in in order to use Unity 2D. DE is desktop environment, e.g. GNOME, KDE, etc.

---

### Post by deathbycopypaste on 2012-06-18
I have done the unity --reset command first without and then with the reinstallation of unity.  It appears to have frozen part way through the process ( there is no ~$ line for me to continue issuing commands..just a blank line).
I have also tried (after the unity reset): sudo apt-get install gnome with a reboot.  Still no luck.

I was able to get unity 2D to work. 
I'm thinking reinstall ubuntu and call this issue solved.  

I really appreciate all of your help, i have learned many lessons with this.

---

### Post by deathbycopypaste on 2012-06-23
do not see how to change tag ...

---

### Post by zombifier25 on 2012-06-24
Thread Tools on top of page > Mark as Solved

---

