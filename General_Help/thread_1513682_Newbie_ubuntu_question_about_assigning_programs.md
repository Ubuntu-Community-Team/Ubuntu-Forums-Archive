---
title: "Newbie ubuntu question about assigning programs"
date: 2010-06-19
forum: General Help
---

### Post by ksaul on 2010-06-19
How do i assign programs to certain files? When I right click->open with not all the applications are listed. 
Main issue is .php files is opening with Notepad in Wine, but I want it to run with ZendStudio but do not know the commandline to have it execute.

---

### Post by Smart Viking on 2010-06-19
right click in the file, then go to the "open with" thingy, then all files of that type will be open with the assigned program.

This is the command to make a file executable:

```
chmod +x <filename>
```And remember if you are not in the relative path you must enter the full /path/to/file

, I hope this helped. :)

---

### Post by Primefalcon on 2010-06-19
for reference php files SHOULD NOT BE EXECUTABLE they are read by an interpreter not directly executed

---

### Post by Deadite81 on 2010-06-19
The reason not all applications are listed is usually because the developer of the application did not include any mimetypes in the .desktop file (launcher file for the menu).  This is very annoying and is especially confusing for users used to other operating systems.  

I don't know what ZendStudio is, but making the file executable has nothing to do with your problem.  I really should write a tutorial about mimetypes and Ubuntu because everything out there that I've found is far too complicated and spread out.

I also run into the problem constantly of Nautilus file manager not remembering what files to open with what.  I'm not sure if all these problems should be associated with the developers of individual apps or as a flaw of Ubuntu itself.

Also, Wine just simply took over the duties of opening all kinds of files by default on my system when I installed it, which was completely out of line and took an awful long time to repair, but that's another story.

Anyway, if you haven't solved your problem and want to know more let me know, cause it'll be a lot more typing.

---

### Post by ksaul on 2010-06-26
yes i still need help and I have no idea where ZendStudio installed itself.. ZendStudio is a PHP IDE for editing PHP files

.php files are shown with zends logo, but when double clicked on it opens in Wine->Notepad. Open With doesnt offer Zend on the menu

---

### Post by supergrav on 2010-06-26
You can run in terminal:  locate ZendStudio and you've got your answer. Have in mind that filenames are case sensitive, so if you don't find it at first try, alter capital letters...

---

### Post by Deadite81 on 2010-06-26
You can do this several ways, this is one of my favorites.  I assume Zendstudio has a main menu entry.  Open any text editor that supports drag and drop, such as Gedit, Geany, or Kate.

Open your main menu and drag the Zendstudio entry into the text editor.  You should see something like this:
```

[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
**MimeType=text/plain;**
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=gedit Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.2
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit-2/gedit-bugreport
X-Ubuntu-Gettext-Domain=gedit
```Note the name and location of the file, which should be in the title bar, and named something like "zendstudio.desktop".

In the above example notice the bold line "Mimetype=text/plain".  In a nutshell, this means that the Gedit text editor will always be presented in Nautilus as an option to open text files.  The fact that Gedit has a mime type at all ensures that it will be available as a choice in the Nautilus file properties "Open With" tab.  When a program has no mime type it is not recognized by Nautilus at all.

Now, in your zendstudio.desktop file you need to add the line any where as long as it's on it's own line:
```

Mimetype=application/x-php;
```Save the file.  This file is likely located in /usr/share/applications, so you will need to open your text editor as root to be able to save.

Restart Nautilus (nautilus -q &) or log out and in to see the changes.  Now you can right click a PHP file in Nautilus and make Zendstudio the default through the Properties window.

There are other ways to do this.  For example, I said note the location of the .desktop file.  There are files stored in /usr/share/applications called "mimeapps.list" and "defaults.list".  These files control what type of file is opened in what app.  You probably don't want to mess with defaults.list, but if you take a look at mimeapps.list it should be pretty clear what these files do.

Any entry added to mimeapps.list will become the default automatically as long as it's first in the list.  For example:
```

application/x-php=zendstudio.desktop;gedit.desktop;geany.desktop;

```Means that all three of these programs will be available to open PHP files, but Zendstudio will be the double click default.  But this is not necessarily all the apps that will be available for PHP files, it could be many more assuming that the program's individual .desktop files specify a mime type.

When you make a user modification to any of this stuff it is stored in /home/you/.local/share/applications.  This is the place for custom launchers, mime lists, ect.  It's structure is exactly that of /usr/share/applications, and it's contents override any root settings for that user.

Lastly, you can find a list of the mime types your computer recognizes in the file "/etc/mime.types".

If you run into any problems or have a question let me know :)

---

### Post by Deadite81 on 2010-06-26
I am also assuming that Zendstudio opens correctly from the menu or terminal.  I have known 
Wine to screw up launchers.  When you look at its .desktop file make sure that the line "exec="
is the correct command to open Zendstudio.

---

### Post by ksaul on 2010-06-27
no zend does not have a menu item

---

### Post by Deadite81 on 2010-06-27
Wine usually automatically creates menu items for any program it installs under Applications --> Wine --> Programs.  The launcher for this menu item is located in the directory /home/you/.local/share/applications.  This is a hidden directory.  Ctrl+H or the Nautilus menu View --> Show Hidden Files will make it visible.  If you do not have this, then there is a problem.

The first question is have you figured out how to run the program at all?  It appears that you haven't but I'm not sure.

Wine will have installed Zendstudio in your virtual C Drive, which is located in the hidden directory /home/you/.wine/drive_c/Program Files.  An easy way to view your C Drive is through your main menu - Applications --> Wine --> Browse C Drive.  In this directory you will find your Zendstudio installation.  Double clicking on the proper .exe file will launch the program just as in Windows.

Also, the locate command already mentioned will find the files or you can use the Gnome Search Tool, a graphical frontend to locate found in Applications --> Accessories --> Search.

If you find no results in your home folder or file system, you can try typing into a terminal:
```
sudo updatedb
```This will update your search database.  If you still find no Zendstudio files after all this then Wine may have crapped out on you or you are overlooking something.

---

