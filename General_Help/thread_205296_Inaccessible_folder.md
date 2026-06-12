---
title: "Inaccessible folder"
date: 2006-06-28
forum: General Help
---

### Post by mwdowns on 2006-06-28
Hello folks. :)

I was fiddling around with the "Simple Backup Config" tool in System->Administration, and I somehow locked the Storage folder I was using to store the backups in (this folder is a storage partition on a seperate drive).

Basically, what I did was add a couple folders from my home directory for backup, making the final destination for these backups the folder (partition) in question.  I then wanted to see what would happen, so I hit the "backup now" button.  After doing this, I went to the Storage folder, only to find it locked.  I can view the contents by using the right-click "scripts->root-nautilus-here", but I can't access it normally.

I tried chmoding the folder using "sudo chmod u+rwx (folder name)" command, but that didn't do anything.

Any ideas about how to get the folder back to normal?

Thanks

---

### Post by mwdowns on 2006-06-28
Also, I just noticed that even though I can open up the folder using the root-nautilus-here command, I can not copy any of the files from that folder to another folder.

How can I make the folder normal again? :)

---

### Post by trent dillman on 2006-06-28
Is the partition mounted read-only?

---

### Post by aysiu on 2006-06-28
Assuming your storage folder is mounted at /storage, try ```
sudo chown -R mwdowns:mwdowns /storage
sudo chmod 755 /storage
```

---

