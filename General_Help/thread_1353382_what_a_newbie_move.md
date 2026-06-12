---
title: "what a newbie move"
date: 2009-12-12
forum: General Help
---

### Post by Hackit on 2009-12-12
Ok i know you are going to laugh, when you are done laughing please read blelow.

I was using gpart to format an external drive for my router and after it failed I realized i had to unmount the drive.

i unmounted my external drive and restarted gpart, this is where i messed up, i forgot to change the drive to my exterenal and cleared my main drive.
once i releasized what i did i was unable to undo. so know gpart shows my main drive as empty.

So I have not rebooted my system as i suspect it will no longer boot once i do.

does anyone have any ideas of what might or will happen when i restart?
or if i can fix my newbie mistake.

Or it's time to luaugh again.

---

### Post by scouser73 on 2009-12-12
Been there, done that.  I suspect once you start the PC that it certainly won't boot into Ubuntu, or any O/S that was on there, I'm afraid you might need to do a full installation again.

---

### Post by serpantman on 2009-12-12
You can still run programs to recover data. But the file system / directory structure will be gone. You can still get back important files if you need them. Would be best to do this from a separate OS install since you might overwrite files you want if you reinstall on that disc.

---

### Post by Hackit on 2009-12-13
I was just thinking is there now way to rewrite the hard drive tables? I'm still logged in and everything is fine.

There must be a way to get the drive table info back?

I know i will have to reboot at some time and i have this rig set up so sweet and everything is perfect.

---

### Post by pbrane on 2009-12-13
If you haven't formatted the partition then yes, you can recover *IF* you put in the **exact same values** as the original partition table.

---

### Post by serpantman on 2009-12-13
> **Hackit said:**
> 
I know i will have to reboot at some time and i have this rig set up so sweet and everything is perfect.

Not rebooting is sounds like a valid strategy. 
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html)
Maybe. If you do get this, post back and tell us how. I would like to know.

---

