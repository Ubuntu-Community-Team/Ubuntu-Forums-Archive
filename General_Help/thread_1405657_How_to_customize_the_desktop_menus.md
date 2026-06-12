---
title: "How to customize the desktop menus"
date: 2010-02-12
forum: General Help
---

### Post by temporos on 2010-02-12
How do I rearrange or otherwise customize the desktop menus and icons in the Netbook Remix?  For example, I wish to combine the System Tools and System menus, and I want to rearrange the icons in the Favourites menu.  There is no Control Panel (that I can find) which will let me do this.

---

### Post by golanbatrac on 2010-02-12
Not sure if it's the same in netbook remix, but in the desktop version you hit alt + F2 and then type alacarte.

---

### Post by temporos on 2010-02-18
Cool.  That let me edit the panels and combine some that were there.  Thanks.

Now, I have the other desktop customization issue.  How do I reorder the icons within a particular panel (re: netbook remix)?  I can add icons by copying them from other panels, or by adding them manually, but once they're there, I can't reorder/organize them.  I suspect the solution lies somewhere in Nautilus, but I can't figure out how to access that from the netbook remix desktop.  How do I get there from the command line?

The specific things I wish to do are:

[LIST]
[*]Reorder icons in desktop panels
[*]Add the Public folder to the "Files&Folders" panel
[*]Get the weather to show in the toolbar at the top
[/LIST]
 In regard to the weather thing, I've already configured it though the control panel, but it still isn't showing up next to the date.  I entered a US zip code, so it should work.

Any help would be appreciated.

---

### Post by golanbatrac on 2010-02-19
I've never used UNR, so none of the following may apply:

> The specific things I wish to do are:

[LIST]
[*]Reorder icons in desktop panels
[*]Add the Public folder to the "Files&Folders" panel
[*]Get the weather to show in the toolbar at the top
[/LIST]
To reorder the icons on the desktop panel, right-click on one of the icons and uncheck 'Lock to Panel' and then right-click the icon again and select 'Move' to move it along the panel or from panel to panel.  Once you have it where you want it, right click again and lock it to the panel.

To add a folder to a panel, right click anywhere on the panel, choose 'Add to Panel' and then choose 'Custom Application Launcher' from the list.  In the command portion enter 'nautilus /full/path/to/public/folder' and then hit 'Ok' to add a launcher to the panel.

The only thing I can think to suggest Re: the weather is to right click on the clock, choose 'Preferences' and make sure that 'Show Weather' and 'Show Temperature' are both checked.

Again, I have no idea if any of this will work on UNR.  If not, hopefully someone will come along and provide better advice.  Best of luck!

---

### Post by JCollierDavis on 2010-03-02
There's a program on the System menu called Menu Editor.  Use that and you'll get a file browser tree type interface with all the menu categories on the left and the contents on the right.  You can select a program icon in that right pane and use the [UP] or [DOWN] buttons to reorder them.  It's a bit slow so be patient.  There's a menu at the top of the tree to reorder the menus.  
 
There will also be check boxes where you can "turn off" a program that you don't really use.  You can use a pop-up from there to change the launcher for each program including the icon and file path.
 
Attached is a pair of screenshots of my desktop for reference.

---

### Post by UberPuppy on 2010-03-24
I couldn't find an option to edit the launchers unfortunately.

However, for the favourites at least it is possible to modify them. Have a look at your configuration editor either via the menus or via

> gconf-editor

In here you'll find reference to the favourites launchers under 

> /apps/netbook-launcher/favourites/xxx

where xxx is the application launcher you want to change. In there is the location of a .desktop file. You can add your modifications in there.

Well, at least that's how I finally managed it.

---

### Post by kalos on 2010-09-17
As UberPuppy said, it seems that there is no provided way aside from gconf-editor to change the order of favourites. I thought that sounded like a challenge, so I wrote an application to reorder my netbook-launcher favourites. It's on github: [http://github.com/pydave/ficklefav-netbook-launcher.git](http://github.com/pydave/ficklefav-netbook-launcher.git)


Simple instructions for use:
```

sudo apt-get install git-core jython imagemagick
git clone http://github.com/pydave/ficklefav-netbook-launcher.git
cd ficklefav-netbook-launcher
jython ficklefav.py

```

It's not slick, but pretty simple to use. Just click on one icon and then another to swap their positions. Use the menu to save your config and restart netbook-launcher to see the changes.

---

