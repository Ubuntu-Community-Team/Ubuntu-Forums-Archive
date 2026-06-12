---
title: "Can't access drive with Ubuntu Studio"
date: 2010-06-24
forum: General Help
---

### Post by BobLand on 2010-06-24
I have Ubuntu Studio installed on a separate drive.  I recently built a new system and installed Windows 7 with Ubuntu Lucid (not Studio) onto a new and faster drive.  I need to access the data on the Ubuntu Studio drive but all I get is the grub and lost+found directories along with a number of preempt files.

The drive was originally setup with LVM.

I mainly want to get the contents of my home directory copied to some other drive but can't reach it.

Any ideas of suggestions?

Thanks,
bobland

---

### Post by VH-BIL on 2010-06-24
Can you boot into Ubuntu Studio and back up your files?

---

### Post by BobLand on 2010-06-24
Can't boot into the drive.  I assumed that I could.  I didn't touch the drive in any way.  Figured I'd just connect it up and it would boot.  No such joy.

---

### Post by VH-BIL on 2010-06-25
Did you connect it in the same configuration as when you had it working before?

---

### Post by BobLand on 2010-06-25
> Did you connect it in the same configuration as when you had it working before?

Not sure what you mean.  I set the bios to boot this drive first.  It didn't.

---

### Post by VH-BIL on 2010-06-25
I mean if that was the only drive connected to the computer before is it now? I know you should be able to have more then one drive connected but just for diagnostic purposes.

---

### Post by BobLand on 2010-06-25
Using the rescue disc, I found the data is intact.  How do I actually fix the system so it boots on its own?  The rescue program dumps me into a root prompt but I don't know what to do to fix the system.

Thanks,
bobland

---

### Post by VH-BIL on 2010-06-25
if you have access to the new drive you can probably use copy commands to copy the data.

---

### Post by BobLand on 2010-06-25
After spending way too much time with this I ended up just reinstalling everything.  In the end, I was able to get back the original drive and all the data.  I'll probably reformat the drive and use it as a giant private directory.

---

