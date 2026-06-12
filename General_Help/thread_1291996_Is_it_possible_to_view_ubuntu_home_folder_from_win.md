---
title: "Is it possible to view ubuntu home folder from windows os?"
date: 2009-10-15
forum: General Help
---

### Post by mlinuxuser on 2009-10-15
Is it possible to view ubuntu home folder from windows os?

What should I do in ubuntu to do this?:confused:

---

### Post by karlson on 2009-10-15
> **mlinuxuser said:**
> Is it possible to view ubuntu home folder from windows os?

What should I do in ubuntu to do this?:confused:

From the same machine?  Or from a network server?

---

### Post by Giblet5 on 2009-10-15
There's a [driver for Windows]("http://www.fs-driver.org/").

It's not spectacularly useful, but it works.

---

### Post by mlinuxuser on 2009-10-15
> **karlson said:**
> From the same machine?  Or from a network server?

from the same machine

---

### Post by Giblet5 on 2009-10-15
> **mlinuxuser said:**
> from the same machine

That link I posted above will do that for you.

---

### Post by mlinuxuser on 2009-10-15
> **Giblet5 said:**
> That link I posted above will do that for you.

I am using ext 3 file system

---

### Post by Giblet5 on 2009-10-15
> **mlinuxuser said:**
> I am using ext 3 file system

"To find if a thing is possible, try it."
 - Napoleon "UnkNappy" Bonaparte

It'll read ext3.

---

### Post by mlinuxuser on 2009-10-15
Thanks for the link. I installed . It shows me a two drives for the swap and root with my assigned letters. But When I am opening the drive it asks "do u want to format it now" and not showing the contents

---

### Post by MelDJ on 2009-10-15
how about if ubuntu is installed through wubi?

---

### Post by mlinuxuser on 2009-10-15
> **mlinuxuser said:**
> Thanks for the link. I installed . It shows me a two drives for the swap and root with my assigned letters. But When I am opening the drive it asks "do u want to format it now" and not showing the contents
Whether I am installed correctly?

---

### Post by Giblet5 on 2009-10-15
> **mlinuxuser said:**
> Thanks for the link. I installed . It shows me a two drives for the swap and root with my assigned letters. But When I am opening the drive it asks "do u want to format it now" and not showing the contents

Are you running x64 windows or 32-bit? XP? Vista? Win7?

---

### Post by mlinuxuser on 2009-10-15
> **Giblet5 said:**
> Are you running x64 windows or 32-bit? XP? Vista? Win7?
Windows XP 32bit

---

### Post by Giblet5 on 2009-10-15
> **Giblet5 said:**
> Are you running x64 windows or 32-bit? XP? Vista? Win7?

Or, here's the [web that discusses how to mount Ext2 or Ext3]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html") filesystems under Windows. It has links and additional resources.

---

### Post by Giblet5 on 2009-10-15
I have it working on this box under XP-Pro-32, XP-Pro-64, and Vista-64. I have a Win7 partition but haven't tried this on there yet.

I used the [one off of Sourceforge]("http://sourceforge.net/projects/ext2fsd/") but had heard rumors that the Ext2 IFS was easier to use. I haven't actually used that one... I apologize for the extra trouble if you wind up having to remove that one and install the SF one...

---

### Post by mlinuxuser on 2009-10-15
> **Giblet5 said:**
> I have it working on this box under XP-Pro-32, XP-Pro-64, and Vista-64. I have a Win7 partition but haven't tried this on there yet.

I used the [one off of Sourceforge]("http://sourceforge.net/projects/ext2fsd/") but had heard rumors that the Ext2 IFS was easier to use. I haven't actually used that one... I apologize for the extra trouble if you wind up having to remove that one and install the SF one...
No Problem.I will try that ext2fs

---

