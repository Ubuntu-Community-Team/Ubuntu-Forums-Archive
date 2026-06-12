---
title: "USB mounts issue"
date: 2010-05-02
forum: General Help
---

### Post by julio_grr on 2010-05-02
Before telling me to search the forum and read all the threads about that, I must say I already did that.

None of the solutions really work, they are more like workarounds.

Issue :
When plugging in a usb device (such as a memory-stick), it's automatically mounted as /media/usbXX, but:
- it's read-only,
- only root can unmount.

Both problems have solutions such as changing /etc/usbmount/usbmount.conf (works fine for the read-only issue), or adding a line in /etc/fstab with the memory-stick partition uid (works fine for both issues but line has to be added for all possible memory-sticks around)

My problem is that it worked flawlessly in Karmic Koala *out of the box* and, most importantly *without having to add new lines to fstab*.

Now with Lucid Lynx I can't afford to add dozen of lines to fstab for all the memory cards that I may meet.

So what changed ? How can I solve the problem ?



(On a side note I must add that as long as textual configuration files will have to be edited by hand for such simple issues, Linux will NEVER be largely adopted.)

---

### Post by julio_grr on 2010-05-03
Ok so quite hard to get help on that.
I got to the web page of usbmount to get some documentation and read:
"The original author does not have enough time any more to actively maintain the USBmount package."
Perfect.

apt-get remove --purge usbmount 
apt-get install pmount


Problem solved.

-- 
Julio

---

