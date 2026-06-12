---
title: "Gnote reinstall, how to import backed up notes?"
date: 2011-11-06
forum: General Help
---

### Post by Kurtosis on 2011-11-06
Hi all, I just backed up my home directory and did a fresh install of Ubuntu 11.04, and then added Gnote from the Ubuntu repo (version 0.7.1).  However, I'm having trouble getting the new Gnote install to import or recognize my backed up notes from the previous install.

The previous Gnote stored all its notes in ~/.gnote as files with (what appears to be) a UUID and a .note extension:

1f5151fb-c93f-43fa-9858-cc4c62d4530f.note
...

However, the new Gnote install did not create the ~/.gnote directory.  And copying my backed up .gnote directory into ~/ does not make any difference either.  It appears the new Gnote is storing notes somewhere else?

Starting gnote from the cmdline and manually pointing it to ~/.gnote actually works, though:

$> gnote --note-path=~/.gnote

I've tried searching my hard drive for *.note to see if there are notes stored anywhere else in the file system (including a test note I created and saved for the purpose), but no joy.

Anyone have any idea how to import old notes, or get gnote 0.7.1 to use ~/.gnote again as the source directory?

Thanks!

---

### Post by stoneguy on 2011-12-24
Looks like a Tomboy conversion leaves the Gnote data where the .tomboy directory is. 

Copy the backup ~/.gnote directory to ~/.local/share/gnote and you're good to go.

---

