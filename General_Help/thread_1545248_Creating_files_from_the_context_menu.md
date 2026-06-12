---
title: "Creating files from the context menu"
date: 2010-08-03
forum: General Help
---

### Post by studdard on 2010-08-03
Hi all

I'm a first time poster and very new to Linux, having recently installed it on my laptop. I'm enjoying the experience so far and already feel a bit less of a slave to the Microsoft Corporation.

I am having one issue. I like to create files using the GUI context menu. I right click on windows and one of the options in the menu is "new" and then I have many options such as Word 2007 file etc. 

I create a lot of files and so this method is more convenient by far for me than opening the application, saving and then navigating to where I want the file to go. Because when I want to create the file, I will probably be in the directory in which I want to create the file, the process takes only a few gestures to complete which is not the case if I have to go through the file system in the "save as" window. 

Is it possible to have this functionality in Ubuntu?

Thanks in advance.

---

### Post by floorish on 2010-08-03
There's a 'Template' folder in your home directory. Save templates to that dir and you'll be able to create them with RMB->Create document->*template name*

For example if you want to create open office documents from the context menu:
- start Open Office word processor
- File -> Save As ... ->
- browse to home/*username*/Templates
- save the file

- right click anywhere in a folder -> Create document -> *template name* 

Hope this will help you.

---

### Post by AlphaLexman on 2010-08-03
Welcome to the forums.

Just right click an empty area of your desktop, -> Create Document -> Empty File.

A 'new file' will appear on your desktop, right click it -> Open With -> (choose an application from the list)!

It doesn't matter if you want to make a spreadsheet or a written document, the 'new file' doesn't hold any header information to limit what kind of file it can or will be.

---

### Post by WorMzy on 2010-08-03
You may have noticed that there is a "Create Document" entry in Nautilus' context menu (Nautilus is the file browser, in case you didn't know). By default, that submenu just has "Empty file", but you can add other entries by adding a blank document (or a preformatted document) to the "~/Templates" folder. You need to restart Nautilus before they become visible in the list (just press Alt+F2, and run "pkill nautilus" [no quotes]), but once they're there, you can use them to copy the document from ~/Templates to your current location.

---

### Post by endotherm on 2010-08-03
Wow, I never knew the templates directory was useful. I always figured it was just bundle stuff like examples or sample pictures...

Op: I usually just Rclick -> New Empty File, and then just give it an extension. I never make a file without renaming it, so it's just as easy for me to add the extension then. glad you got a good answer though (and one that is personally educational as well).

---

### Post by studdard on 2010-08-03
Thanks very much for your help everyone.

---

