---
title: "usb recovery package"
date: 2011-03-24
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-24
Hi friends 

let me know is there any package available in ubuntu for recovering data from 

the usb drive

Thanks

---

### Post by Script Warlock on 2011-03-24
try testdisk or maybe try viewwing the hidden files in you usb sometimes it get stuck inside the .files or something.

---

### Post by Rakeshvijayan on 2011-03-24
> **Script Warlock said:**
> try testdisk or maybe try viewwing the hidden files in you usb sometimes it get stuck inside the .files or something.


Sorry friend 

I didn't mentioned the problem that I faced 

I had accidentally  formatted the pen drive that contain an important data 
I wanted it back is it possible to get back ?

---

### Post by t0p on 2011-03-24
Are these files you deleted and now want to get back?  If so, open the drive in question then click on **View > Show hidden files**.  A folder called .Trash-1000 (or something similar) will become visible.  Your missing files may be in there.

**EDIT:** Ah, I just saw your follow-up post where you mention that you formatted the drive.  I don't know how you can retrieve the files or if it's even possible.  All I can suggest is you search Synaptic (**System > Administration > Synaptic Package Manager**) for data retrieval packages.

---

### Post by Rakeshvijayan on 2011-03-24
> **t0p said:**
> Are these files you deleted and now want to get back?  If so, open the drive in question then click on **View > Show hidden files**.  A folder called .Trash-1000 (or something similar) will become visible.  Your missing files may be in there.


I mean is there any package available in ubuntu for recovering data from usb ?

---

### Post by fackamato on 2011-03-24
Try ddrescue, then create an image of the USB drive, then try recovering stuff from the image. (google ext3 format recovery or something)

---

### Post by s8472 on 2011-04-23
Sorry for the delayed reply, I've been busy.  But if you haven't found a suitable package and still looking for one, "[COLOR="Teal"]PhotoRec[/COLOR]" can do what you want.  Here is the first paragraph from its home page:

[INDENT]> PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from hard disks, CD-ROMs, and lost pictures (thus the Photo Recovery name) from digital camera memory. PhotoRec ignores the file system and goes after the underlying data, so it will still work even if your media's file system has been severely damaged or reformatted.[/INDENT]
[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

Hope this is not too late.

---

