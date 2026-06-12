---
title: "Dropbox and Symlinks"
date: 2009-12-08
forum: General Help
---

### Post by listerdl on 2009-12-08
Hi is there a way to remove symlinks?

I am trying to point a programme to sync files at a particular location and it is proving a complete headache due to my various attempts that have left a littering of symlinks. Is there a way to hunt these and remove them?

Thanks!

---

### Post by FearfulJesuit on 2009-12-08
Not to be a smart ***, but if you know how to program recursive scripts, you can program a recursive script that looks for the symlinks by extension and removes them. I don't remember if you can get the 'rm' function to do this.

Just curious, how many symlinks do you have in the folder? If it's like 30 or less, just arrange the icons by type and remove all the symlinks. If this is a system folder don't do this. You might delete symlinks that are actually important.

The other thing you can do is use the find function in the folder where you tried creating the symlinks. Find all the symlink files and delete them.

---

### Post by listerdl on 2009-12-08
> **FearfulJesuit said:**
> Not to be a smart ***, but if you know how to program recursive scripts, you can program a recursive script that looks for the symlinks by extension and removes them. I don't remember if you can get the 'rm' function to do this.

Just curious, how many symlinks do you have in the folder? If it's like 30 or less, just arrange the icons by type and remove all the symlinks. If this is a system folder don't do this. You might delete symlinks that are actually important.

The other thing you can do is use the find function in the folder where you tried creating the symlinks. Find all the symlink files and delete them.

thanks for the advice - could you possibly expand a bit more on this - like how do i "....use the find function in the folder where you tried creating the symlinks. Find all the symlink files and delete them"

Thanks

---

