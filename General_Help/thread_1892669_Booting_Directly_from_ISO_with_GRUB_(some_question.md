---
title: "Booting Directly from ISO with GRUB (some questions)"
date: 2011-12-08
forum: General Help
---

### Post by Beanz239 on 2011-12-08
So I've done some heavy research and I'm close to being able to write a full tutorial on this, but I've hit sort of a roadblock. This is what I have so far:

For the average ISO, you should be able to mount it in the following manner using GRUB:

```
title Whatever You Want Here
find --set-root /directory/bootableimage.iso (navigation cannot contain spaces!)
map /directory/bootableimage.iso (hd32)
map --hook
chainloader (hd32)
```

A few notes: You can use things such as .gz or .bin files to mount as well. I'm not sure on the full compatibility list, though.

My question, though, is that certain images I've seen in the past use (0xff) instead of (hd32). I was wondering why. I have also seen that some of them require the command: ```
root (hd32)
``` after the 'map --hook' line. If anyone has any idea on why these are used and when to use them, it would be very helpful for when I go to put together a full tutorial.

I have only seen these pre-written. I've only been able to boot to 1 or 2 ISOs from my experiments and I want to include instructions for when to add these. Thanks for any help!

---

### Post by drs305 on 2011-12-08
Take a look at these two threads:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")
There is a section on installing from an ISO.

Can't answer the technical questions you pose, so hopefully you can include that!

---

