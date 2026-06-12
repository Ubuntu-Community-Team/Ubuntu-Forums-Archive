---
title: "Cleanup Wine Garbage 10.04 x64"
date: 2010-12-09
forum: General Help
---

### Post by rdunnion on 2010-12-09
I have been experimenting with Wine. I have installed and uninstalled many programs. I couldn't get most to work and I think maybe 1 uninstalled cleanly. How can I clean up the remnants of uninstalled programs or programs that wouldn't uninstall? When the menu to choose a program to open a filetype is opened I have a half dozen entries for itunes for example due to reinstalls , to give you an idea of what I want to clean up. I want it as clean as possible too. Any help would be awesome. I am running 10.04 x64 on a HP dv9225us with all current updates.

---

### Post by I'mGeorge on 2010-12-09
to uninstall your program cleanly you should use the command
```

sudo apt-get --purge remove wine

``` 

Anyway you should check if the folder ~/.wine still exists, and if it does just delete it. Deal with the remained menu entries if you're using GNOME this way [http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

---

### Post by rdunnion on 2010-12-09
thanks George. The problem is I have 1 game installed that I like very much. Maybe I could backup the saved game then do as you say? Then reinstall wine and my game.

---

### Post by bodhi.zazen on 2010-12-09
You are best off deleting your .wine directory and re-installing your application.

You do this with (warning, this will delete your installed applications in wine):

```
rm -rf ~/.wine
```

Back up any data you wish to keep from ~/.wine and replace it after.

Removing and reinstalling wine itself , with apt-get, will not help (as that will not delete ~/.wine).

I know that is not the answer you want, but it is easier that way. debugging wine is often difficult, and for complex applications I keep a separate custom .wine for each application.

---

### Post by rdunnion on 2010-12-09
Found the last step to this problem here:
[http://art.ubuntuforums.org/showthread.php?t=1520195]("http://art.ubuntuforums.org/showthread.php?t=1520195")

---

### Post by I'mGeorge on 2010-12-11
> **rdunnion said:**
> thanks George. The problem is I have 1 game installed that I like very much. Maybe I could backup the saved game then do as you say? Then reinstall wine and my game.

Well yeah, most of the games that aren't so pretentious could be installed in another partition or directory and still work, even if you delete ~/.wine so you can completely reinstall it.

---

