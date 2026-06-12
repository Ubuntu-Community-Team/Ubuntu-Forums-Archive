---
title: "Undo mount action"
date: 2010-06-03
forum: General Help
---

### Post by Harutyun Dr. on 2010-06-03
Hello everyone.

Today I looked for a way to hard link directories. I came to "mount --bind olddir newdir" to achieve what I wanted. Accidentally the "olddir" folder specified contained some imported PHP files. After command execution the folder was empty. 

What I'm looking for is recovering the files I've lost. I've used magicrescue to find deleted files, but it seems my files are not in deleted files. 

That is why I thought that they are not actually deleted, but 
"hidden" somehow, and maybe un-mounting will show my files again.

Any help is highly appreciated!

---

### Post by dcstar on 2010-06-03
> **Harutyun Dr. said:**
> Hello everyone.

Today I looked for a way to hard link directories. I came to "mount --bind olddir newdir" to achieve what I wanted. Accidentally the "olddir" folder specified contained some imported PHP files. After command execution the folder was empty. 

What I'm looking for is recovering the files I've lost. I've used magicrescue to find deleted files, but it seems my files are not in deleted files. 

That is why I thought that they are not actually deleted, but 
"hidden" somehow, and maybe un-mounting will show my files again.

Any help is highly appreciated!

```
man umount
```

---

### Post by Harutyun Dr. on 2010-06-03
Hello and thank you for your reply. I've tried umount command and it worked to un-mount, but files which existed in the directory are not recovered. Any other suggestions?

---

### Post by WorMzy on 2010-06-03
mount --bind doesn't delete any files or folders in the mounted directory. If umounting the directory hasn't made the php files visible, then chances are they weren't there to begin with, or the umount command didn't successfully umount. If you did mount --bind manually, then restarting will return the directory to normal. If you added an entry to fstab, adding a "#" to the start of the line, then saving and restarting will also return the directory to normal.

---

