---
title: "Create multiple ISO from one folder"
date: 2012-06-22
forum: General Help
---

### Post by schworak on 2012-06-22
I have a script that uses mkisofs to create a single DVD ISO.

This is working fine for now but the folder is growing fast and in a couple months the ISO will be larger than what a DVD will hold.

Is there some way to tell mkisofs to split the contents across multiple ISO files?

I may also have need for putting this same folder to CD which would take several files already. The files can't be compressed as they are already compressed and the images are for needed so I can burn them to physical media.

The process runs weekly in the background and I burn the disks each Monday morning. I need to keep that part of the process. 

I am more than happy to switch to another command line ISO creation tool if there is one and mkisofs can't do what I need.

Any help would be greatly appreciated.
[B]
[/B]

---

### Post by David Andersson on 2012-06-22
> **schworak said:**
> 
Is there some way to tell mkisofs to split the contents across multiple ISO files?


You can use the -m option: **exclude** files matching a glob pattern.

Example: Assuming you burn files in a directory named "films". It contains files and sub-directories begining with [a-zA-Z0-9]. Assuming half the size is occupied by files and subdirs beginning with [a-pA-P] and other half beginning with [q-zQ-Z0-9]. Run mkisofs (or genisoimage) twice. Once with option **-m "films/[q-zQ-Z0-9]*" films** and once with option **-m "films/[a-pA-P]*" films**

If output to an iso file, let each run output to different iso files.

Cons:
* Requires a manual analyze to determine a split point in the alphabet where either side is less than a dvd in size.
* When automated backup, the manually determined split point may not be valid if new large files have been added since.
* Increased complexity if and when there is need to split into 3 or more dvds.
* Increased complexity if files can begin with other letters than a-zA-Z0-9
* Bug prone: the directory name must be part of the -m option value. Just -m "[a-pA-P]*" will exclude files beginning a-p in sub-directories too. Not what we want.

Pros:
* Can work until you find a better answer.

---

### Post by David Andersson on 2012-06-22
> **David Andersson said:**
> 
* Can work until you find a better answer.

There is **dirsplit**, designed just for this kind of problem.

See last post of [http://forums.fedoraforum.org/archive/index.php/t-218353.html](http://forums.fedoraforum.org/archive/index.php/t-218353.html)

---

