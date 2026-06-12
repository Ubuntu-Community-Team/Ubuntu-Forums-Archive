---
title: "Help! Screwed up Avant Window Navigator, need reinstall"
date: 2010-10-27
forum: General Help
---

### Post by X-Windows on 2010-10-27
Messing around with the new AWN multi dock feature and accidentally deleted all docks, now I have a 50 px region at the top of the screen I cant use, and no docks at all! I have uninstalled/reinstalled multiple times and tried to clean out as many preference files as I could find but every time I reinstall AWN it uses my old, screwed up preferences leaving me at the same place as I started. 

I used these instructions to install and uninstall (reverse install I guess) and deleted the relevant files in /user/share and ~/.gconf/apps. Beyond that I'm stumped, AWN must be storing my old configuration somewhere I just cant find it. Any help would be greatly appreciated, AWN multi-dock is a great feature I miss dearly...

---

### Post by Frogs Hair on 2010-10-27
The AWN theme you were last using gets stored in Appearance Preferences > customize > icons . delete that also and try a reinstall.

---

### Post by moonbeam on 2010-10-27
Start awn-settings... you should be able to just right click on that 50px region and choose dock preferences... though you can just start it from a terminal if need be.  

It will allow you to configure the current dock.  I'd suggest adding the Launcher/Taskmanager applet to start with and then move it / configure it as desired.

As as a side note some work has recently went into trunk that will have an effect on the multiple dock support including, a simple launcher applet, single instance only of Launcher/Taskmanager (use simple launcher for additional launchers in extra docks) and proper support of multi-panel intellihide.  Expect in the next awn-testing ppa update.

---

### Post by smellyman on 2010-10-27
not in front of my Ubuntu pc, but I bet there is a .awn or .avant config file or directory you can delte or rename.  The kill awn or logout and back in and it will load  default settings....

---

### Post by X-Windows on 2010-10-27
Yea, I found a .avant something in the home folder and in the locations previously specified but deleting them did nothing. When AVN loads it pushes all my windows down for the 50 px region but I cant right click anything ro get into the dock settings - there are no docks to right click...

---

### Post by moonbeam on 2010-10-27
> **X-Windows said:**
> Yea, I found a .avant something in the home folder and in the locations previously specified but deleting them did nothing. When AVN loads it pushes all my windows down for the 50 px region but I cant right click anything ro get into the dock settings - there are no docks to right click...

Start a terminal and run awn-settings then.  I am fairly sure you will just need to add an applet and it will appear.  Unless you've done something _very_ odd it's not possible to remove the last dock completely so when you start awn-settings up it will be configuring that instance.

---

### Post by X-Windows on 2010-10-27
error when running awn-settings, I dont think I'm using murrine though...
```
username@Linux:~$ awn-settings
/home/username/.gtkrc-2.0:6: Invalid color constant 'transparent'
/home/username/.gtkrc-2.0:6: error: invalid string constant "transparent", expected valid string constant
/home/username/.themes/Khali/gtk-2.0/gtkrc:55: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
Traceback (most recent call last):
  File "/usr/bin/awn-settings", line 54, in <module>
    from awnClass import awnPreferences, awnManager, awnLauncher, awnApplet, awnThemeCustomize, awnTaskManager
ImportError: No module named awnClass

```

I was trying to delete one of the docks that had the "Remove Dock" button greyed out. Removed all applets and did something else (sorry, wasn't paying too much attention at the time... hey you can always reinstall right?) then unisntalled and reinstalled screwing something up with the preferences and end result - no awn docks when awn is running and cant open the awn-settings to create a new one/delete whatever is taking up the top 50 pixal space...

---

### Post by moonbeam on 2010-10-28
> **X-Windows said:**
> error when running awn-settings, I dont think I'm using murrine though...
```
username@Linux:~$ awn-settings
/home/username/.gtkrc-2.0:6: Invalid color constant 'transparent'
/home/username/.gtkrc-2.0:6: error: invalid string constant "transparent", expected valid string constant
/home/username/.themes/Khali/gtk-2.0/gtkrc:55: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
Traceback (most recent call last):
  File "/usr/bin/awn-settings", line 54, in <module>
    from awnClass import awnPreferences, awnManager, awnLauncher, awnApplet, awnThemeCustomize, awnTaskManager
ImportError: No module named awnClass

```

I was trying to delete one of the docks that had the "Remove Dock" button greyed out. Removed all applets and did something else (sorry, wasn't paying too much attention at the time... hey you can always reinstall right?) then unisntalled and reinstalled screwing something up with the preferences and end result - no awn docks when awn is running and cant open the awn-settings to create a new one/delete whatever is taking up the top 50 pixal space...

hmmm...  yeah that's screwed up.  My suggestion at this point.

1) start synaptic and remove all awn packages.
2) Install all the awn* and avant* packages listed at [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa).
3) Exit synaptic.
4) From a terminal do a 'killall gconfd-2'
5) Try starting awn... if nothing appears then try starting awn-settings from a terminal.

---

### Post by X-Windows on 2010-10-28
Is fixed!

Uninstalled/removed anything having to do with awn or docks (except gnome) THEN deleted all the config files in the aforementioned locations. Reinstalled via the website posted and ran avant-window-navigator and voila! all the docks back. The 50 pixel area was due to the invisible dock being set to panel instead of always visible.

---

### Post by moonbeam on 2010-10-28
> **X-Windows said:**
> Is fixed!

Uninstalled/removed anything having to do with awn or docks (except gnome) THEN deleted all the config files in the aforementioned locations. Reinstalled via the website posted and ran avant-window-navigator and voila! all the docks back. The 50 pixel area was due to the invisible dock being set to panel instead of always visible.

Good to hear.  In general awn devs do not recommend uninstall/reinstall as method of fixing configuration issues.  Basically it doesn't really help and leads to issues like the missing "AwnClass" above.  Assuming one doesn't do the uninstall/reinstall approach the worst that can happen in the huge majority of cases is needing to run awn-settings from a menu or terminal.  That being said, _occasionally_ killing the awn config entries is required (this is not as straightforward as one might think) though it almost certainly was not actually required in this case :-)

Glad you got everything up and running again though (next time just run awn-settings from a terminal) and remember you cannot get rid of the last dock instance.

---

### Post by X-Windows on 2010-10-28
Yea, something got screwed up and awn-settings wouldn't run nor would the docks show, although the program was running... Glad to have it fixed...

In love with AWN minimalism! If only it had an applet for Cardapio...
[http://img200.imageshack.us/img200/2746/screenshotmq.png](http://img200.imageshack.us/img200/2746/screenshotmq.png)

---

### Post by kerry_s on 2010-10-28
interesting set up.

your still using the normal panel? (left bottom corner)

you know you can make a launcher for cardapio.
[http://www.webupd8.org/2010/07/how-to-use-cardapio-menu-with-docky-and.html](http://www.webupd8.org/2010/07/how-to-use-cardapio-menu-with-docky-and.html)

i been embracing the orange. :)

added cardapio to mine.(my launcher's spin when clicked, that's why the icon looks funny)

---

