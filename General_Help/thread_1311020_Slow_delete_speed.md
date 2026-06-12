---
title: "Slow delete speed"
date: 2009-11-02
forum: General Help
---

### Post by Pasdar on 2009-11-02
I'm running Kubuntu 9.10 now and everytime I select to delete a file (via dolphin, not terminal), it takes quite some time before the deleting is done. I see the notice that the file is being moved to the trash and after like 15 secs its completely moved. Obviously this is annoying.

Is there a fix for this?

---

### Post by Giblet5 on 2009-11-02
Yes. Hard delete the file instead.

Select the file(s) and hold down the shift key while pressing Del.

Same as Windows.

Note: If you have less than 10% free disk space, performance of deleting or creating files will go through the toilet before it gets to you. This is true of all Unix filesystems other than those emulated directly in RAM.

This is because the default filesystem structure was designed for "typical" use (best performance under varying file allocation strategies). One can tune an ext filesystem for spectacular performance for ONE SPECIFIC TASK eg, storing/organizing .iso CD/DVD images, but other tasks will suffer as a result.

---

### Post by Pasdar on 2009-11-05
Thank you, that works great. Is there a way though to make it 'move' the files in an instant to the trash?

---

