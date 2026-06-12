---
title: "fixing my USB drive"
date: 2006-05-14
forum: General Help
---

### Post by JacksonL on 2006-05-14
hey guys. I have a 2gb usb thumb drive that was working perfectly until one day when it just decided to refuse to be read. I've tried to fdisk but it can't open the drive (/dev/sdc). in nautilus it shows up, but I can't read it. I've even tried reading it in windows. again it shows up but windows says it has 0 bytes capacity and it can't read the disk. any idea how I could format/fix this little buddy?

---

### Post by garner_nc on 2006-05-14
I'm no expert on these things but you should be able to format it under Windows. It should be formatted Fat16 I believe.
   The recurring issue causing problems with these devices seems to be not un-mounting th edevice before removing it from the system. You need to unmount it before you just remove it. Just because you copy a file to it does NOT mean it gets written to the device instantly. The system waits until it has time to do the writing. When you un-mount it, all pending write operations move to the top of the system priority list.

All the Best,
Doug White

---

