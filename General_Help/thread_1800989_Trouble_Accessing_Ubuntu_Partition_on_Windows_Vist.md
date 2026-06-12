---
title: "Trouble Accessing Ubuntu Partition on Windows Vista"
date: 2011-07-09
forum: General Help
---

### Post by kexus on 2011-07-09
So, I'm dual-booting Ubuntu 11.04 and Windows Vista.  I can't access my Ubuntu partition while on Windows.  I have tried using Ext2IFS as well as Ext2Fsd, but neither work.  On each one, when it gets to the point where you assign letters to the drives, the only thing there is my C: drive. The D: drive just contains some system files, I don't even know if I can write to it. So, am I doing something wrong? If so, what? 

Below is the Drive letter chooser thingy.  From the screenshots I saw online, it looks like there is supposed to be drop-down lists and stuff, but I don't get any of those.
[IMG]http://bayimg.com/najNCAADa[/IMG]
[IMG]http://i55.tinypic.com/1xxwrc.jpg[/IMG]
[IMG]http://bayimg.com/najNCAADa[/IMG]

---

### Post by wildmanne39 on 2011-07-09
Hi, did you install with wubi?

---

### Post by Chronon on 2011-07-09
My first guess would be that those tools don't support the ext4 file system.  Are you sure that they do?

---

### Post by kexus on 2011-07-12
> **Chronon said:**
> My first guess would be that those tools don't support the ext4 file system.  Are you sure that they do?
 
That would probably be it.  I think they both said they supported ext2 and ext3,  but they didn't mention ext4.  Do you know of anything that does?

---

