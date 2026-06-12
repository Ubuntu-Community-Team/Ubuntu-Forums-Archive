---
title: "Keyboard shortcut for creating a new file"
date: 2011-07-05
forum: General Help
---

### Post by uShafee on 2011-07-05
If you want to create a new folder you could simply do ctr+shift+N. is there a similar shortcut for creating a new file? if not could someone please help me write a small bash script? how would you figure out the current directory if you are using a command such as touch?

---

### Post by Archy1987 on 2011-07-05
you could make a shortcut using the System - preferences - keyboard shortcuts.
Type the command "touch newfile.txt" to create an empty new file called  "newfile.txt."  If you don't want the file in your home directory, you  must provide the exact path to the file (e.g., "touch /etc/newfile.txt")[LEFT][COLOR=#000000]
[/COLOR][/LEFT]

---

### Post by uShafee on 2011-07-05
but how would you know which directory is currently open in nautilus? So for example, if i am at ~/documents/ and hit the shortcut for new file, it should create a file in that directory.

---

### Post by uShafee on 2011-07-15
Below is the solution.

First, open gconf-editor and set /desktop/gnome/interface/can_change_accels to true. This lets you edit menu shortcuts.

Second, open a terminal and type: killall nautilus && UBUNTU_MENUPROXY= nautilus This will relaunch nautilus with the standard (non-unity) menu bar, because the unity menu bar doesn't support this feature (it will respect your changed shortcuts, but it won't let you change them)

Now, open the file menu, hover the mouse over Create Document > Empty File and press your desired shortcut (Ctrl-Alt-N seems like a decent choice, or you can reassign Ctrl-N). You should see the accelerator hint change in the menu.

Finally, relaunch nautilus without the UBUNTU_MENUPROXY variable to get your unity menus back with the new shortcut.

[Source: askubuntu]("http://askubuntu.com/questions/53202/how-do-you-create-a-new-document-keyboard-shortcut/") by cscarney

---

### Post by piyush.kumar on 2011-08-09
thanks :D

---

