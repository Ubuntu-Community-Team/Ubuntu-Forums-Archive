---
title: "Unmounting USB stick"
date: 2006-06-28
forum: General Help
---

### Post by canadianwriterman on 2006-06-28
My Dapper has suddenly developed a small problem when working on my USB stick. Previously, everything worked perfectly.

Now, the drive is automatically detected and mounted as soon as I plug it in and an icon appears on the desktop, as usual. However, when I copy or delete anything from the drive, close the window and unplug the drive, everything is still the way it was before copying or deleting. 

I now have to manually "unmount" the drive by right-clicking on the desktop icon and selecting "eject" before any changes are written to the drive. Does anyone have any ideas about how I can restore the normal functionality? 

I know you may want to know what I may have installed recently that may have caused this, but I've been playing around with a lot of packages recently, so I couldn't pinpoint which one may have caused the problem.

Thanks for your help.

---

### Post by dmizer on 2006-06-28
i wouldn't consider this a problem.  you should be unmounting/ejecting your usb drive before disconnecting it anyway.

my usb drive has never allowed me to disconnect it without unmounting.  don't know why it worked for you before.

---

### Post by mlind on 2006-06-28
You should unmount removable drives always, or you may end up with a data corruption.

It could this package that has changed the behaviour [https://lists.ubuntu.com/archives/dapper-changes/2006-June/011871.html](https://lists.ubuntu.com/archives/dapper-changes/2006-June/011871.html)
There are some changelog entries about "eject" stuff.

---

### Post by canadianwriterman on 2006-06-28
Okay, bit of a pain compared with the flawless way it used to work. But, I take your point. Thanks.

---

