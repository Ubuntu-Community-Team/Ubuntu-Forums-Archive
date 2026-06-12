---
title: "Backing up with terminal?"
date: 2011-11-04
forum: General Help
---

### Post by littlebird on 2011-11-04
I have been trying to resuscitate my laptop after upgrading from 11.04 to 11.10.  It didn't work, so I am going to re-install 11.04 with a live CD.  What I don't know how to do is back up my home folder with the terminal.  I have access to an external hard drive, and will be moving the data there, but I want to make sure I do it correctly.  

I'm not sure if this is relevant, but when I ran the live CD, it showed no data in any of the files or the hard drive.  Is this simply because it was showing me the data on the CD only, or did my hard drive actually get wiped?  Is there a way to check for this from the terminal?  I have tried searching for the right commands, but I am still just getting the hang of it, and only know enough to have gotten the laptop to the point where I can actually access a terminal.

Any help would be appreciated!

---

### Post by wojox on 2011-11-04
From a Live-CD you would just need to open Nautilus and mount the partitions.

---

### Post by Spyderkid on 2011-11-04
from terminal just do...

```

cp -r TARGET DESTINATION

```

if only copying single files remove -r

---

### Post by Lars Noodén on 2011-11-04
[rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) is a good way to copy large numbers of files.

```

rsync -avH /path/from/directory /another/path/to/directory

```

---

### Post by littlebird on 2011-11-07
Thanks guys, that helps!  I am on the way to a functional computer again.  I am going to mark this thread solved.

---

