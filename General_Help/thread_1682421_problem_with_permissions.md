---
title: "problem with permissions"
date: 2011-02-05
forum: General Help
---

### Post by captainstan on 2011-02-05
whenever i click a box to let a program be executable it gets unclicked right away....i am not able to make any program executable

---

### Post by spaceboy909 on 2011-02-06
> **captainstan said:**
> whenever i click a box to let a program be executable it gets unclicked right away....i am not able to make any program executable
What program(s) are you trying to run?  As a rule, when you install software from the repositories, or even from source, into standard locations, they will automatically be executable.

---

### Post by mcduck on 2011-02-06
> **captainstan said:**
> whenever i click a box to let a program be executable it gets unclicked right away....i am not able to make any program executable

Is the file you are trying to mark executable located on a windows flesystem (FAT or NTFS) or on some optical media?

Windows filesystems lack support for file ownerships and permissions as they are used on Linux & Unix systems, and therefore the  permissions must be set for the whole filesystem at the time it's mounted.

And any optical media is read-only filesystem.

---

### Post by captainstan on 2011-02-07
I am trying to open up files on my second harddrive.  Whenever I try to open up any exe program it tells me i need permission and what not so I go to permissions in properties and when i click the check box it unchecks itself right after clicking it.   
Also I am trying to run sims 2 and I get this messege when trying to set permissions

Sorry, could not change the permissions of "AutoRun.exe": Error setting permissions: Read-only file system

---

### Post by vat with tux on 2011-02-07
i don't know the exact solution. But i was having the same problem & i moved that file to my ubuntu desktop & then i was allowed to mark it as executable. 
U may just try it out.:)

---

### Post by presence1960 on 2011-02-07
> **captainstan said:**
> 

Sorry, could not change the permissions of "AutoRunx.**_exe_**": Error setting permissions: Read-only file system

.exe is a windows extension and will not run in a linux file system

---

