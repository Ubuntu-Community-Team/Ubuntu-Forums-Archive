---
title: "davfs: How to see file copy (cp) status?"
date: 2011-11-15
forum: General Help
---

### Post by charding on 2011-11-15
If I set up my box.net drive using mount.davfs, is there a way to see the file copy status of a file or multiple files using cp?

When I run the cp comment to copy a file (~10MB) to my box.net webdav drive, it copies it and seems like it completed the command within less than a second and returns the the comment line. But I'm pretty sure a 10MB file will take longer.

If there was a davfs tool to tell me this it would be helpful or another way.. Any suggestions?

---

### Post by jjex22 on 2011-11-15
add verbose mode? 

cp -v

tbh these days 10mb will travel across anything other than usb 1/2 VERY fast - it often surprises me, I use Esata for my externals and they transfer 40GB in under 10 mins!

---

### Post by charding on 2011-11-15
> **jjex22 said:**
> add verbose mode? 

cp -v

tbh these days 10mb will travel across anything other than usb 1/2 VERY fast - it often surprises me, I use Esata for my externals and they transfer 40GB in under 10 mins!

This just shows the file start and end locations but gives me nothing on file copy status (like a progress bar like scp gives for file transfer). Any other ideas?

---

### Post by Cyclane on 2011-11-15
I believe scp is the only program that does this. Can't you just scp the file over, to test this?

###EDIT
Ahh never mind you would have to set up a SSH server first.

---

