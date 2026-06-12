---
title: "Need help with applications menu repair"
date: 2009-12-31
forum: General Help
---

### Post by L a r r y on 2009-12-31
I am trying to resolve an issue with the applications menu with regard to Wine.  A couple Windows programs didn't install right, but they have permanently attached themselves to the Wine Programs menu.

I uninstalled Wine and blew .wine, then reinstalled Wine, and let it recreate .wine.  OK, now with a fresh install of Windows XP, in effect, I still have two programs in the Wine menu.

I used the menu editor to remove some programs that had been uninstalled, but were still listed.  But these two will not delete.  They can hide if I uncheck them, but they cannot delete.

So I'm thinking to myself, let's see, in Windows, a menu is a folder and the menu contents are shortcut files.  If in Ubuntu the menu is similarly configured, I may have a permissions problem with these shortcuts.

The following discussion uses /home/me to refer to my home directory.

In hunting around I did find the file responsible for the applications menu. In
**/home/me/.config/menus** folder is **applications.menu**, a text file.

Here, then is that file's contents:
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Menu>
				<Name>wine-Programs-GoldWave</Name>
				<DirectoryDir>/home/me/.local/share/desktop-directories</DirectoryDir>
				<Deleted/>
			</Menu>
			<Menu>
				<Name>wine-Programs-Winamp</Name>
				<DirectoryDir>/home/me/.local/share/desktop-directories</DirectoryDir>
				<Deleted/>
			</Menu>
			<AppDir>/home/me/.local/share/applications</AppDir>
			<Exclude>
				<Filename>alacarte-made-1.desktop</Filename>
			</Exclude>
			<Include>
				<Filename>wine-Programs-Belarc Advisor.desktop</Filename>
			</Include>
			<Include>
				<Filename>wine-Programs-mailto obfuscator.desktop</Filename>
			</Include>
		</Menu>
	</Menu>
</Menu>
```

From what I can see here, "wine-Programs-Goldwave" refers to a successfully-deleted program group (submenu), the Goldwave sound editor, and "wine-Programs-Winamp" refers to a successfully-deleted Winamp program group.  These files were deleted using the delete button on the menu editor.

The "wine-Programs-Belarc Advisor" and "wine-Programs-Mailto Obfuscator" are two program launchers that refuse to be deleted.

Can I edit this file in gedit to eliminate these programs from the menu, or should I just delete applications.menu?  It appears that the bulk of the applications menu is in the /etc/xdg/menus/applications.menu file, and that this menu file just creates the Wine menu.

So if I blow it away, and reinstall Wine, I should recreate this file.

Any advice is appreciated.

---

### Post by L a r r y on 2009-12-31
I solved the problem by saving the applications.menu as a backup to my Desktop, then blowing it away in .config/menus; I also looked in .config/menus/applications-merged, and there found a wine-Programs.mernu file containing the two Windows programs that will not go away.  I saved-as to my Desktop and then blew it away.

So now, with .config/menus containing only a settings.menu and an empty applications-merged folder, and with Wine still uninstalled and .wine deleted, I installed Wine.

I installed the latest Winamp 5.57.  I went to the Winamp.com download page, clicked on Download, and it downloaded, and ran the installer.

Winamp still was not showing in the Applications menu, but a quick check with the menu editor found it there, but unchecked, and therefore, hidden.  I checked it and it now appears as it should on the menu.

Under this latest version of Wine for Ubuntu 9.04, which is considered to be Beta when you get it from winehq, Winamp plays without a hickup at the start as I have sometimes seen at the start in the past.

Moving the Winamp program window across the desktop is tricky.  I have to go slow, otherwise it can flip off of the screen, and disappear.  I can move the playlist editor and the graphic equalizer windows separately without much fuss, and they will dock together.  I then carefully, and slowly move the Winamp main window into place, and it will dock to the others.

Next time I start Winamp, it is in the position where I last left it.  I can right-click on the  Winamp panel button (on the 'task bar") and use the Linux Move feature to easily move the Winamp main window around, but that doesn't store its location in Windows, and the next time it is started, it appears where Windows last saw it.

Since the fresh install, I no longer have the issue with the Winamp Options Menu dialog or open-file dialogs being behind one of Winamp's windows.  These dialogs come up in front of all three sections of Winamp that I have displayed:  Main window, EQ and Playlist.

I can use Direct Sound output and configure fades and gapless track changes.  I can scroll the track title in the Task Bar.

Winamp has no Media Library.  Under Ubuntu 8.04, it did have a Media Library, but it was only half-usable, but that 8.04 installation was on a different motherboard and video card, which machine is now out of service.

Winamp has a graphic EQ.  That is one feature that I have not seen in the Linux software stockpile.

---

