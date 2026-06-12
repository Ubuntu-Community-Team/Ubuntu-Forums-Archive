---
title: "can't edit &quot;Applications&quot; menu"
date: 2009-12-30
forum: General Help
---

### Post by raphaelmsx on 2009-12-30
Hi,

Using the default gnome menu editor, when I try to create a sub-menu under any menu (for example, Audio Production under Sound & Video), and then I try to move app icons into there, after one second the icon returns to the original location. And when I close the menu editor, any created menu is gone.

What's happening and how can I fix that?

Using Ubuntu 9.10 here.

Thank you.

---

### Post by plucky on 2009-12-31
> **raphaelmsx said:**
> Hi,

Using the default gnome menu editor, when I try to create a sub-menu under any menu (for example, Audio Production under Sound & Video), and then I try to move app icons into there, after one second the icon returns to the original location. And when I close the menu editor, any created menu is gone.

What's happening and how can I fix that?

Using Ubuntu 9.10 here.

Thank you.

Open a terminal and type ```
alacarte
```

Make the changes you require and see if there are any errors reported in the terminal window.Paste them to the forum for us to see.


Good Luck

---

### Post by raphaelmsx on 2009-12-31
Still not working, and there were no errors in the terminal window.

I remember that I could do that before, and it simply stopped working.

> **plucky said:**
> Open a terminal and type ```
alacarte
```Make the changes you require and see if there are any errors reported in the terminal window.Paste them to the forum for us to see.


Good Luck

---

### Post by plucky on 2009-12-31
Try to reinstall alacarte ```
sudo apt-get install --reinstall alacarte
```

Good Luck

---

### Post by raphaelmsx on 2009-12-31
Still no good...

> **plucky said:**
> Try to reinstall alacarte ```
sudo apt-get install --reinstall alacarte
```Good Luck

---

### Post by plucky on 2009-12-31
Can you give an example of what you are trying to do?


Try adding something simple like "xterm" to start up an xterm as a sub-menu and adding an icon from the list of icons provided.See if that works.

What icons are you using and where did you get them from?
What application are you trying to launch?
What command are you using?

---

### Post by raphaelmsx on 2009-12-31
Adding an icon like "xterm" works, that's not the problem.

There's the the main "Applications" menu, and then there's the "Sound & Video" under "Applications". I need to create "Music Production" under "Sound & Video". It creates, but when I try to move an existing icon under "Sound & Video" to "Music Production", it moves the icon, but after one second it reverts back. And when I close alacarte, the sub-menu "Music Production" is gone. 

Think like this: Applications -> Sound & Video -> Music Production.

Thank you.

> **plucky said:**
> Can you give an example of what you are trying to do?


Try adding something simple like "xterm" to start up an xterm as a sub-menu and adding an icon from the list of icons provided.See if that works.

What icons are you using and where did you get them from?
What application are you trying to launch?
What command are you using?

---

### Post by plucky on 2009-12-31
> but when I try to move an existing icon under "Sound & Video" to "Music Production", it moves the icon, but after one second it reverts back.

I don't think this is allowed,which is why it reverts back.

What you should do is click on the icon,which will open a "Browse Icons" window,from which you can select a new icon.Or search on the system for locations of other icons that you can also use.

Good Luck

---

### Post by Mahngiel on 2009-12-31
Are you still trying to create a sub folder?

---

### Post by raphaelmsx on 2009-12-31
I think I couldn't explain it right, I will try again:

There's the application shortcut X in menu A. I then create sub-menu B inside menu A and I want the application shortcut X inside sub-menu B.

I need to do that, because the default categorization doesn't fit my needs.

Got it?

> **plucky said:**
> I don't think this is allowed,which is why it reverts back.

What you should do is click on the icon,which will open a "Browse Icons" window,from which you can select a new icon.Or search on the system for locations of other icons that you can also use.

Good Luck

---

### Post by raphaelmsx on 2009-12-31
Yes, I am.

> **Mahngiel said:**
> Are you still trying to create a sub folder?

---

### Post by Mahngiel on 2009-12-31
I understand exactly what you're trying to do.  The problem is something I'm currently working on.  See this [thread]("http://ubuntuforums.org/showthread.php?t=1367498").

What I can try to tell you without getting too indepth, is that it's pretty difficult.  There are two main controls that are needed to input your own Menu folders, .desktop and .directory.  Short side, here is an example, this is what Wine had to do in order to insert a folder and further subfolders:

```

src=/etc/xdg/menus/applications-merged/wine.menu
<Menu>
  <Name>Applications</Name>
  <Menu>
    <Name>[COLOR=Red]wine[/COLOR]-[COLOR=Blue]wine[/COLOR]</Name> [COLOR=Red]the wine.desktop reference [/COLOR][COLOR=Blue]the folder within named "Wine"[/COLOR]
    <Directory>wine-wine.directory</Directory>
    <Include>
      <Category>Wine</Category>
    </Include>
  <Menu>
    <Name>[COLOR=Red]wine[/COLOR]-[COLOR=RoyalBlue]Programs[/COLOR]</Name> [COLOR=Blue]folder lives within [COLOR=Red]Wine[/COLOR][/COLOR]
    <Directory>wine-Programs.directory</Directory>
    <Include>
        <Category>Wine-Programs</Category>
    </Include>
  <Menu>
    <Name>wine-[COLOR=RoyalBlue]Programs[/COLOR]-[COLOR=SeaGreen]Accessories[/COLOR]</Name> [COLOR=Blue]Programs folder from above contains [COLOR=Lime]Accessories folder[/COLOR][/COLOR]
    <Directory>wine-Programs-Accessories.directory</Directory>
    <Include>
        <Category>Wine-Programs-Accessories</Category>
    </Include>
  </Menu>
  </Menu>
  </Menu>
</Menu>

```As you look at the attached image, this xml markup allows 'Wine' to add the sub folders Programs and Accessories, and all the contents are references to .desktop items.

As you see, it's not so easy as using the Main Menu to control directories.  I'm digging deep into this, and hopefully will have a work-around soon.

---

### Post by raphaelmsx on 2009-12-31
So, what's the point of having a "new menu" button in alacarte if it doesn't work?

It could be a simple drag-n-drop operation to organize shortcuts... Probably the developers of gnome and alacarte doesn't like that?

Thank you.

---

### Post by Mahngiel on 2009-12-31
you can have as many first level folders as you wish, it's the second level folders that it hard to get into.  You can do it, it's just a matter of creating the markup to allow it.  It's a simple applet, and has many rules to how it is structured, and many references for how it's drawn.  it doesn't make sense to me that it's so difficult to modify, especially with the great demand for it.

You can always look forward to 10.04 and the new gnome-shell. ew.

---

