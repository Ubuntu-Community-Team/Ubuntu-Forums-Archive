---
title: "using smbclient to delete windows directories"
date: 2010-04-02
forum: General Help
---

### Post by mightytater on 2010-04-02
I am trying to use smbclient to remove any directories on a windows server 2000 box recursively, like:
    rm -r *   does on the linux filesystem

Currenlty, I am trying to get something like the following string to work:
    smbclient \\\\10.11.1.20\\Folder -A authfile -c "rmdir *"

Since this returns:
    NT_STATUS_OBJECT_NAME_INVALID removing directory file\*
I try to remove a directory I know exists:
    smbclient \\\\10.11.1.20\\Folder -A authfile -c "rmdir subdirectory"
That returns, as expected:
    NT_STATUS_DIRECTORY_NOT_EMPTY removing remote directory file \subdirectory

I have no idea what's in Folder, or in Folder\subdirectory, but I want all the contents out of there when my script runs.  Ideas on how to do that?

---

### Post by Chesamo on 2010-04-02
Change your command to: ```
smbclient \\\\10.11.1.20\\Folder -A authfile -c "rmdir /s /q subdirectory"
```

---

### Post by nem75 on 2010-04-02
BTW you can use forward slashes in smbclient parameters, a bit easier on the eyes than the quadruple backslashes. ;)

---

### Post by mightytater on 2010-04-02
> **Chesamo said:**
> Change your command to: ```
smbclient \\\\10.11.1.20\\Folder -A authfile -c "rmdir /s /q subdirectory"
```


When I tried this, I got:
    NT_STATUS_OBJECT_NAME_INVALID removing remote directory file \/s

Also, from \\10.11.1.20\Folder I want to use a wildcard to wipe out everything ... such as: 
    rm -r *

---

