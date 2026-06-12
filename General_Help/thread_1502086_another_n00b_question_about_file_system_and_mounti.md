---
title: "another n00b question about file system and mounting"
date: 2010-06-05
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-05
Hi again everyone.  I have another n00b question concerning my "file system". Ive searched the boards and found nothing to what I was specifically looking for.  Ive noticed a few screenshots have their "file systems" directly on the desktops.  When I try to do that, by dragging and dropping, it doesnt happen.  I get the error message saying:  

Error while copying "File System".

There was an error copying the file into /home/mark/Desktop

Can't open mountable file.



So my question is, how do I unmount it so that I can place it on the desktop? Also, how about renaming the "file system" as well? I tried using GPARTED to re-label the partition, but that didnt work. 

Any help would be greatly appreciated!  

Mark

---

### Post by TeoBigusGeekus on 2010-06-05
When you performed a drag 'n' drop, ubuntu attempted to copy the whole filesystem to your desktop! This cannot be done...
What you can do is this:
open configuration editor - type
```
gconf-editor
```
in terminal.
Go to Apps->Nautilus->Desktop and check Computer Icon Visible.
You now have a computer icon on your desktop.
You can right click it and rename it to file system if you want.

---

### Post by VinoFuriaRoja on 2010-06-05
Thanks for the tip!  I just realized too that I could have used Ubuntu Tweak as well, but its better that I learned the command line way.  Thanks!   

Question answered, problem solved.

---

