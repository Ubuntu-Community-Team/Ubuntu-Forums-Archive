---
title: "Restoring Wine and links in Main menu"
date: 2009-06-27
forum: General Help
---

### Post by DeMus on 2009-06-27
Some time ago I used Wine, then I uninstalled it since I didn't use it anymore.
I also deleted the Wine entry in the main menu, using Sytem > Preferences > Main Menu.

Now I want to use Wine again, I installed it but I don't see it in the main menu like it use to be. I can add it manually but I have no idea what to add.
Is there a way to restore things, maybe a complete menu restore to get the Wine entry back? Or what else is possible?

---

### Post by t0p on 2009-06-27
If you right-click on where it says 'Applications' on the top panel, you'll get a menu which has the option 'Edit Menus'.  This will allow you to edit the Applications menu.

---

### Post by geirha on 2009-06-27
If you chose to delete them from the menu (rather than hide them), I think they are completely gone. If you have a backup of your home directory from before that deletion, then try restoring all files starting with "wine" in ~/.local/share/applications/

---

### Post by DeMus on 2009-06-27
> **t0p said:**
> If you right-click on where it says 'Applications' on the top panel, you'll get a menu which has the option 'Edit Menus'.  This will allow you to edit the Applications menu.

Yes, I know, it's the same as what I mentioned in my first post. The question is what should I add here?
I installed a program which should run under wine but it does not appear in this menu. Also when I start it manually by entering the .wine folder it won't run.
So, how to restore everything related to Wine?

Thanks for you help.

---

### Post by DeMus on 2009-06-27
> **geirha said:**
> If you chose to delete them from the menu (rather than hide them), I think they are completely gone. If you have a backup of your home directory from before that deletion, then try restoring all files starting with "wine" in ~/.local/share/applications/

No, I don't have that. What I wonder is, when I installed Wine the first time, the menu is added. Now, after having deleted it completely, I install Wine again and the menu is not added to the Application menu.
Why not.
Any other ideas? I sure can use them. Thanks.

---

### Post by geirha on 2009-06-27
I don't think those menu entries are installed by the wine-package, but rather by wine itself the first time you run it, or the first time you install something with it. I think the easiest way to get those menu entries back, is to install the windows applications again. Give it a try with a small program if possible

1. move your .wine dir away, but don't remove it.
```
mv ~/.wine ~/.wine.backup
```

2. Install the program in the same location as last time. A new .wine dir will be created, and menu entries should be added.

EDIT: 2b. Before doing step 3, run
```
find ~ -mmin -5 | less
``` This will list all files in your home folder that has changed within the last 5 minutes (adjust the number if the install took longer). In particular, look at the files that have changed ouside the .wine dir. Like .local/.

3. Once done, move your original .wine-dir back
```
mv ~/.wine ~/.wine.temporary
mv ~/.wine.backup ~/.wine

```

---

### Post by DeMus on 2009-06-27
Found it:
[http://ubuntuforums.org/showthread.php?t=610115]("http://ubuntuforums.org/showthread.php?t=610115")
In post 4 it says to open System ? Preferences > Main menu and use the revert button. This brought my old wine menu back.
Thanks for all the help. I really appreciate it.

---

### Post by geirha on 2009-06-27
Really? well that's nice to know. And surely easier than my approach :)

---

### Post by mc4man on 2009-06-27
The other manual approach (if revert didn't work or to only effect a single change back) is to go to 
~/.config/menus/applications.menu
You can edit changes out in there if done carefully, when done incorrectly then the Applications drop down won't open and then you'd   have to  correct your mis-edit or just delete the file.

Ex. with wine, removing the red would restore to menu, while leaving other changes. (backspace the line <deleted/> was on
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<Include>
			<Filename>totem-xine.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
		<Exclude>
			<Filename>totem.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>
```

---

