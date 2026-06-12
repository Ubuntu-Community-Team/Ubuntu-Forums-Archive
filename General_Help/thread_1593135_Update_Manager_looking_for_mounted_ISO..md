---
title: "Update Manager looking for mounted ISO."
date: 2010-10-11
forum: General Help
---

### Post by iEthan on 2010-10-11
The upgrade to 10.10 wasn't showing up in the Update Manager, so I torrented the alternate ISO, mounted it, and ran cdromupgrade. It all ran smoothly, until I started my computer back up and ran the Update Manager. It said I needed to insert a disc. I ran "sudo apt-get update", and the output was this:

Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

How do I remove the dependency on the ISO?

---

### Post by TheAnachron on 2010-10-11
What about mounting the cdromdrive as partition called "Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)"? That should work.

---

### Post by plucky on 2010-10-11
> How do I remove the dependency on the ISO? 

In **Update Manager > Settings** un-tick the ISO as a Source on the first tab.This used to be Software Sources in previous releases,but it isn't in the Administration Menu by Default in Maverick

Good Luck

---

