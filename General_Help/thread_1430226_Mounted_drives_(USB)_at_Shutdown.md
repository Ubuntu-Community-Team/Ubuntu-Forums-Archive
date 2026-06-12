---
title: "Mounted drives (USB) at Shutdown"
date: 2010-03-15
forum: General Help
---

### Post by kazakore on 2010-03-15
OK got a couple of external USB hard drives and my mp3 player that are fairly often connected to my laptop. When updating the files on my mp3 player the other day I noticed something that seemed weird.

After deletion of files there is same amount on the disk. After ejecting and reinserting things are still the same. To have the files correctly updated I have to Unmount the drive, then I see it flushing the .Trashes folder and actually freeing space on the drive.

Now the same thing seems to happen at Shutdown of the PC, files are not being updated and are still being seen by the mp3 player/hard drive. Think new files are being seen but old one not removed but not 100% sure.

Is there anything I can do to force Ubuntu to correctly Unmount all drive at Shutdown so I don't have to do each one manually first? Or is there something else I am missing?

---

### Post by l4zy on 2010-03-15
It shows the same usage of diskspace since all the files which you have "deleted" are propably in .trash. 

Clear trash or use swich which deletes files without putting them into the trash.

---

### Post by kazakore on 2010-03-15
As I said in my first post it does seem to be as they are left in .trash and it doesn't know these files are no longer required and may be over-written.

I have been moving and deleting by using file browser (Nautilus/Thunar) and highlighting and pressing Delete button. Is Swich the same as Permanently Delete in Win, I.E. ****+Del shortcut?

Still would be nice to do it automatically on shutdown. Don't have this issue with other OSs. I assume Cut/Paste doesn't leave any remnants though?

---

