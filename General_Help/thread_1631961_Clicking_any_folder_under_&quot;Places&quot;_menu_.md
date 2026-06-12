---
title: "Clicking any folder under &quot;Places&quot; menu opens rhythmbox"
date: 2010-11-27
forum: General Help
---

### Post by john77eipe on 2010-11-27
Hi

I have Ubuntu 10.10. Once I open Rhythmbox it stays open even if I close it. (Under volume icon).

The problem is when i click on any folder(home,downloads,documents,...) under the Places menu it's opening rhythmbox!!!

---

### Post by john77eipe on 2010-11-28
It's a trouble now! Please help.

---

### Post by mc4man on 2010-11-28
see here
[http://ubuntuforums.org/showthread.php?p=10098466#post10098466](http://ubuntuforums.org/showthread.php?p=10098466#post10098466)
this 'bug' (request to mitigate), will explain why and what do to to prevent in the future
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

---

### Post by john77eipe on 2010-11-29
Thank you sire.

That worked.

---

### Post by boyevil on 2011-02-03
Just adding this so you dont have to fallow the ink:

Code:

gedit ~/.local/share/applications/mimeapps.list

Find the line inode/directory= and either delete the whole line or add to front
Code:

nautilus-folder-handler.desktop;

Werked like a lucky charm

---

### Post by jcoles on 2011-03-12
> **mc4man said:**
> see here
[http://ubuntuforums.org/showthread.php?p=10098466#post10098466](http://ubuntuforums.org/showthread.php?p=10098466#post10098466)
this 'bug' (request to mitigate), will explain why and what do to to prevent in the future
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

Interesting. But I am sure that I didn't use the Open with Other Application function on my home folder. The problem just appeared out of the blue. This bug probably doesn't cover all of the causes for this type of problem with the Places menu. 

The Places menu has only one function -- opening various home directory folders in Nautilus -- and no one would ever expect it to do anything else.

---

