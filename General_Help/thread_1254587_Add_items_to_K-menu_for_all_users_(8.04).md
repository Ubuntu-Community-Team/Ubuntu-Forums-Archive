---
title: "Add items to K-menu for all users (8.04)"
date: 2009-08-31
forum: General Help
---

### Post by janel on 2009-08-31
Hi!
Can anyone please tell me how I add items to the K-menu which is then visible for all users in Kubuntu 8.04? I would like to add a menu containing programs available at our department which is not installed as apt-get-packages.
Thanks!

---

### Post by gunksta on 2009-09-01
If you have to do this manually, it works the same way under Ubuntu and Kubuntu. (Thanks opendesktop.org.)

Use dolphin or the command-line to go to /usr/share/applications/
(or any other file browser)

You should see a whole bunch off files with a name like foo.desktop. Open one up (it will be read-only access). As you can see the file structure for a .desktop file is really very simple. (Unless you need it translated into multiple languages . . . in which case you are on your own.  :-))

You will need to run a text editor like Kate or vim as root to edit a .desktop file. If you use vim, I don't need to tell you how to do this. In case you would prefer to use Kate, you can start it up with root access by hitting ALT-F2 and then entering

kdesu kate

The kdesu program will ask for your password (assuming you are allowed to run things as root) and start up kate in administrative super-man mode. Now you can open that .desktop file AND edit it!

I think it's easiest to open an existing .desktop file for a program that is located where I would like to see my new program. I then change the name of the file ("Save As"), so I get a "new" file.

Edit your new .dekstop file and change things where appropriate. It should appear in your menu once it's all saved. If not, log out and log back in or restart Kicker.

That's a basic introduction. If you need more specific help, I'll say more.

---

### Post by janel on 2009-09-02
Thanks, I have now added a few .desktop-files under /usr/share/applications/, but how do I connect them to a folder located under the K-menu? Let say I want to have a folder named "Chemistry" and I want my chemistry-programs added in the folder /usr/share/applications/ to be visible under "K > Chemistry".
Best, Janel

---

### Post by gunksta on 2009-09-03
It's a two step process:

First step. You will need to edit the .desktop files that you have recently created. Here's an example file from my system for the program rlplot which hides in the menu @ Education -> Mathematics:

[INDENT][FONT=Courier New][Desktop Entry]
Version=1.1.2
Encoding=UTF-8
Name=Rlplot Graph Generator
Comment=Generate publication quality graphs
Exec=rlplot
Icon=RLPlot.xpm
Type=Application
Terminal=false
**Categories=Education;Math**
[/FONT][/INDENT]
The last entry in the file is Categories=foobarstuffherethatmatters
It might be easier if it were called menu or location, but I didn't develop the spec and I'm sure someone has a good reason for why that word was chosen. You can change this to what ever you want. If I wanted to put rlplot into a menu folder called chemistry, all I would need to do is make the file read like this:

[INDENT][FONT=Courier New][Desktop Entry][/FONT]
[FONT=Courier New] Version=1.1.2[/FONT]
[FONT=Courier New] Encoding=UTF-8[/FONT]
[FONT=Courier New] Name=Rlplot Graph Generator[/FONT]
[FONT=Courier New] Comment=Generate publication quality graphs[/FONT]
[FONT=Courier New] Exec=rlplot[/FONT]
[FONT=Courier New] Icon=RLPlot.xpm[/FONT]
[FONT=Courier New] Type=Application[/FONT]
[FONT=Courier New] Terminal=false[/FONT]
[FONT=Courier New] **Categories=Chemistry**[/FONT]
[/INDENT]If you want the new Category to have a fancy icon, meta-data, translation into multiple languages, etc. You will need to create one more file (it's getting fun now, isn't it?)

```
cd /usr/share/desktop-directories
```

If you want to menu location or menu "folder" to look really nice, you will need to create a new menu folder or directory.

Here's a snippet from my kde-edu-mathematics.directory file:

[INDENT][FONT=Courier New][Desktop Entry]
Encoding=UTF-8
Type=Directory
Icon=applications-education-mathematics
Name=Mathematics
Name[af]=Wiskunde
...
X-Ubuntu-Gettext-Domain=desktop_kdebase-runtime
[/FONT][/INDENT]Your .directory files may look a little different. I'm using KDE4.2, not 3.x. But, the idea is the same. Find a menu item that is similar to what you want and copy it (remember, you will need to be root to do this). Once you have done that, you can edit the file. Unless you have mad language skills (and users who speak many languages) you can skip most of the Name= entries. Just have one or more in there for the languages that are important for your use.

And that, should make everything peachy keen.

---

