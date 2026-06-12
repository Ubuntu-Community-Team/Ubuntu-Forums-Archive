---
title: "Unrar"
date: 2009-07-04
forum: General Help
---

### Post by gametime25 on 2009-07-04
How can I install unrar?  I already put "sudo apt-get install unrar" [FONT=monospace]i[/FONT]nto the terminal and I got 

Reading package lists... Done[FONT=monospace]
[/FONT]Building dependency tree[FONT=monospace]
[/FONT]Reading state information... Done[FONT=monospace]
[/FONT]Package unrar is not available, but is referred to by another package.[FONT=monospace]
[/FONT]This may mean that the package is missing, has been obsoleted, or[FONT=monospace]
[/FONT]is only available from another source[FONT=monospace]
[/FONT]E: Package unrar has no installation candidate

Their is no unrar file in my computer period.  I looked through my synaptic and searched and it's not their.  This could be because I started way out with 6.06 and used update manager to upgrade now to 9.04. Ubuntu 6.06 never had those files, and update manager didn't download those files when I moved up to Jaunty.  Anyways I downloaded the rarlinux-3.9.b3.tar.gz package from [http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm), but I don't know how to install it. Help!  How do you install this package?

[FONT=monospace]
[/FONT]

---

### Post by earthpigg on 2009-07-04
have you enabled the non-free repositories? 

that is where unrar is found

---

### Post by gametime25 on 2009-07-04
Yes, I've already did that weeks ago.

---

### Post by geirha on 2009-07-04
System -> Administration -> Software Sources. Enable the multiverse repository and [unrar](apt:unrar?section=multiverse) should be available.

---

### Post by gametime25 on 2009-07-04
**Thanks,  I have unrar now. [COLOR=Black]I had to also check the Community-maintained open source software box to get it.[/COLOR]**

---

