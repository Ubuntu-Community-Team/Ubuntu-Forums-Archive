---
title: "Recycle bin wont empty"
date: 2010-02-25
forum: General Help
---

### Post by Tayashlor on 2010-02-25
my recycle bin wont empty. 

i ran the command:
sudo rm -r ~/.local/share/Trash/files/*
and got the response:
rm: cannot remove `/home/steve/.local/share/Trash/files/*': No such file or directory

any help would be greatly appreciated.

---

### Post by quixote on 2010-02-26
Trash/files/ can also have directories in it, which wouldn't be deleted by a rm command unless you added -r -f.  (You have to be super-careful with that command, especially as sudo.  Make sure you're in the right directory or it can silently and irretrievably dump your whole operating system.)

The other thing is that I think (not at all sure on this) the rm command may interpret "*" to mean files with no extension, and you may not have any of those. You could try *.* and see if that makes a difference.

Is there a reason you can't right-click on Trash and select "Empty"?

another thing I thought of is that the new and unimproved gnome no longer lets root do certain things in users' home directories.  Try the command without the "sudo".

---

