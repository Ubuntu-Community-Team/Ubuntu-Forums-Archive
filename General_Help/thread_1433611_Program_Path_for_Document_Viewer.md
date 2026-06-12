---
title: "Program Path for Document Viewer?"
date: 2010-03-19
forum: General Help
---

### Post by YMS_1975 on 2010-03-19
Hey guys, 

I've been searching the site to find out what the program path is for Ubuntu programs, but can't find what I'm looking for. My search terms were :

- "program path" Ubuntu
- change "program path"
- "open with" "program path"

I came across a few articles but nothing really seemed to help me. Here's the problem; anytime I try to open a PDF file from my browser, I get either the "Open With..." option or the "Save to..." option.

If I select "Open With..." the default has been changed to Virus Scanner (ClamTK) which I recently installed. Admittedly, I was fooling around with virus scanners to see how they work in Ubuntu. But now my Document Viewer won't open up the PDF files.

If I select "Save to..." and save the PDF file(s) to my desktop, and double-click the PDF file from my desktop, then Document Viewer will open up the file.

What is the program path for me to change the default program back to Document Viewer???  :confused:

---

### Post by tom4everitt on 2010-03-19
/usr/bin/evince

EDIT: To elaborate a bit:

/usr/bin and /usr/local/bin are the most common installation paths for programs. If you know the terminal command you can find the path by running:

type <command>

If you can find it in the application menu, you can go to System-Preferences->Main menu, find the program there, click properties, and you'll see its full path as the command.

I guess this could have been made much simpler in some way.

---

### Post by YMS_1975 on 2010-03-20
I did what you said (and it worked) but for some reason, the "Do this automatically for files like this from now on" option is greyed out, which means...while it worked, I have to select the correct path everytime.

Why did this happen? How can I change the default?

---

### Post by tom4everitt on 2010-03-21
So the problem is only in firefox? Look in edit->preferences if you can find some option there. There should be one I think (I'm not on a ubuntu system right now unfortunately).

You could also try to reset all settings that has with the browser to do, simply run the command:

rm -rf ~/.mozilla

This will erase every setting in firefox including bookmarks etc., along with all your emails if you use thunderbird for example. But if this is not a problem you can do it.

---

### Post by YMS_1975 on 2010-03-22
> **tom4everitt said:**
> So the problem is only in firefox? Look in edit->preferences if you can find some option there. There should be one I think (I'm not on a ubuntu system right now unfortunately).

You could also try to reset all settings that has with the browser to do, simply run the command:

rm -rf ~/.mozilla

This will erase every setting in firefox including bookmarks etc., along with all your emails if you use thunderbird for example. But if this is not a problem you can do it.

I looked around in FireFox under **Edit > Preferences > Applications tab**, but I don't see PDF listed in the "Content Type", nor do I see an option to add/edit the file associations in FireFox. It merely states various file types (excluding PDF files; which is why I'm sure it asks me how to handle it each time a PDF comes up) and the respective programs used to open these various file formats.  :frown:

---

### Post by DawieS on 2010-03-22
I normally use Document Viewer for PDF files. Recently I had to install Adobe Reader from the repository with Synaptic, in order to do my Income Tax Return on the Internet.

The attached screenshot shows PDF listed in the Content Type column, giving me the choice of setting the default application to Document Viewer, Adobe Reader, or navigate to any other application. It is possible that this option only became available since installing Adobe Reader, since there is now also a Firefox plug-in listed as Adobe Reader 9.3.

When browsing files on my disks with the File Browser, I also have problems in making the default selection "stick". Some applications have disappeared from the available options, while others appear doubled up.

---

### Post by tom4everitt on 2010-03-22
> **YMS_1975 said:**
> I looked around in FireFox under **Edit > Preferences > Applications tab**, but I don't see PDF listed in the "Content Type", nor do I see an option to add/edit the file associations in FireFox. It merely states various file types (excluding PDF files; which is why I'm sure it asks me how to handle it each time a PDF comes up) and the respective programs used to open these various file formats.  :frown:

Okay, then I would try this:

1. quit firefox
2. Run: mv ~/.mozilla ~/.mozilla-backup
3. start firefox. 

If it works you can stay with this (but you will have lost all you bookmars and passwords). If it doesn't work, or you miss your old bookmarks too much:

1. quit firefox
2. Run: mv ~/.mozilla-backup ~/.mozilla
3. start firefox

and they should be back. 




A neat way to have your bookmarks and passwords survive such operations (and reinstallations of OSes etc.) is to install xmarks: 
[http://www.xmarks.com/](http://www.xmarks.com/)

I wouldn't survive without that service :)

---

