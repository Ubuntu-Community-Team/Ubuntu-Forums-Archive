---
title: "Is there a CL command to pipe the entire file system into a file?"
date: 2011-09-04
forum: General Help
---

### Post by TheGuvernor on 2011-09-04
What I mean is I want a complete directory and file tree of my system to be written to a file I can look at. I'm trying to understand the way Ubuntu has things laid out a little better.

---

### Post by haqking on 2011-09-04
> **TheGuvernor said:**
> What I mean is I want a complete directory and file tree of my system to be written to a file I can look at. I'm trying to understand the way Ubuntu has things laid out a little better.

you could use the tree command [http://linux.die.net/man/1/tree](http://linux.die.net/man/1/tree)

or 

**man tree **

from terminal

you could then cat it into a file or pipe it

if not installed then from terminal
[B]
sudo apt-get install tree[/B]

then again from terminal

**tree > filename.txt**

---

### Post by TheGuvernor on 2011-09-04
Muchas Gracias! Worked like a charm.

---

### Post by papibe on 2011-09-04
I would start reading the section 'Main directories' in [this]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") help document.

If you really want all the details, this would work, but it may take several minutes depending on how big and full your disk is:
```
$ sudo find / > FileSytemTree.txt
```
The find command will find files and directories. Without any option, as it's being run, will find and print everything. The list will be written on the file: FileSytemTree.txt

Hope it helps,
Regards.

---

### Post by haqking on 2011-09-04
> **TheGuvernor said:**
> Muchas Gracias! Worked like a charm.


no problem, glad i could help

---

### Post by haqking on 2011-09-04
> **papibe said:**
> I would start reading the section 'Main directories' in [this]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") help document.

If you really want all the details, this would work, but it may take several minutes depending on how big and full your disk is:
```
$ sudo find / > FileSytemTree.txt
```The find command will find files and directories. Without any option, as it's being run, will find and print everything. The list will be written on the file: FileSytemTree.txt

Hope it helps,
Regards.

yeah does same thing as tree.

But i prefer the look of the tree output.

both do the same thing though ;-)

---

