---
title: "grokking the gimp apt-get - where does it install to?"
date: 2006-01-27
forum: General Help
---

### Post by nmatheis on 2006-01-27
hello
new-ish to linux and ubuntu.  i used synaptic to install gimp add-ons, help files, and grokking the gimp html book.  i can't seem to find where the grokking the gimp installed to.  i did a file search in the "file system" for grokking and came up with nothing.  gimp had several hits but no grokking the gimp.  i did a search using lower case letters, whereas the title of the book uses caps in places.  is that the problem with my search?  is the file search function case sensitive?  where do i find the grokking the gimp html document so i can put a link in my hoem folder to access it more readily?
thanks much!!!
nikolaus

---

### Post by az on 2006-01-27
Look at the package list of files.  Either use synaptic or another apt frontend or type

dpkg -L grokking-the-gimp (if that is the package name)

You can also check the contents of a package by looking at the 
packages.ubutnu.com page.
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=grokking-the-gimp&version=breezy&arch=all](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=grokking-the-gimp&version=breezy&arch=all)

usr/share/doc/grokking-the-gimp/copyright		    doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/Grokking_the_GIMP.css  doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/Grokking_the_GIMP.html doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/background.png	    doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/contents_motif.png	    doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/cross_ref_motif.png    doc/grokking-the-gimp [multiverse]
usr/share/doc/grokking-the-gimp/html/first-anim1.gif

---

### Post by Quirky on 2006-01-27
Open Synaptic, search for "grok", right-click grokking-the-gimp -> Properties -> Installed Files. It should tell you there where it lives. Perhaps it's in /usr/share/doc/grokking-the-gimp?

EDIT: Beaten to it :)

---

### Post by nmatheis on 2006-01-27
thank to you both for replying so quickly!  i thought there must be an easy way to get to it.  synaptic says it is installed.  so to get to the secondary point in my post - is the file search function in ubuntu case sensitive?  i'm not at my ubuntu box now, so i can't experiment with it.  if it is case sensitive, is there a way to turn that off?
thanks again!
nikolaus

---

### Post by az on 2006-01-27
[QUOTE=nmatheis] is the file search function in ubuntu case sensitive?  [/QUOTE]

Just about everyting in unix is case sensitive.

---

### Post by nmatheis on 2006-01-27
[QUOTE=azz]Just about everyting in unix is case sensitive.[/QUOTE]
thanks for the quick reply!  i'll definitely try searching with the correct capitalization when i get back to my ubuntu box.  it's fun learning a new system :)

---

