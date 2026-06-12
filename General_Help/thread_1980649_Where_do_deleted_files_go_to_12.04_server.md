---
title: "Where do deleted files go to 12.04 server"
date: 2012-05-15
forum: General Help
---

### Post by buecker on 2012-05-15
I'm having a hard time finding an answer to this one.

I have a linux server setup (as a VM but I don't think that is the issue) and I have windows clients accessing a shared folder on the server.  No user credentials required to access the folder.

If someone on Windows deletes a file in this shared folder where does it go?  I can't seem to find a .trash folder on my server?

Sorry for even asking this.  My search skills are on vacation today.

---

### Post by Lisiano on 2012-05-15
They get deleted. Else you'd see a $RECYCLE.BIN (Created by Windows users) or .Trash-000 (Created by Samba which interpreted the delete as a "Move to Trash")

EDIT: To be more precise, the system instructs the filesystem to remove the inode to the file which points to where the file is located physically on the disk, so the file is there, it's just not referenced anymore.

---

### Post by buecker on 2012-05-15
Thanks for the quick response.

Anyway to change this so that it does goes into a trash or recycle bin type folder?

---

### Post by Sandcastle on 2012-05-15
If you are sharing your folders through SAMBA, you could define a recycle bin using a vfs module.

For example:
```

vfs objects = recycle
        recycle:repository = trash
        recycle:keeptree = yes
        recycle:exclude = *.tmp, *~, *.bak

```

If the location of the repository folder is a relative path, it'll be placed relative to the directory of the share. You can also use absolute path names, so long as the user has write permissions in the parent folder.

If you do not want the users to have access to the recycle bin, while keeping it in the same folder as the share, you could veto the file from being seen through the file share with this line in your file definitions.

```

veto files = /path/to/share/trash

```More information on the vfs modules can be found [here]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/VFS.html").

---

### Post by buecker on 2012-05-15
Thank you!  That's what I need to figure out next!

---

