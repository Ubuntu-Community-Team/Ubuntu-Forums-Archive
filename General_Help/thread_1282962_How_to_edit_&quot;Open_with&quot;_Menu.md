---
title: "How to edit &quot;Open with&quot; Menu"
date: 2009-10-05
forum: General Help
---

### Post by cyanide on 2009-10-05
Hi,
   I would like help in editing the "Open with" Menu in Gnome.

For example, I have a licensed version of PDF Studio and I would like to use this program to view/edit PDF Files instead of Acrobat Reader. So I select the file and right click and choose "Open with">"Open with other applicaton", since PDF Studio is not present in the list of programs, we select the "Use Custom Command" textbox and type in " /bin/sh "/opt/PDFStudio/PDFStudio" ". With this PDF file opens in PDF Studio. 

Now my questions are

1. How do I get PDF Studio into the list of Programs that the "Open with" dialoge box presents??

2. Going back to the example, after I opened the PDF file with PDF Studio for the first time the entry in the "Open with" menu states "Open with sh" instead of "Open with PDF Studio". How do I change the name from sh to PDF studio with correct icon??

Any help is appreciated.

Thanks!!!

---

### Post by barthel on 2009-10-05
You'll need to create appropriate mime-info entries for PDF Studio. Take a look at [http://http://developer.gnome.org/doc/whitepapers/SystemConfig/mime-info.html]("http://http://developer.gnome.org/doc/whitepapers/SystemConfig/mime-info.html") and [http://http://www.freedesktop.org/wiki/Specifications/shared-mime-info-spec]("http://http://www.freedesktop.org/wiki/Specifications/shared-mime-info-spec") for starters.

What you created via nautilus is probably stored under ~/.local/share/mime-info

HTH

---

### Post by kogger on 2009-10-05
You'll need to create an item for the program in the Applications menu. Right-click on Applications, Edit Menus, choose a submenu to put it in (e.g. Office or Other), and then click "New Item" to add the program to the list. In order for the new item to show up on the Open With menu, however, you have to add "%f" after the command. So your command would be '/bin/sh "/opt/PDFStudio/PDFStudio" %f'.

On a side note, if you created the command through "use custom command," then there's probably a menu entry already defined whose name is the same as your command. In that case you can just edit the name and icon of the existing one.

---

### Post by cyanide on 2009-10-05
Wow it worked!! Thanks a million man!! U rock!!

---

### Post by alecz20 on 2009-11-23
How about doing this for folders?

I have too many entries in the "Open With" menu for folders.

I know how to add entries, but not how to remove/edit them.

Going to properties, there is no "Open with" tab.

is there a file somewhere that I can manually edit?

---

### Post by pj_kare on 2010-03-20
> **alecz20 said:**
> How about doing this for folders?

I have too many entries in the "Open With" menu for folders.

I know how to add entries, but not how to remove/edit them.

Going to properties, there is no "Open with" tab.

is there a file somewhere that I can manually edit?


Solution (Karmic): Open HOME folder and show hidden files, open .local/share/applications and edit mimeapps.list under [Added Associations].
Delete inode entries from end ";" to previous ";" leaving no double ;; 
Save and exit.
Note: This will create a backup file "mimeapps.list~" you can delete that if you wish.

Should look similar to this:
```
[Added Associations]
text/x-uri=gedit.desktop;openoffice.org-writer.desktop;
inode/directory=nautilus-folder-handler.desktop;

```[URL="https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963"]
[/URL]

---

