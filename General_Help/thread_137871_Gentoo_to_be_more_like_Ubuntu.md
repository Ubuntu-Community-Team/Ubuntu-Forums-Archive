---
title: "Gentoo to be more like Ubuntu"
date: 2006-02-28
forum: General Help
---

### Post by idtt2s on 2006-02-28
How do I make my Gentoo Gnome environment read foreign filenames and being able to save them from Firefox while being in an English environment?

For example, if I try to download &#32593;&#39029;.txt, it just shows "Invalid byte sequence in conversion input" in Firefox.

---

### Post by glug101 on 2006-02-28
Do you have utf8 listed in your /etc/make.conf file under the USE variable?  I believe that is necessary, but knowing my memory it's probably something similar.  You'll likely have to recompile the program after making the changes to your USE variable.

It's been awhile since I used Gentoo though, so I don't remember the details.  Try the Gentoo forums off of the gentoo.org site.  The people in ther are almost as friendly as the people in Ubuntu Forums :)

---

### Post by idtt2s on 2006-03-01
I have followed all the proper instructions. The latest non-Gentoo distro I've used was Ubuntu, and that does internationalization very well. On Gentoo, Banshee doesn't even recognize Chinese songs.

---

