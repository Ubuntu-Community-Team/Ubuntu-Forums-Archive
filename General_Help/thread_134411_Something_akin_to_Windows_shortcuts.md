---
title: "Something akin to Windows shortcuts?"
date: 2006-02-21
forum: General Help
---

### Post by Gijith on 2006-02-21
Hi all,

One of the features in Windows that I liked (and I guess took for granted) was the ability to create very functional shortcuts to folders and files by using the right click menu. With my computer, I have a lot of folders, located on a lot of different partitions. And it would make my life easier to have them all linked through my home folder. Does KDE have a function similar to Windows'? The closest I've found is the ability to create URLs that will link. This works okay, but it always opens a new tab (slightly annoying) and, much worse, will only seem to work in Konqueror. Mostly, I open files from within the 'Open File' box of an application such as amaroK or Open Office. Again, not a big issue. But it would make my life a little less frustrating if I didn't have to search so much when opening files.

Thanks for any help.

Gijith

---

### Post by Jucato on 2006-02-21
Two ways to do this.
1. GUI way: 
- Open up Konqueror. Your choice to open up 2 Konquerors or 1 Konqueror with Split views (Ctrl+Shift+T to split top-bottom or Ctrl+Shift+L to split left-right). 
- In one window, go to your target directory (where you want to place the shortcut). 
- In the other window display the folder/directory (the folder icon, not the contents of the folder) that you want to be linked.
- drag the folder (from 2nd window) to where you want to place the link (1st window). A menu will pop up, choose "Link Here"
* You can distinguish links from real folders by the text. Link names are italicized.

2. CLI (Command Line Interface) way:
```
ln -s *source_directory* *target_directory*
```
If you are trying to place a link inside a directory owned by root, don't forget to use sudo.
CLI Example: I want to put a link of the directory /usr/bin in my /home directory. I do this:
```
ln -s /usr/bin /home/username
```
*you can distinguish links by listing files using the -l option (ls -l). Links will start with "l" in the listing.

---

### Post by aysiu on 2006-02-21
Drag the folder or file you want to make a shortcut to (you can drag it to the desktop if you want) and then select "link here."

---

### Post by MetalMusicAddict on 2006-02-21
Is there a way to do this in Gnome?

---

### Post by Gijith on 2006-02-21
Wow. Thanks for the fast response guys. I can't believe I didn't notice that drag method before. Thanks a bunch. I love this forum. \\:D/

---

### Post by aysiu on 2006-02-21
[QUOTE=MetalMusicAddict]Is there a way to do this in Gnome?[/QUOTE] Yes. Middle-click-drag.

---

### Post by MetalMusicAddict on 2006-03-05
[QUOTE=aysiu]Yes. Middle-click-drag.[/QUOTE]
Um... How do I get rid of the _link_? Its tellin' me I cant do it.

---

