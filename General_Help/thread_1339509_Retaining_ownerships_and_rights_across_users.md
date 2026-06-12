---
title: "Retaining ownerships and rights across users"
date: 2009-11-27
forum: General Help
---

### Post by kartal on 2009-11-27
Hi

I have bunch of folders that are modified by multiple users. The main folders are in one users home folder, and the others are accessiong via symbolic linking. As you might guess the problem arises when non home owner users modifies the files and folders(when the user runs an application that utilizes those folders), the ownership changes and the application modifies the writing and accessing rights. Then the other users cannot access those folders because the file rights are modified by another users access. 


Would there be a way to keep the rights and access rights same across users and sessions?


thanks

---

### Post by aysiu on 2009-11-29
Perhaps keep the shared files on a FAT32 partition? That's the relatively simple way to do it.

There are other ways to approach it, though:
[http://ubuntuforums.org/showthread.php?t=419456](http://ubuntuforums.org/showthread.php?t=419456)

---

### Post by dcstar on 2009-11-29
> **kartal said:**
> Hi

I have bunch of folders that are modified by multiple users. The main folders are in one users home folder, and the others are accessiong via symbolic linking. As you might guess the problem arises when non home owner users modifies the files and folders(when the user runs an application that utilizes those folders), the ownership changes and the application modifies the writing and accessing rights. Then the other users cannot access those folders because the file rights are modified by another users access. 


Would there be a way to keep the rights and access rights same across users and sessions?


thanks

Move shared files out of /home folders - which are supposed to be secure - and put them somewhere appropriate, like in Samba shared folders.

---

### Post by sisco311 on 2009-11-29
You can use ACLs:

[uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

---

