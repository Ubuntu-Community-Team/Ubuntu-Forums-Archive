---
title: "Nautilus uses memory when deleting"
date: 2011-02-27
forum: General Help
---

### Post by fela on 2011-02-27
I can't use nautilus to delete a whole load of files off an SSH/SFTP server of mine, because when I try to do it, it just hangs and I can see that it quickly fills up the memory (of the client, not the server, obviously, of which there is a reasonable 896MB [I'm running Arch linux]).

Any reason for this memory usage while deleting [via SFTP]?

Of course I could just use the command line and manually delete each one but that would be a right pain in this circumstance compared to a GUI like nautilus ;) Or maybe I should just write a script to do it...

EDIT: I actually managed to do it with the CLI easily, however nautilus definitely has an issue with this. Maybe I should file a bug.

---

### Post by JRV on 2011-02-27
Could it be this problem?

  [http://ubuntuforums.org/showthread.php?t=1694759](http://ubuntuforums.org/showthread.php?t=1694759)

Run "top" from the command line.

If "gvfsd-metadata" is hogging your processor do this:

```

rm -rf /home/USERNAME/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

---

