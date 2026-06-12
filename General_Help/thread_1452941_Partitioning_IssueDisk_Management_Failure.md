---
title: "Partitioning Issue/Disk Management Failure"
date: 2010-04-12
forum: General Help
---

### Post by Dan09 on 2010-04-12
Hey everyone! I have a quick question regarding the shrinking of my hard drive (that has Windows 7 already installed) in order to dual boot Ubuntu.

I have about 50GB of a 160GB HD free, and for some reason when I use the built-in Disk Management tool to attempt to shrink my HD, Windows tells me that there is only about 24GB of space available to be shrunk...? *see picture*

[CENTER][CENTER][CENTER] [IMG]http://i42.tinypic.com/1j9do2.png[/IMG] [/CENTER]
[/CENTER]
[/CENTER]

Does anyone know what in the world is going on? I have fragmented my HD TONS of times, as well as disabled the System Restore feature along with some other things. 

Any ideas guys? :confused::confused:

---

### Post by mikewhatever on 2010-04-12
It could be that Windows has its page file at the end of the partition, and it can't move them, since the files are in use. You could try deleting the page file and then resizing again.

---

### Post by Dan09 on 2010-04-12
> **mikewhatever said:**
> It could be that Windows has its page file at the end of the partition, and it can't move them, since the files are in use. You could try deleting the page file and then resizing again.

Typical of Windows to do something as intelligent as that, would the pagefile be the thing found in Control Panel - Advanced System Settings \ Advanced \ Performance \ Advanced \ Change \  No Paging File?

Thanks very much for the tip!

---

### Post by egalvan on 2010-04-12
Paging files
Restore Points files
System Restore files
Hibernatiion files
TrashCan files...

All of these can hide space from the user...

Yeah, it´s a Microsoft `thing` :P

But then Linux users sometimes get confused as to the trash-can also...

---

### Post by Dan09 on 2010-04-12
> **egalvan said:**
> Paging files
Restore Points files
System Restore files
Hibernatiion files
TrashCan files...

All of these can hide space from the user...

Yeah, it´s a Microsoft `thing` :P

But then Linux users sometimes get confused as to the trash-can also...

Ah well, I guess I was wrong to hand out the blame to MS alone XD.

I think I'm just going to shrink the 24G that I CAN work with and hope that is enough. Messing with vital system files like those listed above has too much potential to become a headache.

Anyways, thanks for the ideas guys! Wish me luck getting Ubuntu running! (finally)

---

### Post by egalvan on 2010-04-14
> **Dan09 said:**
> Ah well, I guess I was wrong to hand out the blame to MS alone XD.

No, Linux is much more stable on this than Microsoft...
so blame away.

> **Messing with vital system files like those listed above has too much potential to become a headache.**

Funny you should mention that....

On my Microsoft XP systems, the ONLY "vital system file" that is left is the paging file...
ALL the others have been eliminated.
And the functions that used them have been shut down or removed.
And my XP are happy :P

> Anyways, thanks for the ideas guys! Wish me luck getting Ubuntu running! (finally)

Ideas are meant to be shared, despited what the current crop of Copyright, DRM, Patent and "Intellectual" Property lawyers have convinced the gullible public and bodies politic to believe.

---

