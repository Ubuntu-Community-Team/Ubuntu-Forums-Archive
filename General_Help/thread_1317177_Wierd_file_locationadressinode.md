---
title: "Wierd file location/adress/inode"
date: 2009-11-06
forum: General Help
---

### Post by AlexZaim on 2009-11-06
Hello. I have a question that makes me curious. Today i was playing around the system files and have noticed this strange thing...

in /urs/bin/ there is a folder named X11 and that's ok. But when i enter it, i find myself in the same folder (i mean: same files, same x11 etc) but the *location* bar tells me its /urs/bin/X11 . If i enter again in X11 folder, the same thing happens again and the location changes to /urs/bin/X11/X11.

This can go on non stop. So my question is , why does it work this way? Who or what needs it?

---

### Post by alphaniner on 2009-11-06
That X11 'folder' is actually a symbolic link (indicated by the little arrow on the icon) to the very folder in which it is located (/usr/bin).  Open a terminal and do a **file /usr/bin/X11** and it will become clear.  The reason you seem to move into successive X11 folders (rather than having the shell know you are *really* just in /usr/bin) is part of the design of symbolic links.

In the most simple terms (because that's as best as I understand it), some program expects stuff to be in the /usr/bin/X11 folder, but that stuff is in the /usr/bin folder (for whatever reason).  Rather than duplicate the stuff, the symbolic link is used so the program can think it is actually finding the stuff in /usr/bin/X11.

---

