---
title: "Edit places menu in GNOME classic Ubuntu 11.10"
date: 2012-05-31
forum: General Help
---

### Post by tito-dutta on 2012-05-31
I want to add these two folders in Places menu
1) Documents folder
2) Ebooks folder
In short I want to customize "Places"
By default, "Documents" was added there, but I think I have messed up something, so, it is missing now!
How can I do it?

---

### Post by tito-dutta on 2012-06-01
Anyone?

---

### Post by tito-dutta on 2012-06-09
Bump, anyone?

---

### Post by hariprasad on 2012-06-09
I would like to do it too. Because after upgrade it doesn't work for me. Icons are visible, but after click there is no response. It looks like, that there is something wrong.

---

### Post by bogan on 2012-06-09
Hi!, **tito-dutta**,

The only 11.10 install I have access to at present does not have the Gnome Classic option so I cannot confirm what follows works for that, but from memory it did.

But In 12.04:
What show in the drop-down of the Places menu are Bookmarks, and you add or edit them from the  Bookmarks menu of a Places window.

Open a Places window, say Home Folder,  Select 'Bookmarks' menu and either >Add or >Edit Bookmarks.

Change the entries in the Add or  Edit window that opens and select 'Close', or 'Remove' and 'Close'.

Chao!,** bogan.**

---

### Post by pkirkaas on 2012-12-11
Well, that didn't work for me, but in 12.10, after grepping around, I found the ```
/home/[username]/.config/gtk-3.0/bookmarks
``` file. 

That lists the custom locations like Documents, Music, etc.

Just put or remove locations there to customize the Places menu. It seems like by default it takes the last directory name in the path as the name of the place, but if you add a space and your own name, it will use that instead.

Then, just log out & back in.

---

