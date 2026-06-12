---
title: "Scotty Tkined"
date: 2005-02-16
forum: General Help
---

### Post by dwanders on 2005-02-16
Is there a way to get Scotty & Tkined installed on Ububtu? Or is there a better application sugestion that I should instead?

---

### Post by drjava on 2006-01-11
I have tried to get Scotty 3.0.0 to work on Breezy but no luck, I get a segmentation fault when the Tnm library is initialized.  I even went so far as to build tcl 8.4 from the cvs branch, and scotty from the svn trunk.

It seems as though the Tcl function Tcl_FSStat() from TnmMkDir() is stepping on some memory which causes a segmentation fault down the line.

I say this because the path sent to TnmMkDir() is split using Tcl_FSSplitPath() and the number of path components is saved to a local int.  Then these path components are iterated on.  After the call to Tcl_FSStat() the value of this count changes from 2 to some other value like 260098.

I have not been able to track down what is causing it.  Since I'm not an expert on Tcl internals and don't have enough time, I may never solve it.  I suppose I could try it on another distro and see if that makes a difference. 

Does anyone know if this worked on prior releases of Ubuntu?  I would really like to have this work because I have a lot of automation based on scotty running on an ancient Suse box that I would like to migrate.

Mike

---

### Post by Anemos_w on 2007-06-12
After a lot of effort a managed to set tkined on a debian. I 'd like to ask if there is any possibility to make this running on an apache server so i could see it from a web browser.
Thanks

---

