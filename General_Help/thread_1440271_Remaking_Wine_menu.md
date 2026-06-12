---
title: "Remaking Wine menu"
date: 2010-03-27
forum: General Help
---

### Post by smitty96 on 2010-03-27
In my quest to completely reinstall Wine because it was acting strange, I removed the Wine part of the main menu. However, after reinstalling wine, it's not there. How would I go about making it again?

-Tim

---

### Post by codger76028 on 2010-03-27
Good question.  I had the same problem.  I couldn't figure out how to do it, so I reinstalled Ubuntu and went from there.  There ought to be a simpler way.  I need to go back to an earlier version of Wine now - it's making my old genealogy program funky - but am afraid to mess with it since I expect to run into this problem again.

Codger76028

---

### Post by karthick87 on 2010-03-27
Goto your home directory,search for the folder named .wine(which is hidden),delete the entire folder..And then goto terminal and type **winecfg **this  will recreate all the wine configuration files..

---

### Post by smitty96 on 2010-03-27
That recreates the wine folder, but the main menu is still the same...

---

### Post by SPr on 2010-03-27
Take a look at
```

man xdg-desktop-menu 

```
I've never had to use it so can't offer any advice other than RTM, sorry.

---

### Post by Peter7K on 2010-07-09
[http://ubuntuforums.org/showthread.php?t=632090]("http://ubuntuforums.org/showthread.php?t=632090")

Ah ha! Finally found it. For anyone else that has this problem, after wine is installed:


```
sudo apt-get --purge remove wine
sudo rm -r /home/username/.config/menus
```
Then Log Off and and Log On back to restart the desktop.

And it's right back where it should be

---

### Post by 2uRcJQ34G1 on 2010-10-11
[SIZE="5"][COLOR="Red"]Caution[/COLOR]: _The above commands will delete you entire menu and all its prefrences._[/SIZE]

The Alternative:
[LIST=1]
[*]Go to your home directory
[*]Locate the ".config" folder
[*]Locate "menus" folder
[*]Open applications.menu
[*]Locate the part of the file where it says Wine within the '[Menu] & [/Menu]'
[*]It should stay [/Deleted] before the [/Menu]
[*]Delete the entry: everything between [Menu] & [/Menu]
[*]Save and then close the file
[*]Right click on the Applications and enter the Edit Menus
[*]You should now see the Wine in the list
[*]Enable it and eh voila!
[/LIST]

Could you also please mark this thread as SOLVED.

Cheers.

---

