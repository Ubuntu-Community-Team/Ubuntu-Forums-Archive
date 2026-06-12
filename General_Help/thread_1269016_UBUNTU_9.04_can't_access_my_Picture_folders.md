---
title: "UBUNTU 9.04 can't access my Picture folders"
date: 2009-09-17
forum: General Help
---

### Post by gkiteguy on 2009-09-17
I imported all my pictures and subfolders from another network computer. When I try and access the subfolder of Pictures, it opens the window, and I see the subfolders and then the window closes.  Is it a permission thing or a problem with how many levels or files UBUNTU can handle?

Gkiteguy

---

### Post by mcduck on 2009-09-17
There's no limit to directory structure depth, and it definitely isn't a permission problem either, if it was you couldn't open the directory at all instead of being able to open it and window closing immediately.

I'd say that the most likely reason is that one of your pictures wasn't copied correctly, and now when you try to open the directory Nautilus crashes when trying to create thumbnail for that corrupted file.

---

### Post by gkiteguy on 2009-09-17
Well, that makes sense. I will just delete the directory structure and re-import, hopefully without errors. 

Thanks for your help, I will let you know.

---

### Post by gkiteguy on 2009-09-18
> **mcduck said:**
> There's no limit to directory structure depth, and it definitely isn't a permission problem either, if it was you couldn't open the directory at all instead of being able to open it and window closing immediately.

I'd say that the most likely reason is that one of your pictures wasn't copied correctly, and now when you try to open the directory Nautilus crashes when trying to create thumbnail for that corrupted file.

> **gkiteguy said:**
> Well, that makes sense. I will just delete the directory structure and re-import, hopefully without errors. 

Thanks for your help, I will let you know.

Well, I recopied the entire directory on another drive, and the corrupted file or folder thing, makes sense as the other drive now does the same thing. It may be a folder. 

Is there a way to identify, which file is causing the problem so I could delete it without browsing the folder, which doesn't work?

Thanks for your help thus far. 

Gkiteguy

---

### Post by Don1500 on 2009-09-18
This sounds like a troubleshooting endevor.
[LIST=1]
[*]Can you open the original folder (This is probably "Yes",but since you are copying the folder I don't know.
[*]Copy 1/2 of the files to the new folder....does it work?
[*]If it works copy 1/2 of what is left to a separate folder. Does it work?
[*]Repeat until it doesnt work, then look through that folder.
[/LIST]

---

### Post by gkiteguy on 2009-09-18
> **Don1500 said:**
> This sounds like a troubleshooting endevor.
[LIST=1]
[*]Can you open the original folder (This is probably "Yes",but since you are copying the folder I don't know.
[*]Copy 1/2 of the files to the new folder....does it work?
[*]If it works copy 1/2 of what is left to a separate folder. Does it work?
[*]Repeat until it doesnt work, then look through that folder.
[/LIST]

That kind of works.  Some 15,000 pictures in some 100 folders. I knew that there was a downside of cheap digital cameras! I think I will import 1 folder at a time first. 

GKiteguy

---

### Post by gkiteguy on 2009-09-19
> **gkiteguy said:**
> That kind of works.  Some 15,000 pictures in some 100 folders. I knew that there was a downside of cheap digital cameras! I think I will import 1 folder at a time first. 

GKiteguy  Turns out to be some kind of a ".TMP" file.  Go figure! at least my pictures are all backed up. 

Thanks for your help

Gkiteguy

---

