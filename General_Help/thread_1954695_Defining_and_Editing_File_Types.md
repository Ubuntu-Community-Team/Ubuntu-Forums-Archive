---
title: "Defining and Editing File Types"
date: 2012-04-08
forum: General Help
---

### Post by SillySod on 2012-04-08
I need to find a way of defining/editing file types so that files with certain extensions can be opened by default using a specified application.

I've tried using Assogiate, but it doesn't work as expected: in particular, I am trying to re-define what happens with MS Word documents with the .doc extension.

The Word types defined only apply to .docx and .docm extensions and .doc is to be found in "Plain text", which means that every time I try to open a .doc file, it comes up in Gedit.  If I change the default to Open Office, it changes all my plain text files to open in OO which I don't want.

I've added .doc to the Word type in Assogiate, but it doesn't make any difference - can anyone help?

---

### Post by ridetheteapot on 2012-04-08
man xdg-mime

check this out for a little help making an xml file to descibe your file type-
[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html.en)

---

