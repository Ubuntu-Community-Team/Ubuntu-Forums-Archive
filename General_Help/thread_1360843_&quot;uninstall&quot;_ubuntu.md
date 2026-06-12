---
title: "&quot;uninstall&quot; ubuntu?"
date: 2009-12-21
forum: General Help
---

### Post by zaffe93 on 2009-12-21
how do i get my windows vista back? i can't play so many games on Ubuntu which i thought it would .. :/


so please help me :P

---

### Post by muteXe on 2009-12-21
Stick in your vista disk and away you go.

---

### Post by ibuclaw on 2009-12-21
It's a simple 3 step procedure that is exactly the same as uninstalling Windows - Delete, Resize, Update Bootloader.


1) Delete the Ubuntu Partition(s) - done in the Ubuntu LiveCD.
2) Resize the Windows Partition to take up the entire disk (possibly done in Windows - idk, I know next to nothing about how it works).
3) Reinstall the Windows bootloader, typically done in the Windows Recovery CD/DVD - something like "fixmbr" (Again, idk the specifics).

---

### Post by muteXe on 2009-12-21
Oh he has a windows partition left?  Sorry, i read it as he didnt have a win partition at all anymore.

---

### Post by zaffe93 on 2009-12-21
hmm i have recovory cd of vista, will it work? 

also are you sure that u can uninstall ubuntu with the ubuntu CD?

---

### Post by ibuclaw on 2009-12-21
> **zaffe93 said:**
> hmm i have recovory cd of vista, will it work? 

also are you sure that u can uninstall ubuntu with the ubuntu CD?

Windows cannot read/detect any filesystem outside of its own internally used ones. So yes you will have to use the Ubuntu CD to remove Ubuntu.
**System->Administration->Partition Manager**
Will be the place you go, and then delete the Ubuntu filesystem from there.

For Microsoft's Fixmbr thingy: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
To resize the root filesystem for Windows, you should be able to do that in disk Management via "Extend Filesystem": [http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

