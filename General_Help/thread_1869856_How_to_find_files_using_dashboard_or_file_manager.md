---
title: "How to find files using dashboard or file manager"
date: 2011-10-26
forum: General Help
---

### Post by mrehorst on 2011-10-26
Can anyone explain to me how to find files using the search function in either the file manager or dashboard?  I was trying to find some linker scripts to run a c compiler for a microcontroller project and every search I tried (*.lkr, lkr, *lkr*, *.*lkr*) returned no results.  So I manually switched to the directory where the compiler is installed (after some digging to find out where THAT was) and looked inside a couple folders and found about 100 linker scripts with filenames like p18fxxxx.lkr.  

Where does the dashboard search feature search?  Where does the file manager search feature search?  How do I tell either to search all subfolders?  As far as I can tell the defaults make the search feature absolutely useless.  How do I set it to default to searching the whole HDD/file system?:confused:

---

### Post by vanadium on 2011-10-26
"search" in Unity dash does not work. It will only find files you recently opened.
Nautilus "find" should do the job, but is terribly slow.
Your best bet by now might be to press Ctrl+Alt+F. This loads the gnome search applet. It first uses locate, returning fast results, and then continues searching using find.
If Ctrl+Alt+f does not work for you, the command is "gnome-search-tool".

---

### Post by philinux on 2011-10-26
> **vanadium said:**
> "search" in Unity dash does not work. It will only find files you recently opened.
Nautilus "find" should do the job, but is terribly slow.
Your best bet by now might be to press Ctrl+Alt+F. This loads the gnome search applet. It first uses locate, returning fast results, and then continues searching using find.
If Ctrl+Alt+f does not work for you, the command is "gnome-search-tool".

I note that key binding is not default. Easy to set up under the command plugin. However open dash and type search brings up the search tool.

---

### Post by vasa1 on 2011-10-26
> **philinux said:**
> ...
Easy to set up under the command plugin. However open dash and type search brings up the search tool.

Could you please give a little more information about the command plugin or point me to a FAQ?

---

### Post by Frogs Hair on 2011-10-26
To set a custom keyboard short cut open , Keyboard > Shortcuts > Custom Shortcuts > Add . If you have Multi function key board the search button may work as well for opening file search .

---

### Post by philinux on 2011-10-26
> **vasa1 said:**
> Could you please give a little more information about the command plugin or point me to a FAQ?

Open compizconfig settings manager > General > Commands plugin

Enter the command you want in "Command Line 0" the in key bindings tab under "Run command 0" click on the disabled button. The rest is easy.

It took longer to type this than to set one up lol.

I've got one set up to gnome-terminal with the Menu key(inbetween The right win key and Ctrl)
And another to run xkill with Alt+x. This replaces the force kill applet.

---

### Post by philinux on 2011-10-26
> **Frogs Hair said:**
> To set a custom keyboard short cut open , Keyboard > Shortcuts > Custom Shortcuts > Add . If you have Multi function key board the search button may work as well for opening file search .

I tried that first for my terminal shortcut and it would not let me use the Menu key. This key seems to have no use and is nice for a one click terminal.

---

### Post by mrehorst on 2011-10-26
Thanks for the answer!  Typing search in the dashboard does the trick.  What is the point of the Dash search if it won't find anything but recently used files?  This is the kind of stuff that keeps windows users from dumping windows.

---

