---
title: "Uninstall WINE"
date: 2009-10-21
forum: General Help
---

### Post by andycastille on 2009-10-21
I installed WINE to run Windows programs, and it stopped working. I found instructions to remove it in System -> Preferences -> Main Menu. Now it won't install again because it still says WINE under Applications, but when I open the Wine sub-menu, it's empty. How can I remove the Wine option from my Applications menu? HELP!!!

---

### Post by GeneralSpecific on 2009-10-21
I assume you are running Standard Ubuntu, with Gnome.

I don't have Gnome installed now, so I can't check on the 'instructions' you mentioned, but I think I can help you reinstall Wine

It *sounds like* all you did was remove the Wine program launcher from your menu, you didn't uninstall wine.



If you want to **reinstall wine** try this:

[INDENT]Open [COLOR="Red"]Synaptic[/COLOR] (It is in your menu somewhere, probably under Administration)

Once it opens type "[COLOR="Blue"]wine[/COLOR]" in the Quick Search box at the top, and it should show up as the first result on the right.

If it doesn't, make sure that "[COLOR="Blue"]All[/COLOR]" is selected on the left.

If it is installed the check box should be [COLOR="DarkGreen"]green[/COLOR] and it will say what the installed version is.

Right click on the green box and select "[COLOR="Blue"]Mark for Reinstallation[/COLOR]"

Click "[COLOR="Blue"]Apply[/COLOR]" and then "[COLOR="Blue"]Apply[/COLOR]" again when it asks for confirmation.[/INDENT]



If you have any problems, or have more questions, just ask.

--Ryan

---

### Post by andycastille on 2009-10-22
THANK YOU!! It's working so far... OOPS! It didn't replace the WINE menu. When I open menu editor, I click it in in the side and there are no other options inside.:confused:

---

### Post by GeneralSpecific on 2009-10-23
Hmmm...

Like I said, I'm not running Gnome right now, but here are a few posts that might help you:

[INDENT][http://ubuntuforums.org/showthread.php?t=594410&page=3]("http://ubuntuforums.org/showthread.php?t=594410&page=3")

[http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu+problem]("http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu+problem")[/INDENT]

They are older threads, but hopefully something there will work.

-Ryan

---

### Post by andycastille on 2009-10-23
No luck; the first link got moved to a new site, which told me they then moved again 3 more times. The second link is for a different version of Ubuntu, so still no help. Where are the programs and menus stored? The second link listed where, but I couldn't find it under /home/users [missing folder]

---

### Post by GeneralSpecific on 2009-10-23
I'm not sure if your file is missing, or merely **hidden**.
Any file or directory that starts with a period (*.something*) is a hidden file.

To see these when looking at your home directory in your file browser just type [COLOR="Blue"]ctrl+h[/COLOR] and they will show up.

That should help you find the file talked about here:

> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing

And here is the directions from the _thrice moved first link_.
> 
10.)how to fix disappearing menu icons and shortcuts

Go to: (username is your log in name)

/username/.config/menus/

delete applications.menu

and settings.menu


now you'll just have to re-hide stuff that you've hidden before but this should fix any problems ...
[COLOR="Red"]
If you want to try these suggestions, Here is what I would suggest:[/COLOR]

Try the **first suggestion** by doing this:

Open up a [COLOR="Blue"]terminal[/COLOR] (The terminal can be found at Applications menu -> Accessories -> Terminal) and type these commands, one at a time:

```
cp ~/.config/menus/applications.menu applications.menu-bak

cp ~/.config/menus/settings.menu settings.menu-bak
```

That backs up the menu files we are going to play with, and puts them in your home directory

Then type this to open your menu file:

```
gedit ~/.config/menus/applications.menu
```

Follow the directions above and remove the <Deleted/> part from the file.

Save the file and close gedit.

See if that works.  If not, and you want to try the **second suggestion** (deleting the files and letting them be rebuilt automatically)

Type this:

```
rm ~/.config/menus/applications.menu

rm ~/.config/menus/settings.menu
```

Hopefully then your menu's will be rebuilt for you.

**If it doesn't work**, [COLOR="RoyalBlue"]Don't panic[/COLOR] :P we can put everything back with these two commands:

```
cp ~/applications.menu-bak ~/.config/menus/applications.menu

cp ~/settings.menu-bak ~/.config/menus/settings.menu
```

Like I said at the outset, I can't double check this myself, but these suggestions are pretty safe and should work on a standard ubuntu install.

Let me know if it works!

-Ryan

---

### Post by andycastille on 2009-10-24
IT WORKED!!!!!!!!!!! THANK YOU SO MUCH!!!!

Now, if I mouse over Applications -> Wine -> Programs, I get a list of installed programs. How do I delete all of the files so the will disappear from the list, but the file it is pointing to will no longer be on my hard drive?

---

### Post by Camilia on 2009-10-25
> **andycastille said:**
> IT WORKED!!!!!!!!!!! THANK YOU SO MUCH!!!!

Now, if I mouse over Applications -> Wine -> Programs, I get a list of installed programs. How do I delete all of the files so the will disappear from the list

If you just want them off the list you can go to Systems> Preference > Main Menu. Then go to the category that are in and remove them. They will still be on the computer.

---

### Post by andycastille on 2009-10-25
Let's face it: I'm going to have to re-install Ubuntu, aren't I? I'll have to anyway, because I ordered Windows 7, and my ENTIRE hard drive will need re-formatting. All of the partitions will be removed and the disk will be empty. I will put on Windows 7, install Windows XP again, (if it ends up that I can't run CoffeeCup HTML Editor and FileZilla in Windows 7) and then install Ubuntu. I WILL wait for my Ubuntu 9.10 disk to come so that I can get the latest version. This forum is closed if I can't fix WINE.

---

### Post by andycastille on 2009-10-25
Well, now my WINE menu is gone completely! I can't even find it in the System -> Preferences -> Main Menu anymore! WINE is no longer installed. That code that got posted a while ago, the code that opens a window and I had to remove the <Deleted> part? What part of code can I remove so that it will be like I never had WINE at all?

---

### Post by GeneralSpecific on 2009-10-25
First off...RELAX!  

The joy of Linux is it is infinitely customizable, but it takes some learning.

Rarely do you have to do a fresh install to fix a problem...but you have to be patient and willing to do a little learning and a little work.  (Though you are correct, that may be different if you want to install a new dual boot system with windows 7)

I honestly don't understand _what your current problem is_.  
If you would like more help you'll have to give a clear and detailed description of **what you did** and **what you want**.

To clear up one bit of confusion it seems you may have...

[INDENT]When you delete something from the menu...it only deletes the entry, or link to the program...not the program itself.

If you want to **uninstall a windows program** that you installed with wine, you have to run the uninstall program just like you were on windows.

Use this command:

```
wine uninstaller
```

And uninstall the program from there.

If you want to install or remove a program(or package) **from Linux** (such as uninstalling wine).  You need to run *"Add/Remove programs"*, or *"Synaptic" package manager* to do it.[/INDENT]

Don't give up on Linux, for me it has become more that just on OS...it is a hobby, and I am addicted!

-Ryan

---

