---
title: "is there a search i can do if i forget where i put a file?"
date: 2010-06-18
forum: General Help
---

### Post by SGC622 on 2010-06-18
I saved a file from openoffice word processor that i am trying to find, i forget where i placed it, its not in a traditional place, i meant to hide it, apparently from myself. I know the file name i was wondering if i could type in the file name to a program already on my computer or if there is one anyone knows of to help me. as far as recent documents, i have done numerous things on word processor that kicked the file in question off of the recent documents

---

### Post by WorMzy on 2010-06-18
If you run "sudo updatedb && locate <filename>", you might find it.

I've had varying success with this method.

You could also try Places -> Search for Files.

EDIT: Just noticed you're using Kubuntu; dunno if there's an equivalent to Places -> Search for files, on KDE.

---

### Post by LoneWolfJack on 2010-06-18
open a terminal window and type

```

cd /
sudo find . -name "*.odt"

```

---

### Post by jchase45 on 2010-06-18
Theres a search bar at the top of the folder view , click the magnifying glass to the right of the icon view button

---

### Post by SGC622 on 2010-06-18
Thank you everyone i found it, i ended up going to the root folder tools>find files and typed in the filename and found it, thanks!

---

