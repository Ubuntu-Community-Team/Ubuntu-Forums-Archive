---
title: "Files moved to trash,then deleted completely"
date: 2011-04-19
forum: General Help
---

### Post by PCaddicted on 2011-04-19
If I move a file to the trash,I can restore it later.But if I empty the trash,I'll be warned that I cannot recover the files if I proceed.Is this really true or are there Linux applications for recovering files deleted from the trash?Uhm...are the files deleted completely and unrecoverably or are there any traces left behind?

---

### Post by An Sanct on 2011-04-19
As always, there are traces, deleting into trash and emptying the trash does not *wipe* the files.

There are different tools to wipe files, take a look at these "[wipe for nautilus]("http://www.ubuntu-unleashed.com/2008/01/securely-wipeerase-files-in-ubuntu.html")" tutorial.

---

### Post by PCaddicted on 2011-04-19
I installed wipe and nautilus-actions,ran nautilus-actions-config but I got "command not found"...I use Nautilus 2.32.0,maybe it doesn't work on this version.Any ideas?

---

### Post by An Sanct on 2011-04-20
I see your problem (tried the tutorial myself right now...), the command is "nautilus-actions-config-tool", it can be found in the menu under System->Preferences->Nautilus Actions Configuration

PS. Also note, that there is no "OK" button, as stated in the tutorial, it seemed to be replaced by the little disk *with green arrow* button, just next to the "add" button - *empty file with green plus*.

---

### Post by PCaddicted on 2011-04-20
It didn't work immediately,I'll restart the PC...
EDIT:still,no luck:I have nothing related to wipe in Nautilus,even after following those instructions and restarting the computer.Any idea?

---

### Post by An Sanct on 2011-04-20
It has to work, if you restart nautilus
```
nautilus -q
nautilus
```

Select a file, right click and it should be there. No need to restart the machine for this...

PS. This action requires no confirmation, be careful with it :)

---

### Post by PCaddicted on 2011-04-20
Well,I have already tried to reset Nautilus with that command;still,no luck!

---

