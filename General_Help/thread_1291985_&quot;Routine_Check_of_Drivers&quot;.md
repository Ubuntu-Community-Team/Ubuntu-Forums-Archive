---
title: "&quot;Routine Check of Drivers&quot;"
date: 2009-10-15
forum: General Help
---

### Post by wbee on 2009-10-15
Hello,

This is not a problem but I'm curious.

Does the driver check occur every so many boot ups or when there might be a problem or randomly or combinations of the above?

In the last couple/three weeks,it has come up four times. I always let it run and it always continues and boots up.

Is it detecting something that is not quite right or should I not worry about it?

----------

Thanks.

---

### Post by Giblet5 on 2009-10-15
> **wbee said:**
> In the last couple/three weeks,it has come up four times. I always let it run and it always continues and boots up.


Uh.... A driver check during bootup?

Are you sure it isn't talking about a disk drive check? That happens at every boot, and will force a complete check every 30-40 bootups.

Disk checks will occur on disk devices with names like "/dev/sda2", etc.

Windows does that too but doesn't tell you about it.

If it takes a bit of time, every bootup, then you either have a USB disk that takes a looooong time to come 'ready', or you shut off the system by pulling the power cord out of the wall (or the system thinks you did), or you have the slowest disk drive ever.

---

### Post by oldos2er on 2009-10-15
You can configure fsck's behavior either with the tune2fs command, or a little utility called autofsck. See [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by wbee on 2009-10-15
Hello again,

Yep,it was routine check of "drives".

Thanks both.

---

### Post by ralley4 on 2009-10-30
You asked my exact question [wbee]("http://ubuntuforums.org/member.php?u=782197"). :D

Although, I had something else to add/ask...

> **Giblet5 said:**
> 
Windows does that too but doesn't tell you about it.


I also own several Macs, and I have never had this happen. Does OS X also do it without tell you?

I don't have a problem with this happening, except that sometimes it catches me off guard when I need to do something right quick. It would be nice if this happened in the background. Which may be an option because I have not looked into it any further, but just wanted to comment and say Thanks!

---

### Post by prostar on 2010-01-26
I'm sure you've learned by now, but you can just hit escape to skip the check.

---

