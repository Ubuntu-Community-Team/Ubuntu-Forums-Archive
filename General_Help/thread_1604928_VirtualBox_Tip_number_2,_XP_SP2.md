---
title: "VirtualBox Tip number 2, XP SP2"
date: 2010-10-24
forum: General Help
---

### Post by coldraven on 2010-10-24
Ok, you have created your Windows XP virtual machine using your Service Pack 2 restore disk.
Now you want to upgrade it to SP3.

In my case the SP3 file (316.4 MB) was on my 1TB external USB drive (F) so I copied it 
across to C:\Windows\Temp. Fairly slow!
I forgot to say this was after Windows tried to index the drive. That is slow!
But when run it extracted all the files to....guess where, drive F:.  This is very slow!
Then it backed up all the old files to F: as well. More slowness again!

So what have we learnt? 
Windows is cranky!
Don't bother copying across SP3 to your VM, run it from wherever it is.
Make a SP3 slipstreamed version of your Restore Disk!! This will save you a long long wait.

---

