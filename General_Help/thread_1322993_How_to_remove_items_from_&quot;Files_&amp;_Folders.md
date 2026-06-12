---
title: "How to remove items from &quot;Files &amp; Folders&quot; in 9.10NR ?"
date: 2009-11-11
forum: General Help
---

### Post by cbraxton on 2009-11-11
The "Connect to server" panel applet saves its bookmarks into the "Files and Folders" section of the Karmic Netbook Remix GUI.

How do you edit or remove these? I saved a couple of server bookmarks that for whatever reason do not work (they give a short "connecting" message and then nothing), and would like to remove them. Problem is I can't find a way to do this; right-clicking on the item does not offer a delete option, and Files & Folders does not appear to be in the menu editor. Any help with this would be greatly appreciated, thanks!

---

### Post by fooman on 2009-11-11
try opening your home folder...click the main menu in the left corner of the top panel > places > home folder

when the home folder opens,  scroll down in the left column and you will see the bookmarks at the bottom.

there you can just right-click them and choose "remove"

hope that helps.

---

### Post by moore.bryan on 2010-01-17
And if one isn't trying to delete bookmarked entries, but the other ones; e.g., Documents, Pictures, etc.?

---

### Post by jarreboum on 2010-04-30
How do you remove items that are not on the list? I would like to get rid of "Desktop" and Examples". Deleting the original folder doesn't help.

---

### Post by graydo64 on 2010-05-02
Not sure about Desktop but Examples can be removed by deleting or renaming examples.desktop in your home folder, e.g.:

cd ~
mv examples.desktop examples.desktop.old

---

### Post by bryanosaurus on 2010-07-19
I know this is an old thread, but I stumbled across it as I was trying to solve the same problem. 

It appears as if they files and folders you see on the Main Menu are just your bookmarks set in Nautilus, so just go to Bookmarks > Edit Bookmarks and remove what you don't want to show up.

---

### Post by jarreboum on 2010-07-19
> **bryanosaurus said:**
> It appears as if they files and folders you see on the Main Menu are just your bookmarks set in Nautilus, so just go to Bookmarks > Edit Bookmarks and remove what you don't want to show up.

"Desktop" and "Examples" (and ~/ for it matters) are not bookmarks set in Nautilus, therefore cannot be removed that way.

---

### Post by ScottyFX2 on 2010-08-01
Same problem with Ubuntu Netbook Editon 10.04? Any solutions?

---

### Post by MestreLion on 2010-08-09
> **jarreboum said:**
> "Desktop" and "Examples" (and ~/ for it matters) are not bookmarks set in Nautilus, therefore cannot be removed that way.

In my install, "Downloads" is also non-removable that way...

I have already deleted ALL bookmarks (~/.gtk-bookmarks is empty) and still 4 entries remain in my "Files & Folders": 
- ~/ ($HOME)
- Desktop
- Downloads
- Examples

Home dir and desktop are ok, but i really want to remove Downloads and Examples. And NO, deleting the folders is NOT an acceptable solution. Downloads is used as FireFox default download folder, and Examples... well, i may find it useful in the future. All i want is to remove their ENTRIES in the "Files & Folders" menu. How can i edit (and remove) those "special treatment" entries?

---

### Post by MestreLion on 2010-08-10
Digging up further, i solved the "Examples" issue...

Looks like launcher is hard-coded to search for a file **~/examples.desktop** and, if it is present, it shows up in the Files & Folders section. That file is a "desktop entry" type of file, a sort of "link" that points to **/usr/share/example-content/**

So, if i dont want that entry to appear, i have the following choices regarding ~/examples.desktop file:

- **Delete it**. After logout/login, the entry in the menu is gone, and the folder is still intact at /usr/share/example-content/. But i do lose the link to it that was avaliable in home folder.

- **Rename it**, to something like ~/_examples.desktop (or *~/anything.desktop*). Launcher wont add it to Files & Folders after login, and i still keep the link to Examples dir in my home folder when using Nautilus. And the link is still called "Examples", since the filename is irrelevant for .desktop files

- **Edit it**, so it points somewhere else. It is a plain text file, can be edited with gedit. Changing Name and URL entries change its name and location in both Nautilus and Laucher.

Personally, i renamed the file to ~/exemplos.desktop , and problem solved.

More info:
[https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/423601](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/423601)

Ill research now  the "Downloads" icon...

And, by the way, found out another issue:
**- You can delete all BUT ONE of your bokmarks. If you delete them all, Launcher (or Nautilus, or xdg-user-dirs-update) re-creates ALL of them! Quite annoying!**

---

### Post by MestreLion on 2010-08-10
Researching on the Downloads folder, found out that it is also hard-coded :(

And in a such way that looks like only way of removing it is to edit **~/.config/user-dirs.dirs** and delete (or comment) the line. But i guess that would also remove all "special status" of the download folder as well. I filed a bug report on this:

[https://bugs.launchpad.net/netbook-remix-launcher/+bug/615742](https://bugs.launchpad.net/netbook-remix-launcher/+bug/615742)

---

