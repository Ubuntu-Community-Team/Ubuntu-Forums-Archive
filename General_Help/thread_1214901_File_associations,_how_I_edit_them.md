---
title: "File associations, how I edit them?"
date: 2009-07-16
forum: General Help
---

### Post by roccivic on 2009-07-16
I messed up big time the file associations on my PC over a long time.
Now, I know I can right click on a file of some type and edit these in the properties, but I'm not even sure which ones are wrong. Doing this the GUI way would take forever...

Isn't there some file (e.g.: /etc/associations.conf) that dictates what is opened with what? 

Cheers

---

### Post by drs305 on 2009-07-16
For root, some of the associations are found in /root/.local/share/applications/defaults.list (apps selected via Properties, Open with) and /etc/mime.types

For the user, the associated file is $HOME/.local/share/applications/mimeapps.list for opening apps selected via Properties, Open with. There can be more than one entry for a file type - you can remove any or all of them.

---

