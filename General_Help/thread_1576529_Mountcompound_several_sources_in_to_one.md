---
title: "Mount/compound several sources in to one"
date: 2010-09-17
forum: General Help
---

### Post by Vetal_ca on 2010-09-17
Is there a way to mount/reference/link several folders or ISOs in to one?

Lets say, I have my photo album:


Backed_up_2000-2005.iso
Backed_up_2006-2009.iso

- files as is 
2010/Some_folder1/(group of files)
2010/Some_folder2/(group of files)
. . .

First two already organized and backed up to DVD/BD and kept as convenient single and unmutable .iso. I mount them with 'mount' command, loop service. 

Let's say, I mount Backed_up_2000-2005.iso to /Mounted_2000-2005 etc

When I aggregate it I'll get things like:

Mounted_2000-2005/2000/...
Mounted_2000-2005/2001/...
Mounted_2000-2005/2002/...
. . .

Mounted_2006-2009/2009/...
2010/...
____________________________

What I'd like to see is:

My photos:
/2000
/2001
...
/2010

I.e. flat and family friendly form with all details hidden.


I know, it is prone to conflicts so I do not expect mount will support it.

I want to see it in:

1) XBMC. This one after briefly reading through "Adding sources" I feel can do it (maybe for now)
2) As one Samba-shared folder so it is visible in home network


If I can do #2, number 1 becomes trivial

Thanks

---

