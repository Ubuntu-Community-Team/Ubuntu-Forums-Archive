---
title: "How do I make 2 mounted drives show as a single folder?"
date: 2010-02-19
forum: General Help
---

### Post by kevin06vino on 2010-02-19
Hi All, 

Please excuse my lack of knowledge on this, and I've tried to search.  I'm not even sure I know what to call what I'm trying to accomplish.  I have roughly 5Tb of movies spread out on 6 drives in my system.  I'd like to create a folder that will display the contents of certain folders without actually moving the data.  For example, I have 3 drives with /HDMovies and 3 with /SDMovies.  How do I create two new folders /HDMovies and /SDMovies and have the data from the drives be collected?

I appreciate any/all assistance.  I'm using the x64 of 9.10

Thanks!

---

### Post by MinimalBin on 2010-02-19
[URL="http://en.wikipedia.org/wiki/Symbolic_link"]Wikipedia - Symbolic link
[/URL]

---

### Post by kevin06vino on 2010-02-19
Thanks, I'll give this a read!

---

### Post by kevin06vino on 2010-02-19
If I delete a file from the linked folder, will it delete the actual file?  

My movie collection is getting out of control, and I'm starting to see that I've got duplicate movies, and if they were all in the same list, I could easily locate duplicate files.

---

### Post by kevin06vino on 2010-02-19
> **kevin06vino said:**
> If I delete a file from the linked folder, will it delete the actual file?  


Google was my friend:

[http://library.gnome.org/users/user-guide/stable/nautilus-symlink.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-symlink.html.en)

Creating a Symbolic Link to a File or Folder

A symbolic link is a special type of file that points to another file or folder. When you perform an action on a symbolic link, the action is performed on the file or folder to which the symbolic link points. However, when you delete a symbolic link, you delete the link file, not the file to which the symbolic link points.

To create a symbolic link to a file or folder, select the file or folder to which you want to create a link. Choose Edit &#8594; Make Link. A link to the file or folder is added to the current folder.

Alternatively, grab the item to which you want to create a link, then press-and-hold Ctrl+Shift. Drag the item to the location where you want to place the link.

By default, the file manager adds an emblem to symbolic links.

The permissions of a symbolic link are determined by the file or folder to which a symbolic link points.

---

