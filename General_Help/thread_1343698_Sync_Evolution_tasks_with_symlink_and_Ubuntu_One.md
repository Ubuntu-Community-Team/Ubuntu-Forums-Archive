---
title: "Sync Evolution tasks with symlink and Ubuntu One"
date: 2009-12-02
forum: General Help
---

### Post by firstbishop on 2009-12-02
I've got Evolution calendars sync'ing nicely between two machines using Gmail, but Google apparently doesn't offer the same facility for Tasks, so I thought I'd store the tasks.ics file that Evolution generates in my Ubuntu One folder and symlink to that file from the .evolution folder.

For some reason though any changes to the task list in Evolution results in the symlink being overwritten by the actual tasks.ics file - it's as if Evolution deletes the existing file and then writes a new file in its place. Obviously this means that the file in the Ubuntu One folder never gets updated.

Can anyone spot where I've gone wrong or suggest an alternative approach?

Thanks

Michael

---

### Post by Nostoc on 2010-05-02
> **firstbishop said:**
> I've got Evolution calendars sync'ing nicely between two machines using Gmail, but Google apparently doesn't offer the same facility for Tasks, so I thought I'd store the tasks.ics file that Evolution generates in my Ubuntu One folder and symlink to that file from the .evolution folder.

For some reason though any changes to the task list in Evolution results in the symlink being overwritten by the actual tasks.ics file - it's as if Evolution deletes the existing file and then writes a new file in its place. Obviously this means that the file in the Ubuntu One folder never gets updated.

Can anyone spot where I've gone wrong or suggest an alternative approach?

Thanks

Michael


Every time ubuntu one updates the file, it replaces the symlink with the file. 

I haven't tried it yet with One, but in dropbox (wich is similar) the work-around this is to only use symlinks to *folders* in your sync folder.

If you absolutely must use a symlink to a file, then put the Original file in the ubuntu one folder, and put a symlink where you would find this file in your file system.

---

