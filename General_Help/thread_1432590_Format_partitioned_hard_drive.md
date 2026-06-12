---
title: "Format partitioned hard drive"
date: 2010-03-17
forum: General Help
---

### Post by edfoxx36 on 2010-03-17
Hi, My old laptop had a severe technical problem and I was forced to buy a new one, but I removed the hard disk (SATA) and but it into a shell casing so it essentially now just an external hard drive. The problem that I am having is that I used to dual boot, with most of the hard disk formates as EXT3 for ubuntu, and the rest NTSF for windows. I am trying now to format the entire hard disk as NTSF, but I cant figure out how to do this from windows, because windows cant even detect the ext3 partition.
Can anyone offer any suggestions?

---

### Post by ndefontenay on 2010-03-17
Hi.

Here you go.

Go to Computer Management (There's a variety of ways to get there. If you can't find it, you should see it in Administrator tools from your control panel, or open windows explorer, right click "Computer" or "My computer" depending of the version and choose "manage").

In Computer management, select Storage>Disk Management.

You will see Disk 0 (your internal drive) with the different partition on it.

And logically you will see your external hard drive. Right click and select "remove partition" then right click again and choose create partition.

It's pretty straight forward from there.

Nico

---

### Post by edfoxx36 on 2010-03-17
Ok thanks so much! 
one last thing...im in the disk management window, but when you say to right click and select "remove partition", I dont see that, all that is an active options is "delete volume".
Will that work?

---

### Post by Mark Phelps on 2010-03-18
> **edfoxx36 said:**
> Ok thanks so much! 
one last thing...im in the disk management window, but when you say to right click and select "remove partition", I dont see that, all that is an active options is "delete volume".
Will that work?

Yes ...

---

